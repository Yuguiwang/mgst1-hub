# Mgst1 RNA-seq track hub — ENCODE CSHL batch 1

UCSC Genome Browser track hub for **Mgst1** (microsomal glutathione S-transferase 1)
across 17 adult mouse tissues, mm10.

All tracks stream the **original, unmodified ENCODE bigWig files** from the ENCODE
public S3 bucket. This folder contains no signal data — only hub configuration text
(~250 KB total).

## Hub URL

Single-file hub (recommended):

```
https://raw.githubusercontent.com/Yuguiwang/mgst1-hub/main/mgst1_cshl_batch1_onefile.txt
```

Directory-hub variant (adds per-track description pages):

```
https://raw.githubusercontent.com/Yuguiwang/mgst1-hub/main/mgst1_cshl_batch1/hub.txt
```

Load it via **My Data → Track Hubs → My Hubs → Add Hub**, or open directly:

```
https://genome.ucsc.edu/cgi-bin/hgTracks?db=mm10&hubUrl=https://raw.githubusercontent.com/Yuguiwang/mgst1-hub/main/mgst1_cshl_batch1_onefile.txt&position=chr6:138139500-138157800
```

Check the URL resolves after pushing:

```bash
curl -sI https://raw.githubusercontent.com/Yuguiwang/mgst1-hub/main/mgst1_cshl_batch1_onefile.txt | head -3      # expect HTTP/2 200
```

## Two variants

| File | Notes |
|---|---|
| `mgst1_cshl_batch1_onefile.txt` | Single file, 17 KB, `useOneFile on`. No relative paths — fully portable. Recommended. |
| `mgst1_cshl_batch1/hub.txt` | Directory hub. Click a track name to see a description page with the full 17-tissue file list. Keep the `mgst1_cshl_batch1/` folder intact — it uses paths relative to itself. |

Both expose identical tracks and pass UCSC `hubCheck`.

## Contents

34 tracks = **17 tissues x 2 biological replicates**, shown separately (not averaged).

Single sequencing batch — this is what makes cross-tissue exon comparison valid:

| Property | Value |
|---|---|
| Lab | Thomas Gingeras, CSHL (ENCODE) |
| Assay | polyA+ RNA-seq, rRNA-depleted, spike-ins |
| Read length | 76 bp (uniform) |
| Submitted | 2012-02-29 / 2012-06-29 |
| Assembly / annotation | mm10 / GENCODE M21 |
| Pipeline | `bulk-rna-seq-star-signal-generation-step-v-1-0` |
| Strain / age | C57BL/6, adult 2 months |
| Signal type | plus strand signal of unique reads |

Tissues: adrenal gland, colon, duodenum, gonadal fat pad, heart, kidney, large intestine,
liver, lung, mammary gland, ovary, small intestine, spleen, stomach, subcutaneous adipose
tissue, testis, thymus.

ENCODE's 101 bp batch (cerebellum, cortical plate, frontal cortex, placenta, urinary
bladder) is **deliberately excluded** — it differs significantly in 3' coverage bias
(median E4/mean(E2,E3) 0.34 vs 0.45, p = 3e-5) and apparent first-exon usage
(E1a fraction 0.18 vs 0.11, p = 2e-4). Placenta and urinary bladder, non-brain tissues in
that batch, show the same shift as the brain tissues, so the effect is technical rather
than biological.

## Note on normalisation

These ENCODE signal files are **already RPM-normalised by ENCODE's own pipeline**
(STAR `--outWigNorm RPM`): values are non-integer and the genome-wide signal sum is
near-constant across libraries (3.77e7-4.56e7, a 1.21-fold spread) despite differing
sequencing depth. ENCODE does not distribute un-normalised bigWigs. No further scaling
was applied here, so track heights are already depth-comparable across tissues.

## Mgst1 locus and exon bins (mm10)

Gene: `chr6:138,140,526-138,156,755`, **plus strand** (minus-strand signal over the locus
is ~0, verified).

| Exon | Coordinates | Note |
|---|---|---|
| E1a | 138,140,526-138,140,652 | alternative first exon (NM_019946, NM_001361308) |
| E1b | 138,141,586-138,141,882 | alternative first exon (NM_001347489, NM_001361309) |
| E2 | 138,147,658-138,147,815 | internal coding |
| E3 | 138,150,767-138,150,862 | internal coding |
| E3b | 138,153,495-138,153,603 | cassette exon (NM_001361307 only) |
| E4 | 138,156,131-138,156,755 | terminal exon + 3'UTR (all isoforms) |

## Controlling which tissues are shown

Click the track group **"Mgst1 by tissue"** to open its configuration page:

- **Organ system** checkbox row — digestive / renal / cardiovascular / immune / adipose /
  endocrine / reproductive / respiratory
- **Replicate** checkbox row — rep1 / rep2
- per-tissue checkboxes below the matrix
- `full` / `dense` / `hide` dropdown per track

`autoScale group` is on, so all visible tracks share one y-axis and heights are comparable.

## Provenance

`cshl_batch1_manifest.csv` lists, for all 34 files: ENCODE experiment and file accessions,
biosample accessions, strain, sex, age, submission date, and the direct ENCODE URL.

Validated with UCSC `hubCheck` (0 problems).
