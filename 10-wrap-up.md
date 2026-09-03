---
title: Wrap Up
teaching: 10
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Summarize the IGV skills covered in this lesson.
- Identify further IGV features and resources to explore independently.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What have I learned, and where can I go next with IGV?

::::::::::::::::::::::::::::::::::::::::::::::::::

## What we covered

Across this lesson you have:

- loaded reference genomes both from IGV's hosted server and from your own
  local FASTA file,
- navigated between whole-genome, chromosome, region, and base-pair
  resolution views,
- combined two numeric tracks with a simple arithmetic operation,
- inspected aligned sequencing reads and used sorting, coloring, and BLAT to
  distinguish a likely real SNP from a likely artifact,
- precomputed coverage data with `igvtools` so it remains visible at every
  zoom level,
- explored RNA-seq coverage, splice junctions, and Sashimi plots to identify
  alternative splicing between tissues, and
- explored population variant data from a VCF file, including grouping
  genotypes by sample attributes, and
- used paired-end insert size and pair orientation to confirm a structural
  variant (an inversion) by eye, and
- if you covered the optional episode, filtered raw long-read errors and
  used mapping quality, split reads, and haplotype tags to interpret PacBio
  and Nanopore data.

These are the same core skills — load data, navigate, and use track-specific
display options to interrogate a signal — that apply to almost any data type
IGV can display.

## Where to go next

- **Dedicated SV callers.** The previous episode showed you the raw evidence
  by eye at one locus; tools like Delly, Manta, and Lumpy automate the same
  search genome-wide and output a VCF you can load and view exactly as you
  did in [Viewing Variants and Genotypes](07-viewing-variants.md).
- **igv.js and IGV-Web.** If you want to embed genome browser views in a web
  page or share a specific view with collaborators without asking them to
  install anything, look at [igv.js](https://github.com/igvteam/igv.js) and
  [IGV-Web](https://igv.org/app/), which share much of the same track and
  navigation model as the desktop application you used here.
- **Batch scripting.** IGV supports batch scripts (**Tools > Run Batch
  Script…**) for automating repetitive tasks, such as generating snapshot
  images across many loci — useful if you find yourself repeating the same
  manual steps for many regions or samples.
- **The full IGV user guide.** <https://igv.org/doc/desktop/> documents every
  track type and display option, well beyond what a single workshop can
  cover.
- **Video tutorials.** The [IGV YouTube channel](https://www.youtube.com/@IGVtutorials)
  has short, focused videos on specific features (data navigation, sequencing
  data, VCF files, RNA-seq) if you would rather watch a feature demonstrated
  than read about it.

:::::::::::::::::::::::::::::::::::::::::  callout

## Feedback

If anything in this lesson was unclear, or you found a mistake, please let
your instructor know — lessons like this one improve with feedback from the
people who work through them.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- The core IGV workflow — load a genome and tracks, navigate to a region of
  interest, then use track-specific sort/color/display options — applies
  broadly across data types.
- IGV has many features beyond this lesson, including a web-embeddable
  sibling (igv.js) and batch scripting.

::::::::::::::::::::::::::::::::::::::::::::::::::
