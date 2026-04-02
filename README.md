Conversion of type 'PdfAnalysis' to type 'Record<string, unknown>' may be a mistake because neither type sufficiently overlaps with the other. If this was intentional, convert the expression to 'unknown' first.
  Index signature for type 'string' is missing in type 'PdfAnalysis'.ts(2352)


  SELECT bps.ID, bps.SumInsured, bps.SICategoryID_P20, bps.SITypeID, bps.Deleted
FROM Claims c WITH (NOLOCK)
JOIN MemberSI ms WITH (NOLOCK) ON ms.MemberPolicyID = c.MemberPolicyID
JOIN BPSumInsured bps WITH (NOLOCK) ON bps.ID = ms.BPSIID
WHERE CAST(c.ID AS VARCHAR(50)) = 'YOUR_CLAIM_ID'
  AND ISNULL(ms.Deleted, 0) = 0
  AND ISNULL(bps.Deleted, 0) = 0
