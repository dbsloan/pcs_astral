# pcs_astral
Scripts for automating Partitioned Coalescence Support (PCS) using ASTRAL

pcs_astral.pl

## Overview: 
This script implements the "partitioned coalescence support" method by automating the process of removing one tree at a time from a set of gene trees and analyzing species trees using ASTRAL (https://github.com/smirarab/ASTRAL). The effect of removing each gene on the support for a reference species tree relative to one or more user-specified alternative topologies is calculated and reported in the form of PCS values.


## Requirements: 

This automation is implemented with a Perl script that has been designed for a Unix environment (Mac OSX or Linux). It has been tested in Mac OSX 10.11 and Linux CentOS 6, but it should work in most Unix environments.

Perl - The provided Perl script should called by users (pcs_astral.pl). Perl is pre-installed in most Mac OSX and Linux distributions.

ASTRAL - The Perl script calls ASTRAL (https://github.com/smirarab/ASTRAL), which must be installed, and the user must provide the full path and file name for the ASTRAL jar file. The script has been tested with ASTRAL 4.7.12 and 4.10.5 but would likely work with other versions.

Java - ASTRAL is written in Java, so Java JDK should be installed and in your PATH.



## Running pcs_astral.pl:
The script can be called from the command line to analyze a set of gene trees with ASTRAL. The user must specify the gene trees, the reference species tree, and at least one alternative topology. There are required parameters that are specified at the command line as described below. Sample data and expected output files are provided in the sample_data directory.


Usage: perl pcs_astral.pl [arguments] > output_file

   REQUIRED ARGUMENTS
   
   The optimal species tree must be specified:
   
         --opt_tree     - file containing optimal species tree topology


   Alternative species tree(s) must be specified with one of the 
   following options (but not both): 

         --at_file      - a single file containing one or more trees

         --at_dir       - a directory containing one or more files each 
                          containing a single tree 


   Gene trees must be specified with one of the following options (but
   not both): 

         --gt_file      - a single file containing one or more trees

         --gt_dir       - a directory containing one or more files each 
                          containing a single tree 
   
   Astral jar file name (including relative path) must be specified:

         --jar_file     - Astral jar file

   EXAMPLE
   
         perl pcs_astral.pl
            --opt_tree=sample_data/species_tree.tre
            --at_file=sample_data/alt_trees_file.tre
            --gt_file=sample_data/gene_trees_file.tre
            --jar_file=astral.4.10.5.jar
            > astral_sample.txt
