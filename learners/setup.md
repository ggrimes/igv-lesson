---
title: Setup
---

## Software: IGV desktop

This lesson uses the IGV **desktop** application (not igv.js or IGV-Web).

1. Go to <https://igv.org/doc/desktop/#DownloadPage/> and download the version
  for your operating system. IGV requires Java, and the downloads for Windows
  and macOS bundle a compatible Java runtime, so no separate Java install is
  needed.
2. Install and launch IGV to confirm it opens before the workshop starts.
3. You will need an internet connection the first time you launch IGV and
  whenever you load data hosted on the IGV server (used in the
  [IGV Basics](02-igv-basics.md) episode). The rest of the lesson uses data
  files stored on your own computer and does not need an internet connection.

## Data

The exercises use a small set of example genomics files (a chromosome
sequence and index, a gene annotation file, a sample BAM alignment file, and
a population VCF file). Download
[igvData.zip](https://github.com/ggrimes/igv-lesson/releases/download/data-v1/igvData.zip)
(~95 MB) and unzip it into a convenient location, such as your Desktop or
home directory.

After unzipping, you should have a folder called `igvData` with the following
structure:

```output
igvData/
├── genome/
│   ├── chr1.fasta
│   ├── chr1.fasta.fai
│   └── refSeq_chr1.bed
├── snps/
│   ├── NA12878.SLX.sample.bam
│   ├── NA12878.SLX.sample.bam.bai
│   └── snp_calls.bed
└── vcf/
    ├── ALL.apol1.sample.phase3_shapeit2_mvncall_integrated_v5a.20130502.genotypes.vcf
    ├── apol1_snp131.bed
    ├── chr22.fa
    ├── chr22.fa.fai
    ├── hg19_chr22.genome
    ├── integrated_call_samples_v3.20130502.ALL.panel
    └── vcf_session.xml
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Optional: structural variants data

The workshop data also includes an `svs/` folder with a BAM file aligned
against human chromosome 21 (hg38) for learners who want to explore
structural variant signatures (discordant read pairs, split reads, coverage
drops) on their own after the lesson. It is not required for any of the core
episodes.

::::::::::::::::::::::::::::::::::::::::::::::::::

Keep track of where you unzipped the `igvData` folder — every exercise refers
back to files inside it.
