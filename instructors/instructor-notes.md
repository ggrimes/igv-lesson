---
title: Instructors' Guide
---

## General Notes

This lesson is designed to run in roughly half a day (~1.5 hours teaching,
~2.25 hours of hands-on exercises, plus breaks). It assumes learners already
have IGV installed and the workshop data downloaded (see
[Setup](../learners/setup.md)) — do not spend workshop time on installation
unless you have build in extra time for it.

Episodes 1–2 need an internet connection (they load example data from the
IGV server). Episodes 3–5, 7, and 8 use only local files. Episode 6 needs an
internet connection again for the hosted RNA-seq tutorial data. Episode 9
uses no data at all — it is discussion/demonstration based, walking through
published screenshots rather than a hands-on exercise.

## Pacing advice

It is fine not to get through every episode.
[Viewing Long-Read Sequencing Data](../episodes/09-viewing-long-read-sequencing.md)
is explicitly optional — cover it only if time allows, since it does not use
the workshop data and is not needed for any later episode. If time is short
beyond that, the episodes most worth cutting (in order) are:

1. [Loading Your Own Genome](../episodes/03-loading-your-own-genome.md) — can
  be skipped if learners will only ever use IGV's built-in hosted genomes.
2. [Precomputing Coverage with igvtools](../episodes/05-precomputing-coverage.md)
  — a useful but non-essential workflow detail.

The core episodes — [IGV Basics](../episodes/02-igv-basics.md),
[Viewing Alignments and SNPs](../episodes/04-viewing-alignments-and-snps.md),
and [Viewing Variants and Genotypes](../episodes/07-viewing-variants.md) —
cover the skills learners are most likely to need immediately afterward.

## Common sticking points

- **Loading the wrong thing from "Load from Server."** Learners sometimes
  check the box next to the *Tutorials* folder itself instead of opening it
  and checking a specific dataset inside, which loads far more tracks than
  intended. Watch for this during the first exercise and correct it early —
  it is much easier to prevent than to explain a cluttered screen full of
  unexpected tracks afterward.
- **Loading the `.bai` file.** Learners occasionally try to load the BAM
  index file directly. Remind them IGV finds it automatically.
- **Mixing up the Genomes menu and the File menu.** Loading a genome sequence
  uses **Genomes > Load Genome from File…**; loading every other kind of
  track uses **File > Load from File…**. This distinction trips people up in
  [Loading Your Own Genome](../episodes/03-loading-your-own-genome.md).
- **Not zooming in far enough** before trying to sort/color reads by base in
  [Viewing Alignments and SNPs](../episodes/04-viewing-alignments-and-snps.md)
  — the sort/color options operate on whatever is currently centered in the
  view, so learners need to be at a high enough zoom level that the
  mismatched base is clearly visible and centered first.
- **Forgetting "View as pairs"** in
  [Viewing Structural Variants](../episodes/08-viewing-structural-variants.md)
  — without it, mates are drawn as independent reads and the discordant
  orientation signature at the inversion breakpoint is much harder to spot.

## Adapting this lesson

The exercises are built around a small set of example files (see
[Setup](../learners/setup.md)) chosen because they are small enough to
distribute easily and show clean, unambiguous examples of each concept
(a likely-real SNP vs. a likely-artifact SNP, a clear case of alternative
splicing, a population-stratified variant). If you have your own lab's data
that shows similar patterns, consider substituting it to increase learner
engagement, but keep a copy of the original example data as a fallback in
case your own data doesn't display as cleanly at the zoom levels used in the
exercises.
