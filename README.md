2021_Spring_Areej's Advanced Genomics Notebook

##Day 02 22-Jan-2021
* Exercise day02
```sh

#1 - logon to the cluster @turing.hpc.odu.edu
[amali010@turing1 ~]$ ls
data  exercises  hpc-intro

#2 - make a directory in your course workspace called data
[amali010@turing1 ~]$ mkdir data

#3 - make a directory called exercises in your data directory
[amali010@turing1 data]$ mkdir exercises

#4 - execute a pwd command and start a log of your commands with a 
header for today's date in your README.md github logfile in your workspace
[amali010@turing1 exercises]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/exercises 

#5 - cp the Exercise2.fasta.gz and Exercise2.fastq.tar.gz files into your 
exercises directory from the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02 directory
[amali010@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02/Exercise2.fast* ./
[amali010@turing1 exercises]$ ls
Exercise2_djb.fasta.gz  Exercise2.fasta.gz  Exercise2.fastq.tar.gz
Exercise2.fasta         Exercise2.fastq
[amali010@turing1 exercises]$ ls -alh
total 37M
drwxrwxrwx 2 amali010 users  146 Jan 26 20:48 .
drwxrwxrwx 4 amali010 users  188 Jan 28 17:31 ..
-rwxr-xr-x 1 dbarshis users 4.3M Jan 26 20:48 Exercise2_djb.fasta.gz
-rwxr-xr-x 1 amali010 users    0 Jan 29 09:53 Exercise2.fasta
-rw-r--r-- 1 amali010 users  18M Sep  2  2015 Exercise2.fastq
-rwxr-xr-x 1 dbarshis users 4.3M Jan 22 13:51 Exercise2.fastq.tar.gz

#6 - unzip and untar the files
[amali010@turing1 exercises]$ gunzip -c Exercise2_djb.fasta.gz > Exercise2.fasta
[amali010@turing1 exercises]$ ls
Exercise2_djb.fasta.gz  Exercise2.fasta  Exercise2.fastq  Exercise2.fastq.tar.gz
[amali010@turing1 exercises]$ ls -alh
total 61M
drwxrwxrwx 2 amali010 users  146 Jan 26 20:48 .
drwxrwxrwx 4 amali010 users  188 Jan 28 17:31 ..
-rwxr-xr-x 1 dbarshis users 4.3M Jan 26 20:48 Exercise2_djb.fasta.gz
-rwxr-xr-x 1 amali010 users  17M Jan 29 09:55 Exercise2.fasta
-rw-r--r-- 1 amali010 users  18M Sep  2  2015 Exercise2.fastq
-rwxr-xr-x 1 dbarshis users 4.3M Jan 22 13:51 Exercise2.fastq.tar.gz

[amali010@turing1 exercises]$ tar -zxvf Exercise2.fastq.tar.gz
Exercise2.fastq
[amali010@turing1 exercises]$ ls -alh
total 69M
drwxrwxrwx 2 amali010 users  182 Jan 29 10:11 .
drwxrwxrwx 4 amali010 users  188 Jan 28 17:31 ..
-rwxr-xr-x 1 dbarshis users 4.3M Jan 26 20:48 Exercise2_djb.fasta.gz
-rwxr-xr-x 1 amali010 users  17M Jan 29 09:55 Exercise2.fasta
-rwxr-xr-x 1 amali010 users 4.3M Jan 29 10:06 Exercise2.fasta.gz
-rw-r--r-- 1 amali010 users  18M Sep  2  2015 Exercise2.fastq
-rwxr-xr-x 1 dbarshis users 4.3M Jan 22 13:51 Exercise2.fastq.tar.gz

#7 - add these commands to your notebook
Done

#8 - calculate how many sequences are in each file and add these 
results to your notebook file
[amali010@turing1 exercises]$ head -1 Exercise2.fasta
>scaffold10078|size20675
[amali010@turing1 exercises]$ grep -c '>' Exercise2.fasta
138
[amali010@turing1 exercises]$ head -1 Exercise2.fastq
@HS3:541:HAYTUADXX:1:1101:1297:1938 1:N:0:AGTTCC
[amali010@turing1 exercises]$ grep -c '@HS3' Exercise2.fastq
61304
[amali010@turing1 exercises]$ wc -l Exercise2.fastq
245216 Exercise2.fastq
[amali010@turing1 exercises]$ echo 245216/4 | bc -l
61304.00000000000000000000

#9 - cp the avg_cov_len_fasta_advbioinf.py from the
 /cm/shared/courses/dbarshis/21AdvGenomics/scripts directory into your class scripts directory
[amali010@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py ../scripts/
cp: cannot create regular file `../scripts/': Is a directory
[amali010@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py ../../scripts/
[amali010@turing1 exercises]$ cd ..
[amali010@turing1 data]$ cd ..
[amali010@turing1 areej]$ ls
am_exercise1.txt  data  day03  groundrules.txt  scripts
[amali010@turing1 areej]$ cd scripts
[amali010@turing1 scripts]$ ls
avg_cov_len_fasta_advbioinf.py  Trimclipfilterstatsbatch_advbioinf.py
renamer_advbioinf.py

#10 - start an interactive compute session and re-navigate 
to your exercises directory
[amali010@turing1 exercises]$ salloc
salloc: Pending job allocation 9271058
salloc: job 9271058 queued and waiting for resources
salloc: job 9271058 has been allocated resources
salloc: Granted job allocation 9271058

#11 - run the avg_cov_len_fasta_DJB.py script on your 
Exercise2.fasta file by typing the path to the script followed 
by the Exercise2.fasta file name
[amali010@coreV2-22-007 exercises]$ ../../scripts/avg_cov_len_fasta_advbioinf.py Exercise2.fasta
The total number of sequences is 138
The average sequence length is 126640
The total number of bases is 17476447
The minimum sequence length is 1122
The maximum sequence length is 562680
The N50 is 187037
Median Length = 92612
contigs < 150bp = 0
contigs >= 500bp = 138
contigs >= 1000bp = 138
contigs >= 2000bp = 135

#12 - did you add all these entries to your notebook file, 
including the results of the script?
Yes!

#13 - push your notebook file to your github page
git add README.md
git commit -m 'updating readme'
git push -u origin main
```

##Day 03 27-Jan-2021
* Homework day02 (originally meant for 22-Jan-2021 but done on 27-Jan-2021)
```sh
#1 - write an sbatch script to cp the files /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/ into your own data directory
   Kristina-HADB01
   Ivan-HADB02
   KatieP-HADB03
   KatieC-HADB04
   Stephanie-HADB05
   Areej-HADB06
   Andrew-HADB01
   John-HADB02
   dan-All
   
[amali010@coreV2-25-072 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data

#2 - add the content of your sbatch script to your logfile
[amali010@coreV2-25-072 data]$ cat AMCopyLane06.sh
#!/bin/bash -l

#SBATCH -o AMCopyLane06.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMCopyLane06

cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/HADB06*.fastq.gz /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data

#3 - submit the slurm script (sbatch scripname.sh) and verify 
that it's working (by squeue -u yourusername multiple times and 
checking the destination directory to make sure the files are being created)
[amali010@coreV2-25-072 data]$ sbatch AMCopyLane06.sh
Submitted batch job 9270443

#4 - make sure this is all documented on your github notebook
Done

#5 - write a sbatch script to gunzip all the fastq.gz files
[amali010@coreV2-25-072 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data
[amali010@coreV2-25-072 data]$ cat AMGunzipLane06.sh
#!/bin/bash -l

#SBATCH -o AMGunzipLane06.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMGunzipLane06

gunzip *.fastq.gz

[amali010@coreV2-25-072 data]$ sbatch AMGunzipLane06.sh
Submitted batch job 9270466

#6 - push your notebook file to your github page
git add README.md
git commit -m 'updating readme'
git push -u origin main
```

##Day 03 27-Jan-2021
* Homework day03
```sh
[amali010@turing1 areej]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej

#1 - cp the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03 directory 
(and files) to your sandbox
[amali010@turing1 areej]$ cp -r /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03 ./

#2 - mkdir a fastq directory in your data directory and mv all the .fastq files into this directory
[amali010@turing1 areej]$ cd data
[amali010@turing1 data]$ mkdir fastq
[amali010@turing1 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data
[amali010@turing1 data]$ mv *.fastq ./fastq/

#3 - cp the renamingtable_complete.txt from the day03 directory into your fastq directory and 
the /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py script into your 
sandbox scripts folder and less the new script and check out the usage statement
[amali010@turing1 data]$ cp ../day03/renamingtable_complete.txt ./fastq/
[amali010@turing1 data]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py ../scripts/
[amali010@turing1 data]$ head ../scripts/renamer_advbioinf.py
#!/usr/bin/env python
####usage renamer.py renamingtable
#### this script take the entries in the first column of table and renames (mv's) them to files with the names in the second column

#4 - run the renamer_advbioinf.py script in your fastq folder using the renamingtable_complete.txt as 
practice and verify the output to the screen by hand
[amali010@turing1 data]$ cd fastq/
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ ../../scripts/renamer_advbioinf.py renamingtable_complete.txt
mv HADB01-A_S17_L002_R1_001.fastq VA_W_01_14.fastq
mv HADB01-B_S18_L002_R1_001.fastq VA_B_01_14.fastq
mv HADB01-C_S19_L002_R1_001.fastq RI_W_01_14.fastq
mv HADB01-D_S20_L002_R1_001.fastq RI_B_01_14.fastq
mv HADB01-E_S21_L002_R1_001.fastq VA_W_01_22.fastq
mv HADB01-F_S22_L002_R1_001.fastq VA_B_01_22.fastq
mv HADB01-G_S23_L002_R1_001.fastq RI_W_01_22.fastq
mv HADB01-H_S24_L002_R1_001.fastq RI_B_01_22.fastq
mv HADB01-I_S25_L002_R1_001.fastq VA_W_01_18.fastq
mv HADB01-J_S26_L002_R1_001.fastq VA_B_01_18.fastq
mv HADB01-K_S27_L002_R1_001.fastq RI_W_01_18.fastq
mv HADB01-L_S28_L002_R1_001.fastq RI_B_01_18.fastq
mv HADB01-M_S29_L002_R1_001.fastq VA_W_08_SNP.fastq
mv HADB01-N_S30_L002_R1_001.fastq VA_B_09_SNP.fastq
mv HADB01-O_S31_L002_R1_001.fastq RI_W_08_SNP.fastq
mv HADB01-P_S32_L002_R1_001.fastq RI_B_08_SNP.fastq
mv HADB02-A_S33_L003_R1_001.fastq VA_W_02_14.fastq
mv HADB02-B_S34_L003_R1_001.fastq VA_B_02_14.fastq
mv HADB02-C_S35_L003_R1_001.fastq RI_W_02_14.fastq
mv HADB02-D_S36_L003_R1_001.fastq RI_B_02_14.fastq
mv HADB02-E_S37_L003_R1_001.fastq VA_W_02_22.fastq
mv HADB02-F_S38_L003_R1_001.fastq VA_B_02_22.fastq
mv HADB02-G_S39_L003_R1_001.fastq RI_W_02_22.fastq
mv HADB02-H_S40_L003_R1_001.fastq RI_B_02_22.fastq
mv HADB02-I_S41_L003_R1_001.fastq VA_W_02_18.fastq
mv HADB02-J_S42_L003_R1_001.fastq VA_B_02_18.fastq
mv HADB02-K_S43_L003_R1_001.fastq RI_W_02_18.fastq
mv HADB02-L_S44_L003_R1_001.fastq RI_B_02_18.fastq
mv HADB02-M_S45_L003_R1_001.fastq VA_W_09_SNP.fastq
mv HADB02-N_S46_L003_R1_001.fastq VA_B_08_SNP.fastq
mv HADB02-O_S47_L003_R1_001.fastq RI_W_09_SNP.fastq
mv HADB02-P_S48_L003_R1_001.fastq RI_B_09_SNP.fastq
mv HADB03-A_S49_L004_R1_001.fastq VA_W_03_14.fastq
mv HADB03-B_S50_L004_R1_001.fastq VA_B_03_14.fastq
mv HADB03-C_S51_L004_R1_001.fastq RI_W_03_14.fastq
mv HADB03-D_S52_L004_R1_001.fastq RI_B_03_14.fastq
mv HADB03-E_S53_L004_R1_001.fastq VA_W_03_22.fastq
mv HADB03-F_S54_L004_R1_001.fastq VA_B_03_22.fastq
mv HADB03-G_S55_L004_R1_001.fastq RI_W_03_22.fastq
mv HADB03-H_S56_L004_R1_001.fastq RI_B_03_22.fastq
mv HADB03-I_S57_L004_R1_001.fastq VA_W_03_18.fastq
mv HADB03-J_S58_L004_R1_001.fastq VA_B_03_18.fastq
mv HADB03-K_S59_L004_R1_001.fastq RI_W_03_18.fastq
mv HADB03-L_S60_L004_R1_001.fastq RI_B_03_18.fastq
mv HADB03-M_S61_L004_R1_001.fastq VA_W_10_SNP.fastq
mv HADB03-N_S62_L004_R1_001.fastq VA_B_10_SNP.fastq
mv HADB03-O_S63_L004_R1_001.fastq RI_W_10_SNP.fastq
mv HADB03-P_S64_L004_R1_001.fastq RI_B_10_SNP.fastq
mv HADB04-A_S65_L005_R1_001.fastq VA_W_04_14.fastq
mv HADB04-B_S66_L005_R1_001.fastq VA_B_04_14.fastq
mv HADB04-C_S67_L005_R1_001.fastq RI_W_04_14.fastq
mv HADB04-D_S68_L005_R1_001.fastq RI_B_04_14.fastq
mv HADB04-E_S69_L005_R1_001.fastq VA_W_04_22.fastq
mv HADB04-F_S70_L005_R1_001.fastq VA_B_04_22.fastq
mv HADB04-G_S71_L005_R1_001.fastq RI_W_04_22.fastq
mv HADB04-H_S72_L005_R1_001.fastq RI_B_04_22.fastq
mv HADB04-I_S73_L005_R1_001.fastq VA_W_04_18.fastq
mv HADB04-J_S74_L005_R1_001.fastq VA_B_04_18.fastq
mv HADB04-K_S75_L005_R1_001.fastq RI_W_04_18.fastq
mv HADB04-L_S76_L005_R1_001.fastq RI_B_04_18.fastq
mv HADB04-M_S77_L005_R1_001.fastq VA_W_05_14.fastq
mv HADB04-N_S78_L005_R1_001.fastq VA_B_05_14.fastq
mv HADB04-O_S79_L005_R1_001.fastq RI_W_05_14.fastq
mv HADB04-P_S80_L005_R1_001.fastq RI_B_05_14.fastq
mv HADB05-A_S81_L006_R1_001.fastq VA_W_05_22.fastq
mv HADB05-B_S82_L006_R1_001.fastq VA_B_05_22.fastq
mv HADB05-C_S83_L006_R1_001.fastq RI_W_05_22.fastq
mv HADB05-D_S84_L006_R1_001.fastq RI_B_05_22.fastq
mv HADB05-E_S85_L006_R1_001.fastq VA_W_05_18.fastq
mv HADB05-F_S86_L006_R1_001.fastq VA_B_05_18.fastq
mv HADB05-G_S87_L006_R1_001.fastq RI_W_05_18.fastq
mv HADB05-H_S88_L006_R1_001.fastq RI_B_05_18.fastq
mv HADB05-I_S89_L006_R1_001.fastq VA_W_06_14.fastq
mv HADB05-J_S90_L006_R1_001.fastq VA_B_06_14.fastq
mv HADB05-K_S91_L006_R1_001.fastq RI_W_06_14.fastq
mv HADB05-L_S92_L006_R1_001.fastq RI_B_06_14.fastq
mv HADB05-M_S93_L006_R1_001.fastq VA_W_06_22.fastq
mv HADB05-N_S94_L006_R1_001.fastq VA_B_06_22.fastq
mv HADB05-O_S95_L006_R1_001.fastq RI_W_06_22.fastq
mv HADB05-P_S96_L006_R1_001.fastq RI_B_06_22.fastq
mv HADB06-A_S97_L007_R1_001.fastq VA_W_06_18.fastq
mv HADB06-B_S98_L007_R1_001.fastq VA_B_06_18.fastq
mv HADB06-C_S99_L007_R1_001.fastq RI_W_06_18.fastq
mv HADB06-D_S100_L007_R1_001.fastq RI_B_06_18.fastq
mv HADB06-E_S101_L007_R1_001.fastq VA_W_07_14.fastq
mv HADB06-F_S102_L007_R1_001.fastq VA_B_07_14.fastq
mv HADB06-G_S103_L007_R1_001.fastq RI_W_07_14.fastq
mv HADB06-H_S104_L007_R1_001.fastq RI_B_07_14.fastq
mv HADB06-I_S105_L007_R1_001.fastq VA_W_07_22.fastq
mv HADB06-J_S106_L007_R1_001.fastq VA_B_07_22.fastq
mv HADB06-K_S107_L007_R1_001.fastq RI_W_07_22.fastq
mv HADB06-L_S108_L007_R1_001.fastq RI_B_07_22.fastq
mv HADB06-M_S109_L007_R1_001.fastq VA_W_07_18.fastq
mv HADB06-N_S110_L007_R1_001.fastq VA_B_07_18.fastq
mv HADB06-O_S111_L007_R1_001.fastq RI_W_07_18.fastq
mv HADB06-P_S112_L007_R1_001.fastq RI_B_07_18.fastq

#5 - uncomment the last line of the renaming script in your scripts folder 
that starts with os.popen and comment out the next to last line that starts 
with print
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ nano ../../scripts/renamer_advbioinf.py

#6 - write a sbatch script and submit it to rename all the .fastq files 
according to the renaming table using 
your renamer_advbioinf.py script
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ nano areejsrenamer.sh
[amali010@turing1 fastq]$ cat areejsrenamer.sh
#!/bin/bash -l

#SBATCH -o areejsrenamer.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=FastqRename

../../scripts/renamer_advbioinf.py renamingtable_complete.txt

[amali010@turing1 fastq]$ sbatch ./areejsrenamer.sh
Submitted batch job 9270936
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)

#7 - make sure this is all documented on your github page
areej@DESKTOP-RF6VF4N MINGW64 ~/Desktop/BIOL_803_Advanced_Genomics_Data_Analysis/In_class/21sp_advgenomics/AreejsAdvancedGenomicsLog (main)
$ git add README.md

areej@DESKTOP-RF6VF4N MINGW64 ~/Desktop/BIOL_803_Advanced_Genomics_Data_Analysis/In_class/21sp_advgenomics/AreejsAdvancedGenomicsLog (main)
$ git commit -m 'updating readme'
[main 4326621] updating readme
 1 file changed, 20 insertions(+), 1 deletion(-)

areej@DESKTOP-RF6VF4N MINGW64 ~/Desktop/BIOL_803_Advanced_Genomics_Data_Analysis/In_class/21sp_advgenomics/AreejsAdvancedGenomicsLog (main)
$ git push -u origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 491 bytes | 245.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/areejmalik/AreejsAdvancedGenomicsLog.git
   aa0237a..4326621  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.

#8 - the naming convention for the files is as follows:
SOURCEPOPULATION_SYMBIOTICSTATE_GENOTYPE_TEMPERATURE.fastq
There are 2 sources: Virginia and Rhode Island
There are 2 symbiotic states: Brown and White
	
#9 - next, you're going to start the process of adapter clipping and quality 
trimming all the renamed .fastq files in batches, by lane
Ok!

#10 - cp the script /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Trimclipfilterstatsbatch_advbioinf.py into your scripts directory
[amali010@coreV1-22-016 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data
[amali010@coreV1-22-016 data]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/

#11 - less/head the new script and check out the usage statement
[amali010@coreV1-22-016 data]$ head -14 ../scripts/Trimclipfilterstatsbatch_advbioinf.py
#!/usr/bin/env python
# Written by Dan Barshis

import sys, os

########### Usage #############
# Trimclipfilterstatsbatch.py barcodefile.txt anynumberoffastqfiles
# This should be run from within the folder with all of your original .fastqstrim
# Will quality trim multiple SINGLE-END fastq files
# Things to customize for your particular platform:
# qualoffset = 33 Quality score offset
# -t option in qualitytrim (the lower threshold quality score for trimming)
# -l option in qualitytrim and adapterclip (the length threshold for throwing out short reads)

#12 - cp the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt 
into the working directory with your fastq files
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt ./

#13 - make a sbatch script for the Trimclipfilter... script and run it on your fastq files
[amali010@turing1 ~]$ salloc
salloc: Pending job allocation 9270954
salloc: job 9270954 queued and waiting for resources
salloc: job 9270954 has been allocated resources
salloc: Granted job allocation 9270954
NOTE: The job allocation number matches that of the one that is currently the only one running
[amali010@coreV1-22-005 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@coreV1-22-005 fastq]$ nano FullTrimClip.sh
[amali010@coreV1-22-005 fastq]$ cat FullTrimClip.sh
#!/bin/bash -l

#SBATCH -o AMFullTrimclip.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMTrimTest

../../../scripts/Trimclipfilterstatsbatch_advbioinf.py adapterlist_advbioinf.txt *.fastq

[amali010@coreV1-22-005 fastq]$ sbatch FullTrimClip.sh
Submitted batch job 9270961
[amali010@coreV1-22-005 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270961      main AMTrimTe amali010 PD       0:00      1 (Priority)
           9270954      main       sh amali010  R      18:11      1 coreV1-22-005
[amali010@coreV1-22-005 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270954      main       sh amali010  R      19:42      1 coreV1-22-005
NOTE: I don't know why it keeps failing the job partition I even tried logging 
out the core and remained on turing but that was rejected as well. :(

After multiple attempts!!
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ nano amFullTrimClip.sh
[amali010@turing1 fastq]$ cat amFullTrimClip.sh
#!/bin/bash -l

#SBATCH -o amFullTrimclip.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=amTrimFull

../../scripts/Trimclipfilterstatsbatch_advbioinf.py adapterlist_advbioinf.txt *.fastq
[amali010@turing1 fastq]$ sbatch amFullTrimClip.sh
Submitted batch job 9270966
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R       0:03      1 coreV1-22-005
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R       0:22      1 coreV1-22-005
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R       1:17      1 coreV1-22-005
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R       2:40      1 coreV1-22-005
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R       3:25      1 coreV1-22-005
[amali010@turing1 fastq]$ ls
adapterlist_advbioinf.txt   RI_B_06_18.fastq   VA_B_06_18.fastq
amFullTrimClip.sh           RI_B_07_14.fastq   VA_B_07_14.fastq
amFullTrimclip.txt          RI_B_07_18.fastq   VA_B_07_18.fastq
AMFullTrimclip.txt          RI_B_07_22.fastq   VA_B_07_22.fastq
areejsrenamer.sh            RI_W_06_18.fastq   VA_W_06_18.fastq
AreejsRenamer.sh            RI_W_07_14.fastq   VA_W_07_14.fastq
areejsrenamer.txt           RI_W_07_18.fastq   VA_W_07_18.fastq
FullTrimClip.sh             RI_W_07_22.fastq   VA_W_07_22.fastq
renamingtable_complete.txt  Testing
RI_B_06_18_clipped.fastq    trimclipstats.txt

Note: need to know how to safely delete the extra files that were made
while attempting to getting the script to run

[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R       5:20      1 coreV1-22-005
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R       9:01      1 coreV1-22-005
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9270966      main amTrimFu amali010  R      17:31      1 coreV1-22-005

#14 - push your notebook file to your github page
git add README.md
git commit -m 'updating readme'
git push -u origin main
```

##Day 04 29-Jan-2021
* Homework day04 
```sh
Checked the success of the job submission from the day before
[amali010@turing1 areej]$ cd data
[amali010@turing1 data]$ cd fastq
[amali010@turing1 fastq]$ ls
[amali010@turing1 fastq]$ ls filteringstats/
[amali010@turing1 fastq]$ ls -alh filteringstats/

#1 - add your trimclipstats.txt output to the full class 

#1a - run /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py -h 
to examine usage datafile /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt 
using the following steps
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py -h
Written by Peter Schafran pscha005@odu.edu 5-Oct-2015

This script takes a stats output file from fastx_clipper and converts it into a table.

Usage: Schafran_trimstatstable.py [-c, -v, -h] inputfile.txt outputfile.txt

Options (-c and -v must be listed separately to run together):
-h      Display this help message
-c      Use comma delimiter instead of tabs
-v      Verbose mode (print steps to stdout)

#1b - run the script on your data with the outputfilename YOURNAME_trimclipstatsout.txt
[amali010@turing1 fastq]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py trimclipstats.txt AREEJ_trimclipstatsout.txt

#1c -  add YOURNAME_trimclipstatsout.txt to the class file by running tail -n +2 YOURNAME_trimclipstatsout.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt
[amali010@turing1 fastq]$ tail -n +2 AREEJ_trimclipstatsout.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt

#2 - now we're going to map our reads back to our assembly using the bowtie2 alignment algorithm (starting to follow this pipeline https://github.com/bethsheets/SNPcalling_tutorial)
Ok!

#3 - write a sbatch script to do the following commands in sequence on 
your _clippedtrimmedfilterd.fastq datafiles from your lane of data
[amali010@turing1 fastq]$ cd QCFastqs
[amali010@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/QCFastqs
[amali010@turing1 QCFastqs]$ nano ajbowtie2.sh
[amali010@turing1 QCFastqs]$ ls
ajbowtie2.sh                     VA_B_06_18_clippedtrimmed.fastq
RI_B_06_18_clippedtrimmed.fastq  VA_B_07_14_clippedtrimmed.fastq
RI_B_07_14_clippedtrimmed.fastq  VA_B_07_18_clippedtrimmed.fastq
RI_B_07_18_clippedtrimmed.fastq  VA_B_07_22_clippedtrimmed.fastq
RI_B_07_22_clippedtrimmed.fastq  VA_W_06_18_clippedtrimmed.fastq
RI_W_06_18_clippedtrimmed.fastq  VA_W_07_14_clippedtrimmed.fastq
RI_W_07_14_clippedtrimmed.fastq  VA_W_07_18_clippedtrimmed.fastq
RI_W_07_18_clippedtrimmed.fastq  VA_W_07_22_clippedtrimmed.fastq
RI_W_07_22_clippedtrimmed.fastq
[amali010@turing1 QCFastqs]$ cat ajbowtie2.sh
#!/bin/bash -l

#SBATCH -o ambowtie2.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=ambowtie

module load bowtie2/2.4
for i in *_clippedtrimmed.fastq; do bowtie2 --rg-id ${i%_clippedtrimmed.fastq} \
--rg SM:${i%_clippedtrimmed.fastq} \
--very-sensitive -x /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/Apoc_hostsym -U $i \
> ${i%_clippedtrimmedfilterd.fastq}.sam --no-unal -k 5; done

[amali010@turing1 QCFastqs]$ sbatch ajbowtie2.sh
Submitted batch job 9271117
[amali010@turing1 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9271117      main ambowtie amali010 PD       0:00      1 (Priority)
  [amali010@turing1 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9271117      main ambowtie amali010  R       1:49      1 coreV2-25-049
[amali010@turing1 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9271117      main ambowtie amali010  R       5:07      1 coreV2-25-049

#4 - submit and add everything to your logfile
git add README.md
git commit -m 'updating readme'
git push -u origin main
```

##Day 05 03-Feb-2021
* Exercise day05 
```sh
#1 - team up with a partner for this one and work only on a combined set of 
data for your two lanes of sequences
Partner: Andrew
Combined set of data lanes: 1, 6, & 7

#2 - run the Trinity denovo assembler on your clippedtrimmed.fastq files for 
your two lanes together
Done!

#3 - modify the below sbatch script (note the differences in the header 
compared to the previous one)
Original script (used from homework_day05.txt file)

Edited script
New name: APAMAssemble.sh
Location: /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/apearson/data/fastq/QCFastqs/apam/
#!/bin/bash -l

#SBATCH -o APAMAssemble.txt
#SBATCH -n 32
#SBATCH -p himem
#SBATCH --mail-user=pearsoac@evms.edu
#SBATCH --mail-type=END
#SBATCH --job-name=APAMAssemble

enable_lmod
module load container_env trinity

crun Trinity --seqType fq --max_memory 768G --normalize_reads --single RI_B_01_14_clippedtrimmed.fastq,RI_W_06_18_clippedtrimmed.fastq,VA_B_07_22_clippedtrimmed.fastq,RI_B_01_18_clippedtrimmed.fastq,RI_W_07_14_clippedtrimmed.fastq,VA_B_09_SNP_clippedtrimmed.fastq,RI_B_01_22_clippedtrimmed.fastq,RI_W_07_18_clippedtrimmed.fastq,VA_W_01_14_clippedtrimmed.fastq,RI_B_06_18_clippedtrimmed.fastq,RI_W_07_22_clippedtrimmed.fastq,VA_W_01_18_clippedtrimmed.fastq,RI_B_07_14_clippedtrimmed.fastq,RI_W_08_SNP_clippedtrimmed.fastq,VA_W_01_22_clippedtrimmed.fastq,RI_B_07_18_clippedtrimmed.fastq,VA_B_01_14_clippedtrimmed.fastq,VA_W_06_18_clippedtrimmed.fastq,RI_B_07_22_clippedtrimmed.fastq,VA_B_01_18_clippedtrimmed.fastq,VA_W_07_14_clippedtrimmed.fastq,RI_B_08_SNP_clippedtrimmed.fastq,VA_B_01_22_clippedtrimmed.fastq,VA_W_07_18_clippedtrimmed.fastq,RI_W_01_14_clippedtrimmed.fastq,VA_B_06_18_clippedtrimmed.fastq,VA_W_07_22_clippedtrimmed.fastq,RI_W_01_18_clippedtrimmed.fastq,VA_B_07_14_clippedtrimmed.fastq,VA_W_08_SNP_clippedtrimmed.fastq,RI_W_01_22_clippedtrimmed.fastq,VA_B_07_18_clippedtrimmed.fastq --CPU 32

#4 - check https://trinityrnaseq.github.io/ for usage info
Done!

#5 - submit your trinity script
Note: It was done by Andrew, so the following is from his notebook.
[apear012@turing1 apam]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/apearson/data/fastq/QCFastqs/apam
[apear012@coreV2-22-007 apam]$ sbatch APAMAssemble.sh 
Submitted batch job 9272358

[amali010@turing1 apam]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
[amali010@turing1 apam]$ squeue -u apear012
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9272358     himem APAMAsse apear012 PD       0:00      1 (Resources)
           9272334      main       sh apear012  R    1:19:50      1 coreV2-25-002
           9272357      main       sh apear012  R       6:49      1 coreV2-22-007
[amali010@turing1 apam]$ squeue -u apear012
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9272358     himem APAMAsse apear012 PD       0:00      1 (Resources)
           9272334      main       sh apear012  R    1:20:18      1 coreV2-25-002
           9272357      main       sh apear012  R       7:17      1 coreV2-22-007
Note: Job failed after approximately 15 minutes :(

Edited APAMAssemble.sh file (removed --normalize_reads). This was also done by Andrew.
#!/bin/bash -l

#SBATCH -o APAMAssemble.txt
#SBATCH -n 32
#SBATCH -p himem
#SBATCH --mail-user=pearsoac@evms.edu
#SBATCH --mail-type=END
#SBATCH --job-name=APAMAssemble

enable_lmod
module load container_env trinity

crun Trinity --seqType fq --max_memory 768G --single RI_B_01_14_clippedtrimmed.fastq,RI_W_06_18_clippedtrimmed.fastq,VA_B_07_22_clippedtrimmed.fastq,RI_B_01_18_clippedtrimmed.fastq,RI_W_07_14_clippedtrimmed.fastq,VA_B_09_SNP_clippedtrimmed.fastq,RI_B_01_22_clippedtrimmed.fastq,RI_W_07_18_clippedtrimmed.fastq,VA_W_01_14_clippedtrimmed.fastq,RI_B_06_18_clippedtrimmed.fastq,RI_W_07_22_clippedtrimmed.fastq,VA_W_01_18_clippedtrimmed.fastq,RI_B_07_14_clippedtrimmed.fastq,RI_W_08_SNP_clippedtrimmed.fastq,VA_W_01_22_clippedtrimmed.fastq,RI_B_07_18_clippedtrimmed.fastq,VA_B_01_14_clippedtrimmed.fastq,VA_W_06_18_clippedtrimmed.fastq,RI_B_07_22_clippedtrimmed.fastq,VA_B_01_18_clippedtrimmed.fastq,VA_W_07_14_clippedtrimmed.fastq,RI_B_08_SNP_clippedtrimmed.fastq,VA_B_01_22_clippedtrimmed.fastq,VA_W_07_18_clippedtrimmed.fastq,RI_W_01_14_clippedtrimmed.fastq,VA_B_06_18_clippedtrimmed.fastq,VA_W_07_22_clippedtrimmed.fastq,RI_W_01_18_clippedtrimmed.fastq,VA_B_07_14_clippedtrimmed.fastq,VA_W_08_SNP_clippedtrimmed.fastq,RI_W_01_22_clippedtrimmed.fastq,VA_B_07_18_clippedtrimmed.fastq --CPU 32

[apear012@turing1 apam]$ sbatch APAMAssemble.sh
Submitted batch job 9272385
[apear012@turing1 apam]$ squeue -u apear012
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON) 
           9272357      main       sh apear012  R    1:15:39      1 coreV2-22-007 
           9272385     himem APAMAsse apear012  R       0:14      1 coreV4-21-himem-003
           
#6 - submit and add everything to your logfile
git add README.md
git commit -m 'updating readme'
git push -u origin main
```
##Day 05 03-Feb-2021
```sh
No homework
```
##Day 06 05-Feb-2021
*  Exercise day06 
```sh
#1 - start an interactive session via salloc and run 
the /cm/shared/apps/trinity/2.0.6/util/TrinityStats.pl script on your 
Trinity.fasta output from your assembly
[amali010@turing1 djbtestassembly]$ salloc
salloc: Pending job allocation 9272860
salloc: job 9272860 queued and waiting for resources
salloc: job 9272860 has been allocated resources
salloc: Granted job allocation 9272860

[amali010@turing1 djbtestassembly]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/djbtestassembly
[amali010@coreV2-22-007 djbtestassembly]$ /cm/shared/apps/trinity/2.0.6/util/TrinityStats.pl Trinity.fasta


################################
## Counts of transcripts, etc.
################################
Total trinity 'genes':  20980
Total trinity transcripts:      21992
Percent GC: 46.21

########################################
Stats based on ALL transcript contigs:
########################################

        Contig N10: 1178
        Contig N20: 694
        Contig N30: 514
        Contig N40: 414
        Contig N50: 347

        Median contig length: 273
        Average contig: 356.95
        Total assembled bases: 7850006


#####################################################
## Stats based on ONLY LONGEST ISOFORM per 'GENE':
#####################################################

        Contig N10: 1027
        Contig N20: 643
        Contig N30: 486
        Contig N40: 397
        Contig N50: 336

        Median contig length: 271
        Average contig: 347.72
        Total assembled bases: 7295061

#2 - compare this with the output from avg_cov_len_fasta_advbioinf.py on 
our class reference assembly (/cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta) 
and add both to your logfile
[amali010@coreV2-22-007 djbtestassembly]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta
The total number of sequences is 15079
The average sequence length is 876
The total number of bases is 13210470
The minimum sequence length is 500
The maximum sequence length is 10795
The N50 is 881
Median Length = 578
contigs < 150bp = 0
contigs >= 500bp = 15079
contigs >= 1000bp = 3660
contigs >= 2000bp = 536

#3 - less or head your bowtie2 job output file to look at your alignment 
statistics and calculate the following from the information:

#3a - the mean percent "overall alignment rate"
[amali010@coreV2-22-007 QCFastqs]$ less ambowtie2.txt
[amali010@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/QCFastqs
[amali010@coreV2-22-007 QCFastqs]$ grep "overall alignment rate" ambowtie2.txt
1.87% overall alignment rate
1.53% overall alignment rate
1.46% overall alignment rate
1.92% overall alignment rate
1.65% overall alignment rate
1.48% overall alignment rate
1.25% overall alignment rate
1.60% overall alignment rate
1.94% overall alignment rate
2.00% overall alignment rate
1.67% overall alignment rate
2.09% overall alignment rate
1.62% overall alignment rate
1.54% overall alignment rate
1.70% overall alignment rate
1.41% overall alignment rate

[amali010@coreV2-22-007 QCFastqs]$ grep "overall alignment rate" ambowtie2.txt | cut -d "%" -f 1
1.87
1.53
1.46
1.92
1.65
1.48
1.25
1.60
1.94
2.00
1.67
2.09
1.62
1.54
1.70
1.41

#3b - the mean percent reads "aligned exactly 1 time"
[amali010@coreV2-22-007 QCFastqs]$ grep "aligned exactly 1 time" ambowtie2.txt
    312173 (1.32%) aligned exactly 1 time
    279609 (1.10%) aligned exactly 1 time
    226384 (0.96%) aligned exactly 1 time
    29903 (1.24%) aligned exactly 1 time
    210196 (1.09%) aligned exactly 1 time
    359056 (0.96%) aligned exactly 1 time
    225886 (0.88%) aligned exactly 1 time
    183780 (1.06%) aligned exactly 1 time
    207948 (1.27%) aligned exactly 1 time
    228135 (1.33%) aligned exactly 1 time
    250518 (1.09%) aligned exactly 1 time
    195159 (1.31%) aligned exactly 1 time
    195302 (1.13%) aligned exactly 1 time
    234155 (1.07%) aligned exactly 1 time
    176134 (0.87%) aligned exactly 1 time
    243143 (0.89%) aligned exactly 1 time

[amali010@coreV2-22-007 QCFastqs]$ grep "aligned exactly 1 time" ambowtie2.txt | cut -d "%" -f 1 | cut -d "(" -f 2
1.32
1.10
0.96
1.24
1.09
0.96
0.88
1.06
1.27
1.33
1.09
1.31
1.13
1.07
0.87
0.89

#3c - the mean number of reads "aligned exactly 1 time"
[amali010@turing1 QCFastqs]$ grep "aligned exactly 1 time" ambowtie2.txt
    312173 (1.32%) aligned exactly 1 time
    279609 (1.10%) aligned exactly 1 time
    226384 (0.96%) aligned exactly 1 time
    29903 (1.24%) aligned exactly 1 time
    210196 (1.09%) aligned exactly 1 time
    359056 (0.96%) aligned exactly 1 time
    225886 (0.88%) aligned exactly 1 time
    183780 (1.06%) aligned exactly 1 time
    207948 (1.27%) aligned exactly 1 time
    228135 (1.33%) aligned exactly 1 time
    250518 (1.09%) aligned exactly 1 time
    195159 (1.31%) aligned exactly 1 time
    195302 (1.13%) aligned exactly 1 time
    234155 (1.07%) aligned exactly 1 time
    176134 (0.87%) aligned exactly 1 time
    243143 (0.89%) aligned exactly 1 time
    
    [amali010@coreV2-22-007 QCFastqs]$ grep "aligned exactly 1 time" ambowtie2.txt | cut -d " " -f 5
312173
279609
226384
29903
210196
359056
225886
183780
207948
228135
250518
195159
195302
234155
176134
243143

#3d - the mean percent reads "aligned >1 times"
[amali010@coreV2-22-007 QCFastqs]$ grep "aligned >1 times" ambowtie2.txt
    131960 (0.56%) aligned >1 times
    109989 (0.43%) aligned >1 times
    119408 (0.50%) aligned >1 times
    16432 (0.68%) aligned >1 times
    107800 (0.56%) aligned >1 times
    194361 (0.52%) aligned >1 times
    95504 (0.37%) aligned >1 times
    93466 (0.54%) aligned >1 times
    110827 (0.68%) aligned >1 times
    115424 (0.67%) aligned >1 times
    131960 (0.58%) aligned >1 times
    116526 (0.78%) aligned >1 times
    83427 (0.48%) aligned >1 times
    103215 (0.47%) aligned >1 times
    169138 (0.83%) aligned >1 times
    140557 (0.52%) aligned >1 times

[amali010@coreV2-22-007 QCFastqs]$ grep "aligned >1 times" ambowtie2.txt | cut -d "%" -f 1 | cut -d "(" -f 2
0.56
0.43
0.50
0.68
0.56
0.52
0.37
0.54
0.68
0.67
0.58
0.78
0.48
0.47
0.83
0.52
hint use grep and paste into excel

#4 - add your statistics as single rows to the shared table 
/cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/alignmentstatstable.txt as tab-delimited text 
in the following order:
LaneX_yourinitials	b-the mean percent "overall alignment rate"	c-the mean percent reads "aligned exactly 1 time"	d-the mean number of reads "aligned exactly 1 time"	e-the mean percent reads "aligned >1 times"
[amali010@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/QCFastqs
[amali010@coreV2-22-007 QCFastqs]$ nano alignstatsam.txt
[amali010@coreV2-22-007 QCFastqs]$ cat alignstatsam.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/alignmentstatstable.txt
[amali010@coreV2-22-007 QCFastqs]$ tail -f /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/alignmentstatstable.txt
LaneX   overallalignmentrate    percsinglyaligned       numsinglyaligned        percmultiplyaligned
LaneX_djb       2.495714286     1.251428571     247656.7143     1.247142857
LaneX_djb       2.495714286     1.251428571     247656.7143     1.247142857
Lane1AP 5.378125        1.3725  300361.8125     4.005
lane5_sg        2.03%   1.11%   235455.75       0.92%
LaneX_jcw       2.495714286     1.251428571     247656.7143     1.247142857
Lane4_KCrid     2.48    1.30    289072.88       1.18
LaneX_am 1.670625       1.098125        222342.5625     0.573125

#5 - Data cleanup and archiving:
#5a - mv your Trinity.fast file from your trinity_out_dir to a folder 
called testassembly in your data directory
Note: our job was still running at the time. So to avoid confusion I decided to
work with the Trinity.fasta file that was copied into my data directory during class.
[amali010@turing1 data]$ mkdir testassembly
[amali010@turing1 data]$ cd djbtestassembly/
[amali010@turing1 djbtestassembly]$ ls
Trinity.fasta
[amali010@turing1 djbtestassembly]$ mv Trinity.fasta /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/testassembly/
[amali010@turing1 testassembly]$ ls
Trinity.fasta

#5b - set up a sbatch script to:
	rm -r YOURtrinity_out_dir (don't have one so this will be skipped in the sbatch script)
	rm -r YOURoriginalfastqs
	rm -r YOURfilterstats # as long as you've already appended your filteringstats output to the class as part of homework_day04.txt
original script (used from homework_ day06.txt file)
#!/bin/bash -l

#SBATCH -o OUTFILENAME.txt
#SBATCH -n NUMTHREADS(1 if not multi-threaded)
#SBATCH --mail-user=YOUREMAIL@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=JOBNAME

rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/dan/data/fastq/QCFastqs/21sampleassembly_trinity_out_dir
rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/dan/data/fastq/originalfastqs
rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/dan/data/fastq/filteringstats

[amali010@turing1 originalfastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/originalfastqs

[amali010@turing1 filteringstats]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/filteringstats

[amali010@turing1 fastq]$ nano AMCleanup.sh
[amali010@turing1 fastq]$ head AMCleanup.sh
#!/bin/bash -l

#SBATCH -o AMCleanup.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMCleanup

rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/originalfastqs
rm -r /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/filteringstats

[amali010@turing1 fastq]$ sbatch AMCleanup.sh
Submitted batch job 9273090
[amali010@turing1 fastq]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9273090      main AMCleanu amali010  R       0:01      1 coreV2-22-007

#6 - submit a blast against sprot from your testassembly folder using the following command
#!/bin/bash -l

#SBATCH -o OUTFILENAME.txt
#SBATCH -n 6         
#SBATCH --mail-user=EMAIL
#SBATCH --mail-type=END
#SBATCH --job-name=JOBNAME

enable_lmod
module load container_env blast
blastx -query Trinity.fasta -db /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018 -out blastx.outfmt6 \
        -evalue 1e-20 -num_threads 6 -max_target_seqs 1 -outfmt 6

[amali010@turing1 testassembly]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/testassembly
[amali010@turing1 testassembly]$ nano AMBlast.sh
[amali010@turing1 testassembly]$ cat AMBlast.sh
#!/bin/bash -l

#SBATCH -o AMBlast.txt
#SBATCH -n 6
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMBlast

enable_lmod
module load container_env blast
blastx -query Trinity.fasta -db /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018 -out blastx.outfmt6 \
        -evalue 1e-20 -num_threads 6 -max_target_seqs 1 -outfmt 6
[amali010@turing1 testassembly]$ sbatch AMBlast.sh
Submitted batch job 9273094
[amali010@turing1 testassembly]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9273094      main  AMBlast amali010  R       0:03      1 coreV2-22-028
[amali010@turing1 areej]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9273094      main  AMBlast amali010  R      58:38      1 coreV2-22-028

#7 - head one of your .sam files to look at the header
[amali010@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/QCFastqs
[amali010@turing1 QCFastqs]$ head RI_B_06_18_clippedtrimmed.fastq.sam
@HD     VN:1.0  SO:unsorted
@SQ     SN:TR78|c0_g1_i1_coral  LN:1109
@SQ     SN:TR78|c0_g2_i1_coral  LN:1109
@SQ     SN:TR79|c0_g1_i1_coral  LN:610
@SQ     SN:TR79|c0_g2_i1_coral  LN:1549
@SQ     SN:TR87|c0_g1_i1_coral  LN:732
@SQ     SN:TR93|c0_g1_i1_coral  LN:550
@SQ     SN:TR101|c0_g1_i1_coral LN:673
@SQ     SN:TR104|c0_g1_i1_coral LN:607
@SQ     SN:TR105|c0_g1_i1_coral LN:587

#8 - grep -v '@' your.sam | head to look at the sequence read lines, 
why does this work to exclude the header lines?
[amali010@turing1 QCFastqs]$ grep -v "@" RI_B_06_18_clippedtrimmed.fastq.sam | head
K00188:59:HMTFHBBXX:7:1101:12845:1666   16      TR13647|c0_g1_i1_coral  40      255
51M     *       0       0       TTTGGATTCTTGATCACGGTATGATCGATAAAACACAGACCTGTAAAGTCC
JJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFFFAA     AS:i:0  XN:i:0  XM:i:0  XO:i:0      XG:i:0  NM:i:0  MD:Z:51 YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:17645:1683   16      TR43786|c0_g1_i16_coral 125     1  51M      *       0       0       AAGAGTACTAAATGGTAACCAGCGAGTCCGTGTAGAAGTATTTTGTAGGTC
JJJJJJJJJFJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFFFAA     AS:i:0  XS:i:0  XN:i:0  XM:i:0      XO:i:0  XG:i:0  NM:i:0  MD:Z:51 YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:17645:1683   272     TR43786|c0_g1_i5_coral  151     255
51M     *       0       0       AAGAGTACTAAATGGTAACCAGCGAGTCCGTGTAGAAGTATTTTGTAGGTC
JJJJJJJJJFJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFFFAA     AS:i:0  XS:i:0  XN:i:0  XM:i:0      XO:i:0  XG:i:0  NM:i:0  MD:Z:51 YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:20750:1683   0       TR24696|c0_g1_i2_coral  329     1  51M      *       0       0       CCCCACTACCAGAAATTATACGCTCGAGTTACCCACATTTGGGGTAATCGC
AAFFFJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFJJJJJJ     AS:i:0  XS:i:0  XN:i:0  XM:i:0      XO:i:0  XG:i:0  NM:i:0  MD:Z:51 YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:20750:1683   256     TR24696|c0_g1_i3_coral  329     255
51M     *       0       0       CCCCACTACCAGAAATTATACGCTCGAGTTACCCACATTTGGGGTAATCGC
AAFFFJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFJJJJJJ     AS:i:0  XS:i:0  XN:i:0  XM:i:0      XO:i:0  XG:i:0  NM:i:0  MD:Z:51 YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:22658:1683   16      TR43764|c4_g1_i1_coral  1687    255
51M     *       0       0       TCCATTCCTAATCCGTCTGTTAGTGGTCTGCAGTTCCACGCCGTCTTTTCG
JJJJJJJFJJFJJJJJJJJJJJJJJJJJJJJJJJJJJFJJJJJJFJFFAAA     AS:i:-17        XN:i:0  XM:i:3      XO:i:0  XG:i:0  NM:i:3  MD:Z:25T7C14G2  YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:27854:1683   16      TR29978|c0_g2_i1_coral  10      255
51M     *       0       0       GGAATCCTTGTTAGTTTCTTTTCCTCCGCTTATTAATATGCTTAAATTCAG
JJJJFJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFFFAA     AS:i:-28        XN:i:0  XM:i:5      XO:i:0  XG:i:0  NM:i:5  MD:Z:30G1C12G1C0A2      YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:2392:1701    0       TR35685|c1_g2_i1_coral  534     255
21M     *       0       0       TGACAACCCCGTCTGTGGCGC   AAFFFFJJJJJFFJJJJJFFJ   AS:i:-6     XN:i:0  XM:i:1  XO:i:0  XG:i:0  NM:i:1  MD:Z:7A13       YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:19705:1701   16      TR29978|c0_g2_i1_coral  14      255
51M     *       0       0       TCCTTGTTAGTTTCTTTTCCTCCGCTTATTAATATGCTTAAATTCAGCGGG
JJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFFFAA     AS:i:-30        XN:i:0  XM:i:5      XO:i:0  XG:i:0  NM:i:5  MD:Z:26G1C12G1C0A6      YT:Z:UU RG:Z:RI_B_06_18
K00188:59:HMTFHBBXX:7:1101:23094:1701   16      TR29978|c0_g2_i1_coral  5       255
51M     *       0       0       CTGGGGGAATCCTTGTTAGTTTCTTTTCCTCCGCTTATTAATATGCTTAAA
JJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFFFAA     AS:i:-29        XN:i:0  XM:i:5      XO:i:0  XG:i:0  NM:i:5  MD:Z:2A0A31G1C12G0      YT:Z:UU RG:Z:RI_B_06_18

Header lines include '@'. The -v in grep -v excludes '@' and therefore the header lines as well.

#9 - in an interactive session run /cm/shared/courses/dbarshis/21AdvGenomics/scripts/get_explain_sam_flags_advbioinf.py on 2-3 of your .sam files using * to select 2-3 at the same time.
[amali010@turing1 QCFastqs]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/get_explain_sam_flags_advbioinf.py RI_B_06_18_clippedtrimmed.fastq.sam RI_B_07_18_clippedtrimmed.fastq.sam RI_W_07_18_clippedtrimmed.fastq.sam
RI_B_06_18_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
        read reverse strand
        not primary alignment
256 :
        not primary alignment
16 :
        read reverse strand
RI_B_07_18_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
        read reverse strand
        not primary alignment
256 :
        not primary alignment
16 :
        read reverse strand
RI_W_07_18_clippedtrimmed.fastq.sam
['0', '272', '256', '16']
0 :
272 :
        read reverse strand
        not primary alignment
256 :
        not primary alignment
16 :
        read reverse strand

#10 - we need to run the read sorting step required for SNP calling, 
so if you have time, set up and run the following script on your .sam files to finish before Wednesday
#!/bin/bash -l

#SBATCH -o OUTFILENAME.txt
#SBATCH -n 1         
#SBATCH --mail-user=EMAIL
#SBATCH --mail-type=END
#SBATCH --job-name=JOBNAME

enable_lmod
module load samtools/1
for i in *.sam; do `samtools view -bS $i > ${i%.sam}_UNSORTED.bam`; done

for i in *UNSORTED.bam; do samtools sort $i > ${i%_UNSORTED.bam}.bam
samtools index ${i%_UNSORTED.bam}.bam
done

[amali010@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/QCFastqs
[amali010@turing1 QCFastqs]$ nano AMReadSort.sh
[amali010@turing1 QCFastqs]$ cat AMReadSort.sh
#!/bin/bash -l

#SBATCH -o AMReadSort.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMReadSort

enable_lmod
module load samtools/1
for i in *.sam; do `samtools view -bS $i > ${i%.sam}_UNSORTED.bam`; done

for i in *UNSORTED.bam; do samtools sort $i > ${i%_UNSORTED.bam}.bam
samtools index ${i%_UNSORTED.bam}.bam

done

[amali010@turing1 QCFastqs]$ sbatch AMReadSort.sh
Submitted batch job 9273103
[amali010@turing1 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9273094      main  AMBlast amali010  R    1:21:32      1 coreV2-22-028
           9273103      main AMReadSo amali010  R       0:04      1 coreV3-23-020
[amali010@turing1 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9273094      main  AMBlast amali010  R    1:22:36      1 coreV2-22-028
           9273103      main AMReadSo amali010  R       1:08      1 coreV3-23-020
[amali010@turing1 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9273094      main  AMBlast amali010  R    1:25:19      1 coreV2-22-028

#11 - submit and add everything to your logfile
git add README.md
git commit -m 'updating readme'
git push -u origin main
```

##Day 07 10-Feb-2021
*  Exercise day07 
```sh
#1 - run the following command on your sprot output file to process into the contig length/match format that trinity examines
#!/bin/bash -l

#SBATCH -o OUTFILE.TXT
#SBATCH -n 1
#SBATCH --mail-user=YOUREMAIL.odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=JOBNAME

/cm/shared/apps/trinity/2.0.6/util/analyze_blastPlus_topHit_coverage.pl blastx.outfmt6 Trinity.fasta /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018.fasta

[amali010@turing1 testassembly]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/testassembly
[amali010@turing1 testassembly]$ cat AMBlastparse.sh
#!/bin/bash -l

#SBATCH -o AMBlastparse.TXT
#SBATCH -n 1
#SBATCH --mail-user=amali010.odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMBlastparse

/cm/shared/apps/trinity/2.0.6/util/analyze_blastPlus_topHit_coverage.pl blastx.outfmt6 Trinity.fasta /cm/shared/apps/blast/databases/uniprot_sprot_Sep2018.fasta
[amali010@turing1 testassembly]$ sbatch AMBlastparse.sh
Submitted batch job 9276474
[amali010@turing1 testassembly]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9276474      main AMBlastp amali010 PD       0:00      1 (Priority)
[amali010@turing1 testassembly]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9276474      main AMBlastp amali010  R       0:14      1 coreV3-23-040

[amali010@turing1 testassembly]$ cat blastx.outfmt6.hist
#hit_pct_cov_bin        count_in_bin    >bin_below
100     143     143
90      52      195
80      77      272
70      87      359
60      110     469
50      133     602
40      219     821
30      395     1216
20      726     1942
10      674     2616

#2 - rm UNSORTED.bam's from your QCFastqs directory (or wherever your .bams and .sams are)
[amali010@turing1 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/QCFastqs
[amali010@turing1 QCFastqs]$ cat AMrmunsortbam.sh
#!/bin/bash -l

#SBATCH -o AMrmunsortbam.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMrmunsortbam

rm *UNSORTED.bam
[amali010@turing1 QCFastqs]$ sbatch AMrmunsortbam.sh
Submitted batch job 9276485
[amali010@turing1 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9276485      main AMrmunso amali010  R       0:01      1 coreV3-23-046

#2a - look at one of your files using sam tools
[amali010@turing1 QCFastqs]$ salloc
salloc: Pending job allocation 9276494
[amali010@coreV3-23-031 QCFastqs]$ enable_lmod
[amali010@coreV3-23-031 QCFastqs]$ module load samtools
[amali010@coreV3-23-031 QCFastqs]$ samtools tview RI_W_07_14_clippedtrimmed.fastq.bam /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta
1         11        21        31        41        51        61        71
TCAGGACCAAGTCCACTCATGATCGGAAGAGAAAACTTCTTTTTGGGATCGAATGGCCGGGCTCCAGACTTAGATATTAT
                                                        ........................
                                                        ........................

[amali010@coreV3-23-031 QCFastqs]$ samtools tview -p 'TR78|c0_g2_i1_coral' RI_W_07_14_clippedtrimmed.fastq.bam /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta
1         11        21        31        41        51        61        71
TCAGGACCAAGTCCACTCATGATCGGAAGAGAAAACTTCTTTTTGGGATCGAATGGCCGGGCTCCAGACTTAGATATTAT
                                                        ........................
                                                        ........................

#3 - run the following to start genotyping your SNPs for filtering next week
[amali010@coreV3-23-031 QCFastqs]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq/QCFastqs
[amali010@coreV3-23-031 QCFastqs]$ cat AMfreebayessubref.sh
#!/bin/bash -l

#SBATCH -o AMfreebayessubref.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMfreebayessubref

enable_lmod
module load dDocent
freebayes --genotype-qualities -f /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/refassembly/15079_Apoc_hostsym.fasta *.fastq.bam > AMmergedfastqs.vcf
[amali010@coreV3-23-031 QCFastqs]$ ls *.fastq.bam
RI_B_06_18_clippedtrimmed.fastq.bam  VA_B_06_18_clippedtrimmed.fastq.bam
RI_B_07_14_clippedtrimmed.fastq.bam  VA_B_07_14_clippedtrimmed.fastq.bam
RI_B_07_18_clippedtrimmed.fastq.bam  VA_B_07_18_clippedtrimmed.fastq.bam
RI_B_07_22_clippedtrimmed.fastq.bam  VA_B_07_22_clippedtrimmed.fastq.bam
RI_W_06_18_clippedtrimmed.fastq.bam  VA_W_06_18_clippedtrimmed.fastq.bam
RI_W_07_14_clippedtrimmed.fastq.bam  VA_W_07_14_clippedtrimmed.fastq.bam
RI_W_07_18_clippedtrimmed.fastq.bam  VA_W_07_18_clippedtrimmed.fastq.bam
RI_W_07_22_clippedtrimmed.fastq.bam  VA_W_07_22_clippedtrimmed.fastq.bam
[amali010@coreV3-23-031 QCFastqs]$ ls *.bam
RI_B_06_18_clippedtrimmed.fastq.bam  VA_B_06_18_clippedtrimmed.fastq.bam
RI_B_07_14_clippedtrimmed.fastq.bam  VA_B_07_14_clippedtrimmed.fastq.bam
RI_B_07_18_clippedtrimmed.fastq.bam  VA_B_07_18_clippedtrimmed.fastq.bam
RI_B_07_22_clippedtrimmed.fastq.bam  VA_B_07_22_clippedtrimmed.fastq.bam
RI_W_06_18_clippedtrimmed.fastq.bam  VA_W_06_18_clippedtrimmed.fastq.bam
RI_W_07_14_clippedtrimmed.fastq.bam  VA_W_07_14_clippedtrimmed.fastq.bam
RI_W_07_18_clippedtrimmed.fastq.bam  VA_W_07_18_clippedtrimmed.fastq.bam
RI_W_07_22_clippedtrimmed.fastq.bam  VA_W_07_22_clippedtrimmed.fastq.bam
[amali010@coreV3-23-031 QCFastqs]$ sbatch AMfreebayessubref.sh
Submitted batch job 9276571
[amali010@coreV3-23-031 QCFastqs]$ squeue -u amali010
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9276571      main AMfreeba amali010  R       0:02      1 coreV3-23-002
           9276494      main       sh amali010  R      58:02      1 coreV3-23-031


#4 - submit and add everything to your logfile
git add README.md
git commit -m 'updating readme'
git push -u origin main
```
