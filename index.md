---
permalink: index.html
site: sandpaper::sandpaper_site
---

This lesson is a hands-on introduction to visualizing genomic data with the
[Integrative Genomics Viewer (IGV)][igv-home], a free desktop application for
exploring genomic datasets. It is designed for people who are new to genome
browsers but who already have some familiarity with common genomics file
formats and concepts (chromosomes, genes, reads, variants).

Across a series of hands-on exercises, learners load a reference genome, load
their own genome from a FASTA file, explore aligned sequencing reads (BAM) and
candidate SNPs, precompute coverage data with `igvtools`, explore RNA-seq
splice junctions with Sashimi plots, and explore population variant data from
a VCF file.

::::::::::::::::::::::::::::::::::::::::::  prereq

## Prerequisites

1. Learners should be comfortable with basic genomics terminology: chromosome,
  gene, exon/intron, sequencing read, and variant.

2. Learners must install IGV (desktop) before the workshop starts. See the
  [setup instructions](learners/setup.md) for download links and instructions.

3. Learners must download and unzip the workshop data before class starts.
  See the [setup instructions](learners/setup.md) for the download link.

::::::::::::::::::::::::::::::::::::::::::::::::::

This lesson's exercises, slides, and sample datasets are adapted from the
IGV team's [BroadE workshop materials][broade-2017] (Broad Institute, April
2017) by Jim Robinson and Helga Thorvaldsdóttir. If you use IGV itself in
published work, see [igv.org][igv-home] for the current recommended
citations.

[igv-home]: https://igv.org
[broade-2017]: https://www.igv.org/workshops/BroadApril2017/
