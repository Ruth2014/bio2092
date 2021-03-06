  ![](./media/image1.gif)
   
# BIO2092 Practical 2: Introduction to handling “next-generation” sequencing data

## Introduction
During the first few lectures on this course, you have heard a lot about
so-called “next-generation” sequencing (NGS) methods such as Illumina.
These methods have been available since around 2006 and in the last
decade or so have hugely expanded the limits of what is achievable in
all kinds of fields of biological and biomedical research. You have also
heard about the Sanger method, which has been available since the 1970s.
In this practical session, you will consolidate your understanding of
the data generated by these methods and some of the approaches to
analysing such data.


## Laboratory simulation of NGS 
  
* Please work through this Labster simulation. This will take approximately 30 - 50 minutes.
(This simulation covers material that has appeared in exam previous questions!)  
 
<img src="./media/image3.png" height="200"/>
 
It is based on a real published research study involving the sequencing of ancient DNA from remains of a man who lived about 4000 years ago (Rasmussen *et al.*, 2010).   
You can access this simulation via the link on the [Labster section of the BIO2092 ELE page](https://vle.exeter.ac.uk/course/view.php?id=4041#section-8).

## Accessing the sequence data from study of a 4000-year-old human
All the sequencing data from this study are available through the public
repositories. Specifically, the raw sequence reads are available from
either the Sequence Read Archive (SRA) in the USA or the European
Sequence Archive (ENA) in Europe.

Navigate to the research paper at <https://www.ncbi.nlm.nih.gov/pubmed/?term=20148029> and try to find a hyperlink to the sequence data. Alternatively, if you look at the text of the paper in *Nature*, you will read that “Sequences have been deposited to the short read archive with accession number SRA010102”.   

<img src="./media/image4.png" height="300"/>
   
If you [follow the "SRA" hyperlink](https://www.ncbi.nlm.nih.gov/sra?LinkName=pubmed_sra&from_uid=20148029)
or search the NCBI portal for this accession
number, you will arrive a page like this, describing the data from this
study that is held in the SRA:

<img src="./media/image5.png" height="300"/>

This is telling us that there are 59 datasets associated with this
project. Click on the link "[Send results to Run selector](https://www.ncbi.nlm.nih.gov/Traces/study/?WebEnv=NCID_1_111035670_130.14.18.48_5555_1548934073_662260917_0MetA0_S_HStore&query_key=10)" to explore these in a bit
more detail ...

The 'Run selecter' looks like this:

<img src="./media/image6.png" height="300"/>

Note that in the public databases, sequence data are organised into projects (BioProjects) and samples (BioSamples).
One sample of biological material might have been sequenced once or several times. And one project might involve 
sequencing of several different biological samples.

In the case of this human palaeosequencing project, the BioProject contains only one BioSample. 

Click on the links (in the Run selecter) to the BioProject and the BioSample to find answers to the questions below.

Question                                                                          | Answer (You can write in here or on a separate sheet of paper)
--------------------------------------------------------------------------------  | ------------------------
How many base-pairs of data, in total, were generated in this research project?   |
Which DNA sequencing method(s) did the researcher use?                            |
What information can you find about the geographic location of the sample?        |
From which tissue was the DNA extracted?                                          |


Now we are going to take a look at the actual sequence data.

Within a sequencing project (BioProject), for a single sample (BioSample) the sequencing data
are organised into "studies", “experiments” and “runs”.
One study can contain multiple experiments and one experiment can
contain multiple runs. A “run” essentially means one set of data, generated by running the sequencing machine once.
Don't worry too much about the specific details of studies, experiments and runs and how they relate to each other; I mention
them just in case you were wondering. The important thing is that we want to navigate to an individual "run". So, let's go ... 

Here is our [list of "experiments" belonging to this project](https://www.ncbi.nlm.nih.gov/sra?LinkName=pubmed_sra&from_uid=20148029):

<img src="./media/image9.png" height="300"/>

Click on one of the links to an “experiment". That will take you to the details of one experiment.
It will look something like this:

<img src="./media/image10.png" height="300"/>

Next, click on a link to a “run”. You will see the details of one run, which will look something like this:

<img src="./media/image11.png" height="300"/>
                                                                                                                                         
Now, we are ready to look at the actual sequence data, *i.e.* the sequence reads.
If you click on the “Reads” tab within the run, you can start
browsing the actual sequence reads:

<img src="./media/image12.png" height="300"/>

Note that each base in the sequence read is given a quality score. 
(You might need to click on the tickbox labelled "quality scores" to ensure that the scores are visible.
Also, under "advanced options", try clicking the tickbox labelled "quality score with bases".)
This quality score is usually between 0 and 40 and denotes how confident we are in
that particular base having been called correctly. The scores use the
Phred system (Ewing and Green, 1998; Ewing *et al.*, 1998):

Phred score       | Probability that the base is wrong       | Accuracy
----------------- | ---------------------------------------- | --------------
10                |  1 in 10                                 | 90 %
20                |  1 in 100                                | 99 %
30                |  1 in 1000                               | 99.9 %
40                |  1 in 10000                              | 99.99 %

What do you think about the quality/accuracy of the DNA sequencing in this research study? Good or bad?

What factors do you think might have contributed to this? 
                                                                                              
## Downloading NGS data
It’s all very well examining individual sequence reads, but the whole
point of NGS is that it generates huge numbers of sequence reads … more
than you would ever have time to examine one-by-one. So, how can we
download a whole set of sequence reads?
  
As you can see, clicking on the “Download” tab does not help much.
To download data from the SRA you need to use a software package called the SRA Toolkit.
This is a really useful suite of software tools for a skilled bioinformatician, but is not very
user-friendly for a novice.

<img src="./media/image13.png" height="300"/>

Rather than using the SRA Toolkit, we will use a simpler solution instead. We will download the same data from the European
Bioinformatics Institute (EBI) website. Essentially the same data are mirrored at the USA site (NCBI) and the European site (EBI)
but the web interfaces for the two sites are quite different.
                                                                                                                                         
Try to navigate to the palaeo-eskimo sequencing data on [the EBI website](https://www.ebi.ac.uk/),
using the search tool.

<img src="./media/image14.png" height="300"/>
                                                                                                                                     
Alternatively, we can go directly to the relevant BioProject via this link: <https://www.ebi.ac.uk/ena/data/view/PRJNA46213>   
                                                                                                                                     
One advantage of EBI’s webpages is that it allows us to directly download whole sets of reads from their site,
rather than having to use special software like the NCBI's SRA Toolkit.        
                                                                                                                                     
                                                                                                                                    
Download one of the sequence files. Choose the option of “FASTQ files (FTP)”.
Once you have downloaded your FastQ file, you will need to unzip it using something like WinZip.                               

## FastQ file format
The standard file format for storing and distributing NGS data is called
FastQ. You can read more about this format in a published paper (Cock
*et al.*, 2010) that is included at the back of this document, and the
formal specification of the format
(<http://maq.sourceforge.net/fastq.shtml>). The Wikipedia article about
FastQ is very informative too. You may already be familiar with FastA as
a format for representing nucleotide and amino-acid sequences. Why do
you think this format is called FastQ? The main advantage of FastQ over
FastA is that it can neatly include not only the sequence itself but
also the quality scores for each base in the sequence.

The FastQ format looks like this:

<img src="./media/image16.png" height="300"/>

Can you think of any advantage of representing the quality scores in this manner rather than what we saw on the NCBI website?

Can you write the quality scores for each base in the following sequence read? You will need to use the [ASCII code](https://www.ascii-code.com/) to decode the symbols. Recall from [Lecture 3](https://vle.exeter.ac.uk/mod/resource/view.php?id=850462) that there is an offset of 33.

```@HISEQ:326:C4DKDACXX:1:1101:1729:2243 1:N:0:GTGGCC
GTGCTCACCGCCCCGGATGCCTTCGCCCAGGTCAGGGACGCCCTGGCCGC
+
CBCFFFFFHHHHHJIJJJJJJFEIIJIJJJICHIJJJJJJHHFFFDEEDD
```                                              
Sequence |G|T|G|C|T|C|A|C|C|G|C|C|C|C|G|G|A|T|G|C|C|T|T|C|G|C|C|C|A|G|G|T|C|A|G|G|G|A|C|G|C|C|C|T|G|G|C|C|G|C
 -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- 
 Symbol |C|B|C|F|F|F|F|F|H|H|H|H|H|J|I|J|J|J|J|J|J|F|E|I|I|J|I|J|J|J|I|C|H|I|J|J|J|J|J|J|H|H|F|F|F|D|E|E|D|D
 Score |  |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   
   

## Assessing the quality of sequence data (in FastQ format)
You now know how to manually extract the quality scores for the base at
each position in a sequence read and hence make some judgement about the
reliability of the data. However, clearly this would not be a feasible
approach when dealing with large numbers of reads. Now you are going to
use a software package called FastQC to assess the quality of the whole
set of sequence reads rather than just looking at a single read.
Earlier, you downloaded a FastQ file from the EBI’s website. Please
assess the quality of that FastQ file using FastQC, as illustrated
below. You can find out more about FastQC at its website
(<http://www.bioinformatics.bbsrc.ac.uk/projects/fastqc/>).

### Launching the FastQC software in Windows:

<img src="./media/image18.png" height="300"/>

<img src="./media/image19.png" height="300"/>

### Opening a FastQ file in the FastQC software:

<img src="./media/image20.png" height="300"/>

### Now wait a minute while the FastQC software analyses the FastQ file:

<img src="./media/image21.png" height="300"/>

The FastQC program performs a number of tests which determines whether a
green tick (pass), exclamation mark (warning) or red cross (fail) is
displayed. However, it is important to realise that FastQC has no
knowledge of what your DNA library is or should look like. All of its
tests are based on a completely random library with 50% GC content.
Therefore, if you have a sample which does not match these assumptions,
it may 'fail' the library. For example, if you have a high AT or high GC
organism it may fail the per sequence GC content. If you have any
barcodes or low complexity libraries (e.g. small RNA libraries) they may
also fail some of the sequence complexity tests.

If for any reason FastQC is not installed on your PC, you can obtain it from here:
https://www.bioinformatics.babraham.ac.uk/projects/fastqc/
After unzipping the downloaded file, click on the file called ```run_fastqc.bat```
to execute the program.

IF you cannot get FastQC to work, then you can find some example output here:
https://universityofexeteruk-my.sharepoint.com/:f:/g/personal/d_j_studholme_exeter_ac_uk/ElG8e7OFrDtNmoz3IgHakJQBILMypp48-QqLcFWtQ412Wg?e=ERhTaa



Now let’s take a tour through the more important information provided by
FastQC about our sequence dataset.

### Quality scores
This view shows an overview of the range of quality values
across all bases at each position in the FASTQ file. Generally anything
with a median quality score greater than Q20 is regarded as acceptable;
anything above Q30 is regarded as 'good'.

<img src="./media/image22.png" height="300"/>

In this case, this check is red - and it is true that the quality drops
off at the end of the reads. It is normal for read quality to get worse
towards the end of the read. You can see that at 250 bases the quality
is still very good. We could simply trim the sequence reads down to 250
bp to eliminate most of the poor-quality data.

Note that what we are looking at is [“box and whiskers” plots]
(http://www.bbc.co.uk/schools/gcsebitesize/maths/statistics/representingdata3hirev6.shtml)
of the quality scores at each position.  
                                                             
### Per-tile sequence quality
This is a purely technical view on the sequencing run; it is more
important for the team running the sequencer than for the biologist end-user of the data.
The sequencing flowcell is
divided up into areas called cells. You can see that the read quality
drops off in some cells faster than others. This maybe because of the
way the sample flowed over the flowcell, a bubble, or a mark/smear on the lens
of the sequencing instrument's optical system.

<img src="./media/image24.png" height="300"/>

### Per-base sequence content
For a completely randomly generated library with a GC content of 50% one
expects that at any given position within a read there will be a 25%
chance of finding an A, C, T or G base. Here we can see that our library
satisfies these criteria, although there appears to be some minor bias
at the beginning of the read. This may be due to PCR duplicates during
amplification or during library preparation. 
A perfectly uniform distribution is unlikely.

<img src="./media/image25.png" height="300"/>

### Sequence duplication levels
In a library that covers a whole genome uniformly, most sequences will
occur only once in the final set. A low level of duplication may
indicate a very high level of coverage of the target sequence, but a
high level of duplication is more likely to indicate some kind of
enrichment bias (e.g. PCR over-amplification). FastQC counts the degree
of duplication for every sequence in the set and creates a plot showing
the relative number of sequences with different degrees of duplication.

<img src="./media/image26.png" height="300"/>

Finally, please gather the following information about your downloaded
dataset. Some of this information can be found on the websites and some
can be found using the FastQC software.

Question  | You can write your answer in here on a separate sheet of paper
-------------------------  | ---------------------------------------------
Filename of the FastQ file |                                                                            
Accession number of the sequencing run. This will likely begin with “SRR”. |                             
How many sequence reads are there in this file?     |                                                   
What is the length of the sequence reads?   |                                                           
Would you recommend trimming the ends of the reads before further analysis? If so, then by how much?   |
Are there any other problems with the quality of the data? If so, what are they?  |                    

**Well done!** you made it to the end. In subsequent computer practicals, we
will look at the main approaches to utilising NGS data (following
quality control); that is alignment to a reference sequence and *de
novo* assembly. For alignment to a reference sequence, we will explore
the use of a genome browser software.

If you have spare time and are curious, you may wish to take a look at the sequence data associated with the
Oxford *Candida auris* outbreak that we discussed in the lecture and [described in this paper](https://doi.org/10.1136/bmj.k4133).
You can browse the data here: https://www.ncbi.nlm.nih.gov/bioproject/415955.

OR, if you have spare time, you may wish to begin the next computer practical, here: https://github.com/davidjstudholme/bio2092/tree/master/03_Genomic_NGS_alignment

