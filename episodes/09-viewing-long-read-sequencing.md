---
title: Viewing Long-Read Sequencing Data
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explain how long-read sequencing (PacBio, Oxford Nanopore) differs from
  short-read sequencing in IGV.
- Use IGV's alignment preferences to filter raw long-read errors and reveal
  consensus signal.
- Interpret mapping quality (MAPQ) when assessing a long-read alignment.
- Recognize split reads as evidence for structural variants in long-read
  data.
- Use haplotype-tag coloring to visualize phased variants.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How does IGV handle long reads differently from short Illumina reads?
- How do I tell real signal from raw sequencing error in noisy long reads?
- How can long reads and read phasing help interpret structural variants and
  repeat expansions?

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## This episode is optional

This is a supplementary episode — cover it only if time allows. It does not
use the workshop's `igvData` files; instead it walks through published
examples to introduce concepts you can apply to your own long-read data
later.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Background: what makes long reads different

Illumina ("short-read") sequencing produces reads a few hundred base pairs
long with a very low per-base error rate. Third-generation platforms —
PacBio and Oxford Nanopore — instead produce **long reads**, roughly 10,000
to 100,000 base pairs, at the cost of a much **higher raw error rate in each
individual read**. With enough coverage, those per-read errors average out
into a highly accurate *consensus*, but any single long read, viewed on its
own in IGV, looks considerably noisier than a short Illumina read.

## Filtering raw errors to see the consensus signal

Because of this, IGV includes alignment display options specifically aimed
at long reads: filtering out raw single-read errors so the underlying
consensus signal is easier to see, and extended support for split
alignments (linking a read's split parts together, using the `SA` BAM tag).

Compare the same 10 kb region of chromosome 10, sequenced with both PacBio
and Illumina:

![The same locus sequenced with PacBio (long reads, top) and Illumina (short reads, bottom). The PacBio track is dense with small colored mismatch/indel marks — raw single-read errors — that the Illumina track does not show.](fig/longread-01-pacbio-illumina-comparison.png){alt='PacBio and Illumina alignments at the same locus, PacBio showing many more small mismatches/indels'}

Most of that PacBio noise is small indels — a single insertion or deletion
of a few bases in an individual read, not a real biological difference from
the reference. Hiding indels below a chosen size (and enabling **quick
consensus mode**, which suppresses a mismatch unless it is shared by enough
reads to look real) filters this out:

![The same PacBio track with small indels hidden: the reads now look much closer to the clean Illumina track above it.](fig/longread-02-filtered-small-indels.png){alt='PacBio alignments with small indels filtered out, closely resembling the Illumina track'}

The same idea applies to single-base mismatches. With quick consensus mode
enabled, only mismatches that recur consistently across reads (a real
variant) are still shown; one-off raw sequencing errors are suppressed:

![Quick consensus mode applied to single-nucleotide mismatches: only consistent, likely-real mismatches remain visible.](fig/longread-03-quick-consensus-mode.png){alt='PacBio alignments after enabling quick consensus mode, showing only consistent mismatches'}

These options live under **View > Preferences… > Alignments**:

![The Alignments tab of IGV's Preferences dialog: indel labeling/hiding thresholds and Quick consensus mode.](fig/longread-04-preferences-alignments-tab.png){alt='IGV Preferences dialog, Alignments tab, with indel and quick-consensus-mode options highlighted'}

:::::::::::::::::::::::::::::::::::::::  challenge

## Why filter at all?

If quick consensus mode and indel-hiding can suppress real, rare variants
along with sequencing noise, why would you ever want to turn them on?

:::::::::::::::  solution

## Solution

They trade a small risk of hiding a genuine low-frequency variant for a
much larger gain in readability: without filtering, a long-read track can
be so dense with single-read noise that a real, well-supported signal is
hard to distinguish by eye. Filtering is a first-pass visual aid — for any
locus you are seriously evaluating, you would still want to check the
unfiltered view and the read-level evidence before ruling a variant real or
an artifact.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Real examples: reviewing nanopore BAM files

The examples below are adapted from Oxford Nanopore's EPI2ME team's guide,
["A guide to reviewing BAM files"][epi2me-bam] — reproduced here with
attribution; the screenshots in this section remain © Oxford Nanopore
Technologies and are not covered by this lesson's CC-BY license.

Before loading any BAM file, two things matter regardless of sequencing
platform: it must be aligned against the **same reference genome** you have
selected in IGV (mismatched coordinates can misdisplay data or crash IGV),
and it should be **sorted and indexed** first.

### Mapping quality (MAPQ)

Every aligned read carries a MAPQ score (0–255) reflecting how confident the
aligner is that the read belongs at that exact genomic location — higher is
more confident. Clicking a read in IGV shows its MAPQ directly:

![A single long read's details: read length ~17.9 kb, MAPQ 11, and a CIGAR string full of insertion/deletion operations — typical of nanopore's higher per-base error rate.](fig/longread-06-simple-alignment-detail.png){alt='IGV read-details popup showing read length, MAPQ score, and CIGAR string for a nanopore read'}

Clicking the coverage track instead shows the allele counts at that
position — here, a heterozygous site with 11 reads (61%) supporting the
reference base and 7 reads (39%) supporting an alternate base:

![The variant sites and coverage track for the same locus: two heterozygous SNVs (red-highlighted), each recorded in the accompanying VCF.](fig/longread-05-simple-alignment.png){alt='IGV coverage and alignment view showing two heterozygous SNVs with a VCF track above'}

A MAPQ in the low single digits (as opposed to 60, a common "fully
confident" ceiling) is a warning sign: reads that cannot be confidently
placed at a unique location make any variant called from them less
trustworthy — the same caution you applied to BLAT results in
[Viewing Alignments and SNPs](04-viewing-alignments-and-snps.md).

### Split reads as evidence for structural variants

A single long read spanning a structural variant breakpoint does not need a
*second* read to reveal it (unlike the paired-end evidence used in
[Viewing Structural Variants](08-viewing-structural-variants.md)) — the read
itself can be **split**: part of it aligns on one side of the breakpoint,
part on the other. Sorting reads by length and looking for this pattern
makes large events easy to spot. Here, a 6 kb deletion in a reference sample
(called by the structural variant caller Sniffles2) is directly visible as
reads that align partially, then resume on the far side of the deleted
region — with a ClinVar annotation track confirming the deletion is a known
clinically-relevant variant:

![A 6 kb deletion, directly visible as reads whose alignment is interrupted then resumes past the deleted region; a ClinVar track (blue bars) shows this variant is already clinically annotated.](fig/longread-07-structural-variant-deletion.png){alt='IGV view of a large deletion visible via split long reads, with a ClinVar VCF annotation track'}

### Haplotype phasing

Long reads are also long enough to span multiple nearby variants on the
*same* physical DNA molecule, which lets phasing tools (such as WhatsHap or
LongPhase) tag each read with which parental haplotype it belongs to (the
`HP` BAM tag). Coloring and sorting reads by `HP` groups them into their two
haplotypes, making it easy to compare alleles side by side. In this example
— a short tandem repeat expansion in the *FMR1* gene — one haplotype carries
a much larger insertion than the other; grey reads could not be confidently
assigned to either haplotype:

![Reads colored and grouped by haplotype (HP) tag: one haplotype (top) carries a small insertion, the other (bottom) a much larger one, at a repeat expansion in FMR1.](fig/longread-08-haplotype-phasing.png){alt='IGV view of reads grouped by haplotype tag showing different insertion sizes between the two alleles at an FMR1 repeat expansion'}

:::::::::::::::::::::::::::::::::::::::  challenge

## Why does phasing matter here?

Both alleles in the example above contain an insertion, just of different
sizes. Why is knowing *which reads belong to which haplotype* useful,
rather than just looking at the insertion sizes across all reads together?

:::::::::::::::  solution

## Solution

Without phasing, you would see a mix of insertion sizes at the locus and
have to guess whether that reflects two distinct alleles (e.g. one normal,
one expanded) or a more continuous, noisy distribution. Grouping reads by
haplotype turns that ambiguous mixture into two clean, separately
interpretable groups — letting you say, for example, "this individual has
one allele of roughly this repeat length and a second allele of roughly
that length," which is exactly the kind of call needed to assess conditions
like Fragile X syndrome (associated with *FMR1* repeat expansions).

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

[epi2me-bam]: https://epi2me.nanoporetech.com/reviewing-bam/

:::::::::::::::::::::::::::::::::::::::: keypoints

- Long reads (PacBio, Oxford Nanopore) trade a higher per-read error rate
  for much greater length than short Illumina reads.
- IGV's **quick consensus mode** and indel-hiding thresholds (**View >
  Preferences > Alignments**) filter raw long-read noise so consensus
  signal is easier to see.
- A read's MAPQ score (0–255) reflects alignment confidence; low MAPQ is a
  warning sign for any variant called from that read.
- A single long read can directly reveal a structural variant by splitting
  across its breakpoint, without needing paired-end evidence.
- Coloring and grouping reads by haplotype (`HP`) tag separates two alleles
  for direct comparison, useful for phased variants and repeat expansions.

::::::::::::::::::::::::::::::::::::::::::::::::::
