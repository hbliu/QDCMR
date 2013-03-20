The processed data submitted by user:
========================================
	#Example Command:java -jar -Xmx1024m QDCMR.jar -P infile=/pub2/hbliu/QDCMR/DATA/example.gct,ResultFolder=/pub2/hbliu/QDCMR/DATA/Result,SD=0.07
		* __-Xmx1024m:__Use maximum memory for 1024M.
		* __-P:__for processed data.
		* __infile:__the file path for the import data including the regions with chromation modifiction data across mutiple samples (File format is gct).
		* __ResultFolder:__the folder path for the export of analysis results of QDCMR.
		* __SD:__Standard Deviation--the standard deviation of probablity model for DCMR threshold.

The region and raw chromatin modification data submitted by user:
=================================================================
	#Example Command:java -jar -Xmx1024m QDCMR.jar -R RegionFile=/pub2/hbliu/QDCMR/DATA/example.bed,ReadFolder=/pub2/hbliu/QDCMR/DATA/ReadFile,ResultFolder=/pub2/hbliu/QDCMR/DATA/Result,SD=0.07,ExpandLength=200,BinSize=1,DepthNormalization=NO
		* __-Xmx1024m:__Use maximum memory for 1024M.
		* __-R:__for region and raw chromatin modification data.
		* __RegionFile:__the file path for the import region data (File format is bed).
		* __ReadFolder:__the folder path including the raw read files of Chromatin Modifications by ChIP-Seq (Read file formatfor is bed).
		* __ResultFolder:__the folder path for the export of analysis results of QDCMR.
		* __SD:__Standard Deviation--the standard deviation of probablity model for DCMR threshold.
		* __Expand Length:__ Applicable to the single-terminal sequencing data. User can select or input the suitable length of sequence represented by each read. Each read is expanded to the length firstly, and then mapped to corresponding region.
    * __Bin Size:__ the unit of region segment. The default value is 1 bp meaning the total read number in each region is normalized by the region length.
    * __Depth Normalization:__ (YES or NO,YES--In Depth Normalization,NO--Don't Depth Normalization)Considering the different sequencing depth of ChIP-Seq files, the read number is further normalized by the total read number of the given ChiP-Seq file relative to the mean of the total read numbers of the all used ChiP-Seq files.

##Format guide:
#Bed 
>__Tab delimited format (tabular)__
>__Does not require header line__
>__Contains 6 required fields:__
 >__chrom__ - The name of the chromosome (e.g. chr3, chrY, chr2_random) or contig (e.g. ctgY1).
 >__chromStart__ - The starting position of the feature in the chromosome or contig. The first base in a chromosome is numbered 0.
 >__chromEnd__ - The ending position of the feature in the chromosome or contig. The chromEnd base is not included in the display of the
 >__description1__ - The description for the region, such as region id, gene name et al.
 >__description2__ - The description for the region, such as region id, gene name et al.
 >__strand__ - Defines the strand - either '+' or '-'.
>bed format online:http://genome.ucsc.edu/FAQ/FAQformat.html#format1

#gct
>__Tab delimited format (tabular)__
>__Add two header rows at the top of the file:__ 
	>In the first row, first cell, enter: #1.2
	>In the second row, first cell, enter the number of data rows: N
	>In the second row, second cell, enter the number of data columns: M
	>In the third row is header line
	>In the next is data,Former two columns is ID and description,and later is data matrix to N*M
>gct format online:http://www.broadinstitute.org/cancer/software/genepattern/gp_guides/file-formats#_Creating_Input_Files_GCT