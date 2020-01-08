![](./media/image1.gif)

# BIO2092 Practical 4 – Microbial genomics and antimicrobial resistance

## Introduction

The objective of this practical is to gain some further hands-on
experience of next-generation sequencing data and see how it can be analysed
for a real-world application: we are going to focus on predicting
antibiotic resistance (phenotype) from genomic sequence (genotype),
which of course is of particular relevance in microbial pathogens.prediction of antibiotic susceptibility.
Specifically, we will use
whole-genome shotgun sequence data, generated using the Illumina
sequencing platforms (HiSeq and MiSeq). We will use data from pathogenic
bacteria, including some of the same data as in the previous practical session.
This has the advantage that the genomes are quite small (a few
megabases) and so it is feasible to perform the tasks on a standard PC.
Some of what you will learn can also be applied to larger genomes (such
as human genomes) but we would need a lot more compute power, disk space
and RAM. 

## The data

For your convenience, all of the data that you need has been collected
together on the University’s One Drive. You can access the data by following
a link on the ELE page (http://vle.exeter.ac.uk/mod/url/view.php?id=722134).

<img src="./media/image3.png" height="200" />

As the **reference genome sequence**, we will use the [completely assembled
sequence of strain H37Rv](https://www.ncbi.nlm.nih.gov/pubmed/9634230).

You can download it from the `Practical 3 and 4 (Mycobacterium reference genome)` folder on the One Drive (see above).
This is the same reference genome that we used in the previous
practical. You will find a `.fna` file that contains the genomic sequence
in FastA format and you will find a `.gff` file that contains the
annotation of the genome, including predicted genes, in General Feature
Format (GFF). (If you are using the web-based version of IGV, then use the `.fasta` and `.fasta.fai`
files instead of the `.fna` file).

<img src="./media/image4.png" height="200" />

In addition to the reference genome, for today’s practical you also need
some FastQ files containing genomic **sequence reads** of various strains of
*M. tuberculosis*. You also need some .bam and .bai files that contain
alignments of these genomic reads aligned against the reference genome.
You can find all of these files in the `Practical 4 (data for Mycobacterium resistance prediction)`
folder. You can download the whole set of files
by selecting all and hitting the Download button:

<img src="./media/image5.png" height="300" />

This should result in a .zip file being downloaded into your Downloads
folder. You must then extract the files from this `.zip` file by
right-clicking and selecting “Extract All”. This will generate a new
folder in which you will find your files.

<img src="./media/image6.png" height="300" />

<img src="./media/image7.png" height="300" />

## Task 1. Obtain background information about the data.

Try to find some background information about these datasets and fill in
the table. The filenames indicate the Sequence Read Archive (SRA)
accession numbers of these datasets. So, for example, we could look up
ERR1679585 at the European Bioinformatics Institute (EBI) website, which
would take us to here: <https://www.ebi.ac.uk/ena/data/view/ERR1679585>.
On that web page we can see that the data were generated using Illumina
MiSeq and there is a link to BioSample accession number SAMEA4501278.
Clicking on the SAMEA4501278 link brings us to a page that says the
sample name is NG1. On the other hand, there is a link to BioProject
accession PRJEB15857 and clicking the link to this BioProject reveals
some information about the project. In fact a paper about this project [has been
published](https://www.ncbi.nlm.nih.gov/pubmed/?term=28926571)).

  FastQ file name | Sample name | Sequencing platform | Brief description of research project
----------------- | ----------- | ------------------- | --------------------------------------
`ERR1679585.1.fastq.gz` | NG1     | Illumina MiSeq      | Whole-genome sequencing illuminates the evolution and spread of multidrug-resistant tuberculosis in Southwest Nigeria
`ERR1679586.1.fastq.gz` |         |                     | 
`ERR1679587.1.fastq.gz` |         |                     |  
`ERR987695.1.fastq.gz`  |         |                     | 
`ERR987696.1.fastq.gz`  |         |                     |     
`ERR987696.1.fastq.gz`  |         |                     |         
`ERR987697.1.fastq.gz`  |         |                     | 

## Task 2 (optional). Check the quality of your data using the FastQC software.

Now, gather some quality-control information about these datasets. Use the FastQC software to find out how many sequence reads.

  FastQ file name            | Number of reads   | Any comments on the quality of these data
  -----------------------    | ----------------- | -------------------------------------------
  `ERR1679585.1.fastq.gz`    |                   |  
  `ERR1679586.1.fastq.gz`    |                   |
  `ERR1679587.1.fastq.gz`    |                   | 
  `ERR987695.1.fastq.gz`     |                   | 
  `ERR987696.1.fastq.gz`     |                   |
  `ERR987696.1.fastq.gz`     |                   |
  `ERR987697.1.fastq.gz`     |                   |

## Task 3. Predict the antibiotic susceptibility profiles of each bacterial isolate using Mykrobe Predictor.

You have already downloaded the compressed FastQ files for each genome
(`.fastq.gz` files). Now, for each genome, use the [Mykrobe Predictor
software](https://www.ncbi.nlm.nih.gov/pubmed/?term=26686880) 
to predict to which antibiotics these
bacteria will be susceptible or resistant. Pay attention to the
‘Evidence’ section, because this tells you how the software came to the
decision and we will follow up on this later in the practical. The
Mykrobe predictor software may already be installed on the PC, but if you
encounter any problems, then you can download it from the One Drive:

<img src="./media/image20.png" />


Simply drag your compressed FastQ file into the Mykrobe Predictor window
and wait … You should soon see results something like this:

<img src="./media/image8.png" height="300" />

Repeat this process for some or all of the samples and record your
results:

  FastQ files            | Sample name  | *M. tb*. lineage   |  Resistant                        | Susceptible
 ----------------------- | -----------  | ----------------   | -----------------------------     | ------------
  `ERR1679585.1.fastq.gz`  |  NG1         |  European/American | Isoniazid, Rifampicin, Ethambutol | Quinolones, Streptomycin, Amikacin, Capreomycin, Kanamycin
  `ERR1679586.1.fastq.gz`  |              |                    |                                   |
  `ERR1679587.1.fastq.gz`  |              |                    |                                   |
  `ERR987695.1.fastq.gz`   |              |                    |                                   |
  `ERR987696.1.fastq.gz`   |              |                    |                                   |
  `ERR987696.1.fastq.gz`   |              |                    |                                   |
  `ERR987697.1.fastq.gz`   |              |                    |                                   |

Now let’s take a look at the evidence on which the software predictions are based.

<img src="./media/image9.png" height="300" />

For example, note that the software predicts that this bacterial strain
is resistant to rifampicin, based on detection of a mutation in the
*rpoB* gene. Numerous studies
([Casali *et al.*, 2016](https://www.ncbi.nlm.nih.gov/pubmed/?term=27701423);
[Coll *et al.*, 2017](https://www.ncbi.nlm.nih.gov/pubmed/29358649);
[Grandjean *et al.*, 2017](https://www.ncbi.nlm.nih.gov/pubmed/?term=29281674);
[Naidoo and Pillay, 2017](https://www.ncbi.nlm.nih.gov/pubmed/?term=28947708);
[Senghore *et al.*, 2017](https://www.ncbi.nlm.nih.gov/pubmed/?term=28926571))
have reported correlations between particular mutations in
*rpoB* (and a few other genes) and resistance to antibiotics in M.
tuberculosis.
These mutations alter the structure of the encoded protein
such that they are no longer effectively targeted by the antibiotic.
Several naturally occurring mutations in *rpoB* are known to confer
rifampicin resistance. See for example this figure
(from [this paper](http://dx.doi.org/10.1016/j.cmi.2016.09.006))
listing known mutations in the *rpoB* gene associated with
rifampicin resistance. **Let’s see whether we can find the
resistance-conferring mutations** in our data in the next task …

<img src="./media/image10.png"/>

## Task 4. View the raw data using the Integrated Genome Viewer (IGV) software

We are going to use [the IGV software](https://www.ncbi.nlm.nih.gov/pubmed/?term=22517427) to
view the genome sequence reads aligned against a reference genome (as
discussed in previous lectures and as you have used previously in
practicals). It will look something like the images below:

<img src="./media/image11.png" height="300" />


In preparation for this session, I have aligned each of the sequence
datasets against the reference genome sequence. You have already
downloaded these as `.bam` and `.bam.bai` files.

<img src="./media/image13.png" height="300" />

Please follow these steps to view the data:

* You need to download both the `.bam` files and the `.bai` files to
    your local PC.

* Make sure that you have downloaded the reference genome files

* Launch the IGV software. Spend a little bit of time familiarising
    yourself with zooming in and out and navigating around the genome if
    you have not already mastered this.

* In the IGV software, load the reference genome `.fna` file, using
    the `Genomes ->Load Genome from File` menu.

* Load the `.gff` annotation (gene predictions *etc*.) file for the
    reference genome, using the `File -> Load from File` menu.

* Load the `.bam` files using the `File -> Load from File` menu.
    The corresponding `.bai` files must be present in the same folder as
    the `.bam` files.
    
* Remember, if you are using the web-based version of IGV, you need to simultaneously load the `.bam.bai` files along with the `.bam` files.    

* Navigate to this position on the genome: 759807 - 763325. You should
    be able to see *rpoB* gene. What is the relevance of this gene to
    antibiotic resistance? What sequence variation do you observe in
    this gene?

Here is an overview of the data for the *rpoB* gene in our several
samples:

<img src="./media/image14.png" height="300" />

Here, we zoom in on the S40X mutation in *rpoB*:

<img src="./media/image15.png" height="300" />

What about the mutation in the His residue in the second sample? Will
this have any impact on drug resistance? You can find a full list of the
mutations that Mykrobe predictor uses in [Supplementary Table 15](https://media.nature.com/original/nature-assets/ncomms/2015/151221/ncomms10063/extref/ncomms10063-s1.pdf) of the
[published paper](https://www.ncbi.nlm.nih.gov/pubmed/?term=26686880).

Now, in what time you have left, have a look at some other
antibiotic-resistance-associated loci and check whether the genomic
sequence data are consistent with the Mykrobe Predictor results that you
generated and tabulated earlier. Summarise your findings in the
table below.

  Locus     | Genomic position  | Any resistance-associated mutations? |  Relevant resistance prediction (from Mykrobe predictor)
  --------- | ----------------- | ------------------------------------ | ---------------------------------------------------------
  *rpoB*    | 759807-763325     |                                      |   
  *katG*    | 2153889-2156111   |                                      |  
  *fabG1*   | 1673440-1674183   |                                      |  
  *gyrA*    | 7302-9818         |                                      |  
  *embB*    | 4246514-4249810   |                                      |  
  *rpsL*    | 781560-781934     |                                      |  

