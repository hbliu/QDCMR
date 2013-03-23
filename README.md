========================
README for QDCMR (1.0.0)
========================
Time-stamp: 2013-03-23 12:32:12 Hongbo Liu


Introduction
============
Epigenetic modifications play critical roles in the regulation of gene expression and chromatin remodeling.
Chromatin immunoprecipitation (ChIP) followed by high-throughput sequencing (ChIP-Seq) has been widely used for genome-wide profiling of chromatin modifications and DNA-binding proteins.
The unprecedented scale and precision of epigenomic data have enabled the quantitative analysis of differential epigenetic status in gene regulation in various biological processes.
To address the lack of powerful ChIP-Seq analysis method, we present a novel algorithm, named Quantitative Differential Chromatin Modification Region (QDCMR). 
QDCMR provides a quantitative approach to quantify chromatin modification difference and identify DCMRs from genome-wide chromatin modification profiles by adapting Shannon entropy. Its platform-free and species-free nature makes it easy for computational biologists to analysis the epigenetic regulation related with DCMRs across various temporal and spatial chromatin modifications. 

Install
=======
Currently, QDCMR can be executed with visual interface (QDCMRforView) and in command line (QDCMRforCommand). 
As of Release 1.0, QDCMR , whether QDCMRforView or QDCMRforCommand, can be configured to run under Java 1.6 or higher. Please make sure that you have a recent version of Java installed. If QDCMR can't work, you can try to install a recent version of Java runtime first.

QDCMR with visual interface (QDCMRforView)
==========================================

Function of QDCMRforView
------------------------

The QDCMR with visual interface facilates users to handle ChIP-Seq data. This version of QDCMR provides users the following functions: 

__1.  Import Data:__	Preprocess and import chromatin modification data.

__2.  Quantify Difference:__	Quantify chromatin modification difference across various samples.

__3.  Identify DCMRs:__	Identify DCMRs by threshold imbedded in QDCMR.

__4.  Measure Specificity:__	Measure sample-specificity for each DCMRs.

__5.  Export Results:__	Save results.

__6.  Visualization:__	Display chromatin modification level, DCMR distribution and UCSC links.

Usage of QDCMRforView
---------------------

Download the compressed package named as "QDCMRforView.rar", and decompress it. 
For windows please Double Click run StartWin.bat file
For linux please run StartLinux.sh file
The file named as "Tutorial.html" embedded in QDCMRforView.rar provides more ditailed information about QDCMRforView.



QDCMR in command line (QDCMRforCommand)
=======================================
Function of QDCMRforCommand
---------------------------

The QDCMR in command line facilates users to handle huge ChIP-Seq data in server automatically. This version of QDCMR cen  process the data automatically according to user's commond. 

Usage of QDCMRforCommand
------------------------

Download the compressed package named as "QDCMRforCommand.rar", and decompress it.

__For the processed data__


>``java -jar -Xmx1024m QDCMR.jar -P infile=example.gct,ResultFolder=Result,SD=0.07``

>__Example command__

>``java -jar -Xmx1024m QDCMR.jar -P infile=/pub2/hbliu/QDCMR/DATA/example.gct,ResultFolder=/pub2/hbliu/QDCMR/DATA/Result,SD=0.07``

>*   __-Xmx1024m:__     Use maximum memory for 1024M.
>*   __-P:__            For processed data.
>*   __infile:__        The file path for the import data including the regions with chromation modifiction data across mutiple samples (File format is gct).
>*   __ResultFolder:__  The folder path for the export of analysis results of QDCMR.
>*   __SD:__            Standard Deviation--the standard deviation of probablity model for DCMR threshold.


__For the region and raw chromatin modification data__

>``java -jar -Xmx1024m QDCMR.jar -R RegionFile=example.bed,ReadFolder=ReadFile,ResultFolder=Result,SD=0.07,ExpandLength=200,BinSize=1,DepthNormalization=NO``

>__Example command__

>``java -jar -Xmx1024m QDCMR.jar -R RegionFile=/pub2/hbliu/QDCMR/DATA/example.bed,ReadFolder=/pub2/hbliu/QDCMR/DATA/ReadFile,ResultFolder=/pub2/hbliu/QDCMR/DATA/Result,SD=0.07,ExpandLength=200,BinSize=1,DepthNormalization=NO``

>There are seven major functions available in QDCMR serving as sub-commands.

>*   __-Xmx1024m:__ Use maximum memory for 1024M.
>*   __-R:__ For region and raw chromatin modification data.
>*   __RegionFile:__ The file path for the import region data (File format is bed).
>*   __ReadFolder:__ The folder path including the raw read files of Chromatin Modifications by ChIP-Seq (Read file formatfor is bed).
>*   __ResultFolder:__ The folder path for the export of analysis results of QDCMR.
>*   __SD:__ Standard Deviation--the standard deviation of probablity model for DCMR threshold.
>*   __Expand Length:__ Applicable to the single-terminal sequencing data. User can select or input the suitable length of sequence represented by each read. Each read is expanded to the length firstly, and then mapped to corresponding region.
>*   __Bin Size:__ The unit of region segment. The default value is 1 bp meaning the total read number in each region is normalized by the region length.
>*   __Depth Normalization:__ (YES or NO,YES--In Depth Normalization,NO--Don't Depth Normalization)Considering the different sequencing depth of ChIP-Seq files, the read number is further normalized by the total read number of the given ChiP-Seq file relative to the mean of the total read numbers of the all used ChiP-Seq files.


Format guide
============

BED
---

>__Tab delimited format (tabular)__
>
>__Does not require header line__
>
>__Contains 6 required fields:__
>
>__chrom__ - The name of the chromosome (e.g. chr3, chrY, chr2_random) or contig (e.g. ctgY1).
>
>__chromStart__ - The starting position of the feature in the chromosome or contig. The first base in a chromosome is numbered 0.
>
>__chromEnd__ - The ending position of the feature in the chromosome or contig. The chromEnd base is not included in the display of the
>
>__description1__ - The description for the region, such as region id, gene name et al.
>
>__description2__ - The description for the region, such as region id, gene name et al.
>
>__strand__ - Defines the strand - either '+' or '-'.
>
>bed format online:http://genome.ucsc.edu/FAQ/FAQformat.html#format1


GCT
---

>__Add two header rows at the top of the file:__ 

>In the first row, first cell, enter: #1.2

>In the second row, first cell, enter the number of data rows: N

>In the second row, second cell, enter the number of data columns: M

>In the third row is header line

>In the next is data,Former two columns is ID and description,and later is data matrix to N*M

>gct format online:http://www.broadinstitute.org/cancer/software/genepattern/gp_guides/file-formats#_Creating_Input_Files_GCT


Other useful links
==================
__QDMR__, a tool for identification and analysis differentially methylated regions: http://bioinfo.hrbmu.edu.cn/qdmr/

__GCER__, Our group http://202.97.205.78/gcer/

__MACS__, a tool for ChIP-chip/seq analysis: https://github.com/taoliu/MACS

__bedTools__, a super useful toolkits for genome annotation files: http://code.google.com/p/bedtools/


				        
