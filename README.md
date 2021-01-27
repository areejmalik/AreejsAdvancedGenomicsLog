2021_Spring_Areej's Advanced Genomics Notebook

##Day 02 22-Jan-2021
* Exercise day02
```sh

#1 - Logon to the cluster @turing.hpc.odu.edu
[amali010@turing1 ~]$ ls
data  exercises  hpc-intro

#2 - Make a directory in your course workspace called data
[amali010@turing1 ~]$ mkdir data

#3 - Make a directory called exercises in your data directory
[amali010@turing1 data]$ mkdir exercises

#4 - Execute a pwd command and start a log of your commands with a 
header for today's date in your README.md github logfile in your workspace
[amali010@turing1 exercises]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/areej/data/exercises 

#5 - cp the Exercise2.fasta.gz and Exercise2.fastq.tar.gz files into your 
exercises directory from the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02 directory
[amali010@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02/Exercise2.fast* ./
[amali010@turing1 exercises]$ ls
Exercise2.fasta  Exercise2.fasta.gz  Exercise2.fastq  Exercise2.fastq.tar.gz
[amali010@turing1 exercises]$ ls -lah
total 54M
drwxrwxrwx 2 amali010 users  106 Jan 26 17:46 .
drwxrwxrwx 3 amali010 users   27 Jan 22 13:36 ..
-rwxr-xr-x 1 amali010 users  17M Jan 26 17:44 Exercise2.fasta
-rw-r--r-- 1 amali010 users  18M Sep  2  2015 Exercise2.fastq
-rwxr-xr-x 1 dbarshis users 4.3M Jan 22 13:51 Exercise2.fastq.tar.gz

#6 - unzip and untar the files
[amali010@turing1 exercises]$ gunzip Exercise2.fasta.gz
[amali010@turing1 exercises]$ ls
Exercise2.fasta  Exercise2.fastq  Exercise2.fastq.tar.gz
[amali010@turing1 exercises]$ ls -lah
total 54M
drwxrwxrwx 2 amali010 users  106 Jan 26 17:46 .
drwxrwxrwx 3 amali010 users   27 Jan 22 13:36 ..
-rwxr-xr-x 1 amali010 users  17M Jan 26 17:44 Exercise2.fasta
-rw-r--r-- 1 amali010 users  18M Sep  2  2015 Exercise2.fastq
-rwxr-xr-x 1 dbarshis users 4.3M Jan 22 13:51 Exercise2.fastq.tar.gz

[amali010@turing1 exercises]$ tar -xzvf Exercise2.fastq.tar.gz
Exercise2.fastq
[amali010@turing1 exercises]$ ls -lah
total 56M
drwxrwxrwx 2 amali010 users  106 Jan 26 17:54 .
drwxrwxrwx 3 amali010 users   27 Jan 22 13:36 ..
-rwxr-xr-x 1 amali010 users  17M Jan 26 17:44 Exercise2.fasta
-rw-r--r-- 1 amali010 users  18M Sep  2  2015 Exercise2.fastq
-rwxr-xr-x 1 dbarshis users 4.3M Jan 22 13:51 Exercise2.fastq.tar.gz

#7 - add these commands to your notebook
Done

#8 calculate how many sequences are in each file and add these 
results to your notebook file
[amali010@turing1 exercises]$ head -2 Exercise2.fasta (Note: wasn't 
able to see the sequence when doing assignment outside of class time)
[amali010@turing1 exercises]$ head -1 Exercise2.fasta (same issue as above)
grep -c '>' Exercise2.fasta
0 (Note: I don't know what I did wrong but maybe this might be why 
I couldn't see the sequence)
[amali010@turing1 exercises]$ head -1 Exercise2.fastq
@HS3:541:HAYTUADXX:1:1101:1297:1938 1:N:0:AGTTCC
[amali010@turing1 exercises]$ grep -c '@HS3' Exercise2.fastq
61304
[amali010@turing1 exercises]$ wc -l Exercise2.fastq
245216 Exercise2.fastq
[amali010@turing1 exercises]$ echo 245216/4 | bc -l
61304.00000000000000000000
[amali010@turing1 exercises]$ grep -c "@HS3:541" Exercise2.fastq
61304

#9 - cp the avg_cov_len_fasta_advbioinf.py from the
 /cm/shared/courses/dbarshis/21AdvGenomics/scripts directory into your class scripts directory
[amali010@turing1 scripts]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py ../scripts
[amali010@turing1 scripts]$ less avg_cov_len_fasta_advbioinf.py

#10 - start an interactive compute session and re-navigate 
to your exercises directory
[amali010@turing1 scripts]$ salloc
salloc: Pending job allocation 9270297
salloc: job 9270297 queued and waiting for resources
salloc: job 9270297 has been allocated resources
salloc: Granted job allocation 9270297

#11 - run the avg_cov_len_fasta_DJB.py script on your 
Exercise2.fasta file by typing the path to the script followed 
by the Exercise2.fasta file name


#12 - did you add all these entries to your notebook file, 
including the results of the script?


#13 - push your notebook file to your github page
git add README.md
git commit -m 'updating readme'
git push -u origin main

```