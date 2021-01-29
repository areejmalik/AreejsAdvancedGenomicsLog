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
#1 - Write an sbatch script to cp the files /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/ into your own data directory
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

#2 - Add the content of your sbatch script to your logfile
[amali010@coreV2-25-072 data]$ cat AMCopyLane06.sh
#!/bin/bash -l

#SBATCH -o AMCopyLane06.txt
#SBATCH -n 1
#SBATCH --mail-user=amali010@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=AMCopyLane06

cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/HADB06*.fastq.gz /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data

#3 - Submit the slurm script (sbatch scripname.sh) and verify 
that it's working (by squeue -u yourusername multiple times and 
checking the destination directory to make sure the files are being created)
[amali010@coreV2-25-072 data]$ sbatch AMCopyLane06.sh
Submitted batch job 9270443

#4 - Make sure this is all documented on your github notebook
Done

#5 - Write a sbatch script to gunzip all the fastq.gz files
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

#6 - Push your notebook file to your github page
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
the /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py script into your sandbox scripts folder and less the new script and check out the usage statement
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

#5 - Uncomment the last line of the renaming script in your scripts folder that starts with os.popen and comment 
out the next to last line that starts with print
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ nano ../../scripts/renamer_advbioinf.py

#6 - write a sbatch script and submit it to rename all the .fastq files according to the renaming table using 
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

#7 - Make sure this is all documented on your github page
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

#8 - The naming convention for the files is as follows:
	SOURCEPOPULATION_SYMBIOTICSTATE_GENOTYPE_TEMPERATURE.fastq
	There are 2 sources: Virginia and Rhode Island
	There are 2 symbiotic states: Brown and White
	
#9 - Next, you're going to start the process of adapter clipping and quality trimming all the renamed .fastq files in batches, by lane

#10 - cp the script /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Trimclipfilterstatsbatch_advbioinf.py into your scripts directory
[amali010@coreV1-22-016 data]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data
[amali010@coreV1-22-016 data]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/

#11 - Less/head the new script and check out the usage statement
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

#12 - cp the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt into the working directory with your fastq files
[amali010@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/fastq
[amali010@turing1 fastq]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt ./

#13 - Make a sbatch script for the Trimclipfilter... script and run it on your fastq files
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
NOTE: I don't know why it keeps failing the job partition I even tried logging out the core and
remained on turing but that was rejected as well. :(

After multiple attempts
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

#14 - Push your notebook file to your github page
git add README.md
git commit -m 'updating readme'
git push -u origin main

```