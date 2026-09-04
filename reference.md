---
title: 'Reference'
---

## Reference

## [Introduction to IGV](../episodes/01-introduction.md)

- IGV is a free desktop genome browser that runs locally and supports many
  file formats (FASTA, BED, BAM, TDF, VCF, and more).

## [IGV Basics](../episodes/02-igv-basics.md)

- **File > Load from Server…** loads example data hosted by the IGV team.
- Zoom levels: whole genome (**All**) → chromosome → region → base pair.
- Click-and-drag on the ruler to zoom into a region; double-click a track to
  zoom to a point (<kbd>Alt</kbd>-click to zoom out).
- Type a locus or gene name into the search box and click **Go** to jump
  directly to it.
- Right-click a gene track for **Collapsed** / **Expanded** / **Squished**
  display modes.
- **Genomes > More…** adds other IGV-hosted genomes to the drop-down menu.
- **Tools > Combine Data Tracks** adds, subtracts, multiplies, or divides two
  numeric tracks into a new derived track.

## [Loading Your Own Genome](../episodes/03-loading-your-own-genome.md)

- **Genomes > Load Genome from File…** loads a reference sequence (FASTA).
- **File > Load from File…** loads any other local track (e.g. a BED
  annotation file).
- A genome loaded from a bare FASTA has no gene names or cytoband ideogram
  until you add annotation tracks yourself.

## [Viewing Alignments and SNPs](../episodes/04-viewing-alignments-and-snps.md)

- IGV finds a BAM's `.bai` index automatically if it is named correctly and
  kept alongside the BAM file — never load the `.bai` directly.
- Right-click aligned reads for **Sort alignments by** (e.g. base, read
  strand) and **Color alignments by** (e.g. read strand) options.
- Warning signs of a false-positive variant: low base quality (shaded
  mismatches), a mismatch confined to one strand in a non-strand-specific
  library, and (via BLAT) many equally-good alternative alignments elsewhere.
- **Tools > BLAT…**, or right-click a read and choose **BLAT read
  sequence**, checks whether a read/feature aligns uniquely.

## [Precomputing Coverage with igvtools](../episodes/05-precomputing-coverage.md)

- **Tools > Run igvtools… > Count** precomputes a `.tdf` coverage summary for
  a BAM file.
- Right-click a coverage track and select **Load pre-computed coverage
  data…** to attach a `.tdf` file.

## [Viewing RNA-seq Data](../episodes/06-viewing-rnaseq.md)

- **View > Preferences > Alignments > Splice Junction Track** enables
  junction arcs for RNA-seq BAM tracks.
- Right-click a junction/alignment track and select **Sashimi Plot** for a
  combined coverage + junction view; **Set Junction Coverage Min** filters
  out low-count junctions.

## [Viewing Variants and Genotypes](../episodes/07-viewing-variants.md)

- A VCF track has a variant sites panel and a per-sample genotypes panel.
- Variant sites: blue = reference allele, red = alternate allele. Genotypes:
  grey = homozygous reference, blue = heterozygous, cyan = homozygous
  alternate.
- Sample metadata comes from an auxiliary tab-delimited file (header row of
  attribute names, first column of sample names matching the VCF).
- Search using `gene:protein-change` (e.g. `APOL1:S342G`) as well as by
  coordinate or gene name.
- Right-click genotypes for **Group By…** (a sample attribute, e.g.
  population), **Display Mode**, **Color By**, and sort options.

## [Viewing Structural Variants](../episodes/08-viewing-structural-variants.md)

- A larger-than-expected inferred insert size (colored red) indicates a
  deletion; a coverage drop appears between the two breakpoints.
- Reads colored by an unexpected mate chromosome indicate an
  inter-chromosomal fusion.
- Same-strand (forward-forward or reverse-reverse) discordant pairs indicate
  an inversion; right-click alignments and select **View as pairs** to see
  pair relationships clearly.

## [Viewing Long-Read Sequencing Data](../episodes/09-viewing-long-read-sequencing.md)

- **View > Preferences > Alignments**: indel hiding thresholds and **Quick
  consensus mode** filter raw long-read errors so consensus signal is
  easier to see.
- MAPQ (0–255) reflects alignment confidence; low MAPQ is a warning sign for
  any variant called from that read.
- A single long read can reveal a structural variant directly by splitting
  across its breakpoint.
- **File > Load from URL…** streams a remote BAM/CRAM without downloading
  it first; right-click **Link supplementary alignments** plus **Color
  alignments by > Read strand** (pink = forward, purple = reverse) reveals
  an inversion within single linked reads.
- Color/group reads by `HP` (haplotype) tag (**Color/Group alignments by >
  Tag**, tag name `HP`) to separate two phased alleles for comparison, or to
  tell a heterozygous structural variant (one haplotype) from a homozygous
  one (both).

## Glossary

BAM
:    Binary Alignment/Map format; stores aligned sequencing reads. Requires a
     `.bai` index file for random access.

BED
:    A simple tab-delimited format for genomic intervals/features.

BLAT
:    An alignment search tool used in IGV to check whether a read or feature
     sequence aligns uniquely, or almost as well to other locations.

CIGAR string
:    A compact code in a SAM/BAM record describing how a read's bases align
     against the reference (matches, insertions, deletions).

Coverage
:    The number of aligned reads overlapping each position in the genome.

Cytoband
:    A stained-banding pattern used to represent chromosome structure at low
     zoom levels.

FASTA
:    A plain-text format for nucleotide or protein sequences.

Genotype
:    The specific allele(s) an individual sample carries at a variant site.

Haplotype tag (HP)
:    A BAM tag assigned by a phasing tool (e.g. WhatsHap, LongPhase) that
     labels which parental haplotype a read belongs to.

Insert size
:    The distance spanned by a paired-end fragment, from the outer edge of
     one read to the outer edge of its mate.

Inversion
:    A structural variant in which a segment of the genome is reversed in
     orientation between two breakpoints.

Mapping quality
:    A score reflecting how confident an aligner is that a read is placed at
     the correct genomic location.

Reference genome
:    The assembled genome sequence that reads, genes, and variants are
     positioned against.

Sashimi plot
:    An IGV visualization combining exon coverage and splice-junction reads
     for RNA-seq data.

Split read
:    A single sequencing read whose parts align to two different locations
     (or orientations) in the reference, often evidence of a structural
     variant breakpoint.

Splice junction
:    The point where two exons are joined together after intron removal;
     represented in IGV as an arc connecting the two exons.

TDF
:    A binary, indexed summary format used by IGV to store precomputed
     coverage/summary data at multiple resolutions.

Track
:    A single row (or set of rows) of data displayed in IGV, such as a gene
     annotation track, an alignment track, or a variant track.

VCF
:    Variant Call Format; stores variant calls and, optionally, per-sample
     genotypes.
