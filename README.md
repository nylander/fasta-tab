# fasta $\leftrightarrow$ tab

- Last modified: tis mar 21, 2023  03:49
- Sign: Johan Nylander

## Description

Scripts to transform fasta formatted files to tab separated --- and back.

In addition, two scripts are also provided for converting fasta to csv or tsv
separated files where all positions are separated by the delimiter.

Note: here we use the terms "tab" and "tsv" for different output (see Input and
output examples below).

The scripts reads from STDIN and writes to STDOUT.

## Input and output examples

Input example in fasta format

    >label
    ACGT

Output, tab separated:

    label    ACGT

Output, tsv:

    label    A   C   G   T

Output, csv:

    label,A,C,G,T

## Usage

    # From fasta to tab
    $ fasta2tab infile.fas

    # From tab to fasta
    $ tab2fasta infile.tab

    # From fasta to tsv
    $ fasta2tsv infile.fas

    # From tsv to fasta
    $ tsv2fasta infile.tsv

    # From fasta to csv
    $ fasta2csv infile.fas

    # From csv to fasta
    $ csv2fasta infile.csv

## Examples

    $ fasta2tab infile.fas | sort | tab2fasta > sorted-on-header.fas
    $ fasta2tab infile.fas | sort -k2 | tab2fasta > sorted-on-sequence.fas

## Perl one-liners for fasta to tab

The following oneliners accomplishes the same tasks (fasta - tab).
And remember, "there are several ways to do it"!

    $ perl -0076 -ne 'chomp;($h,@S)=split/\n/;$s=join("",@S);print"$h\t$s\n"unless(!$h)' infile.fas
    $ perl -naF\t -e 'print">$F[0]\n$F[1]\n"' infile.tab

