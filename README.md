# fasta $\leftrightarrow$ tab

- Last modified: mån okt 21, 2019  09:08
- Sign: Johan Nylander

## Description

Perlscripts to transform fasta formatted files to tab separated --- and back.

The scripts read from STDIN and writes to STDOUT.

## Usage

#### From fasta to tab

    fasta2tab infile(s).fas

#### From tab to fasta

    tab2fasta infile(s).tsv

#### Example

    fasta2tab infile.fas | sort | tab2fasta > sorted.fas

## Perl oneliners

The following oneliners accomplishes the same tasks.
And remember, "there are several ways to do it"!

#### From fasta to tab

    perl -0076 -ne 'chomp;($h,@S)=split/\n/;$s=join("",@S);print"$h\t$s\n"unless(!$h)' infile(s).fas

#### From tab to fasta

    perl -naF\t -e 'print">$F[0]\n$F[1]\n"' infile(s).tsv
