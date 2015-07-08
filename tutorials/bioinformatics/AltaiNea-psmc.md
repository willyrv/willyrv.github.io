---
layout: post
title:  "Applying PSMC to Neandertal data"
date:   2015-07-08 18:38:58
---

Guidelines to apply the psmc to Neandertal data
===============================================

In 2014, it was published *The complete genome sequence of a Neanderthal from
the Altai Mountains* in
[nature](http://www.nature.com/nature/journal/v505/n7481/full/nature12886.html).
As a part of their study, authors did a psmc analysis with the data. I describe
here how I was able to reproduce the analysis at July 3, 2015.
The tools I used where:
* [samtools](https://github.com/samtools/samtools) version 1.2-88-gf845404
* [htslib](https://github.com/samtools/htslib) version 1.2.1-125-g3a95a67
* [bcftools](https://github.com/samtools/bcftools) version 1.2-46-g6baab20

**First we download and compile the tools**

```
git clone https://github.com/samtools/samtools.git
git clone https://github.com/samtools/htslib.git
git clone https://github.com/samtools/bcftools.git

cd bcftools
make
cd ../samtools
make
```

The read sequences of the AltaiNeandertal where aligned to the the GRCh37 build
of the [human reference](ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/technical/reference/human_g1k_v37.fasta.gz)

Assume we have all the aligned chromosomes in a folder called "bam", named
*chr1.bam*, *chr2.bam* and so on.

We must first uncompress and index the reference file

```
gunzip ./human_g1k_v37.fasta.gz
./samtools/samtools faidx human_g1k_v37.fasta
```

This will produce a file *human_g1k_v37.fasta.fai*

Now I run the following pipeline:

```
./samtools/samtools mpileup -C50 -uf ./human_g1k_v37.fasta ./bam/chr1.bam | \
./bcftools/bcftools call -c | ./bcftools/vcfutils.pl vcf2fq -d 10 -D 100 | \
gzip > ./chr1.fq.gz
```

Note: Samtools is also able to open a BAM (not SAM) file on a remote FTP or HTTP
 server (see the [doc](http://www.htslib.org/doc/samtools.html)). So in the last
 command we could replace *./bam/chr1.bam* by the link to the bam file in the
 server (i.e. http://cdna.eva.mpg.de/neandertal/altai/AltaiNeandertal/bam/AltaiNea.hg19_1000g.1.dq.bam)


By using the last pipeline I was able to have one fq file per chromosome.
The .fq file produced by vcfutils.pl contains lowercase and uppercase letters (eg
  'nnATgagtttAGnn') wich is a bit confusing given that a fasta sequence (normally)
  should contains only *uppercase* characters (see the [fastq Format
    Specification](http://maq.sourceforge.net/fastq.shtml)). After a bit of
    goggling it seems that lowercase indicates low coverage.

In order to get the input sequence for psmc, I used the *fq2psmcfa* tool that
comes with the [psmc](https://github.com/lh3/psmc) software. For each chromosome

```
for i in {1..22};
  do ../psmc/utils/fq2psmcfa -q20 ./chr$i.fq.gz > chr$i.psmcfa;
done
```
And finally, I put all the chromosomes together in a single file.

```
for i in {1..22};
  do cat ./chr$i.psmcfa >> AltaiNea.psmcfa;
done
```

Now I can run the psmc analysis. I use the deffault parameters. Assuming you
have a compiled version of the psmc inside a folder called psmc and your data
(the file AltaiNea.psmcfa) is in the current directory, you can do:

```
./psmc/psmc -N25 -t15 -r5 -p "4+25*2+4+6" -o ./AltaiNea.psmc ./AltaiNea.psmcfa
```

This will produce the psmc inferred history (it could take a while). The output
will be written in a file named AltaiNea.psmc

To make a plot and see the inferred demographic history, you can type

```
./psmc/utils/psmc_plot.pl -p ./AltaiNea.pdf ./AltaiNea.psmc
```

This will produce a pdf file with a plot of the demographic history.
