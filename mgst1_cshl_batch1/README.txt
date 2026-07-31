Mgst1 — ENCODE CSHL batch 1 track hub (raw ENCODE files)

WHAT THIS IS
  34 tracks = 17 mouse tissues x 2 biological replicates.
  Every bigDataUrl points at the ORIGINAL ENCODE bigWig on the ENCODE public S3
  bucket. This hub contains NO generated, rescaled, merged or averaged data files.

  Single batch: 76 bp reads, submitted 2012-02-29 / 2012-06-29, mm10 + GENCODE M21,
  pipeline bulk-rna-seq-star-signal-generation-step-v-1-0, Gingeras lab (CSHL),
  C57BL/6, adult 2 months. The 101 bp batch is excluded, so exon-ratio
  comparisons across all 17 tissues here are valid.

NOTE ON "RAW"
  ENCODE's signal bigWigs are already RPM-normalised by ENCODE's own pipeline
  (STAR --outWigNorm RPM): values are non-integer and the genome-wide signal sum
  is near-constant across libraries. ENCODE does not publish un-normalised
  bigWigs. Nothing further was applied here.

TO LOAD
  1. Put this directory on an HTTP(S) server (only 4 small text files; total < 30 KB).
  2. UCSC Genome Browser -> My Data -> Track Hubs -> My Hubs.
  3. Paste the URL of hub.txt and click "Add Hub".

  Because the signal streams from ENCODE, your server only hosts the text files.

LEFT-HAND CONTROL
  Click the track group "Mgst1 by tissue" to open the configuration page:
    - Organ system checkbox row (digestive / renal / cardiovascular / immune /
      adipose / endocrine / reproductive / respiratory)
    - Replicate checkbox row (rep1 / rep2)
    - Per-tissue checkboxes below the matrix
    - full / dense / hide dropdown per track

Validated with UCSC hubCheck: 0 problems.
