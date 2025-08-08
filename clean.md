# Filtering raw reads and quality control

## Filtering raw reads

In order to filter FASTQ files, meaning trimming adapter sequences, removing low quality sequences, and matching read mates (R1 and R2) you can use the [***Trimmomatic***](https://github.com/usadellab/Trimmomatic) software.

```
conda deactivate  # If you are not at (base) environment
conda create --name trimmomatic
conda activate trimmomatic
conda install bioconda::trimmomatic
```

Before you can trim adapter sequences, you will need the Illumina adapter sequences used in the experiment in a FASTA file. In this case the experiment run [SRR7464845](https://www.ncbi.nlm.nih.gov/sra/?term=SRR7464845) was conducted in a Illumina HiSeq 2500 instrument, which uses the [TruSeq3 adapters](https://github.com/depaulats/MARRIO_genomics/blob/main/adapters/TruSeq3-PE-2.fa). 

Download the FASTA file to `/mnt/c/MARRIO_genomics`:

```
wget https://raw.githubusercontent.com/depaulats/MARRIO_genomics/main/adapters/TruSeq3-PE-2.fa -P /mnt/c/MARRIO_genomics/
```

Now run the comand:

```
trimmomatic PE -threads 8 -phred33 \
  /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_1.fastq \
  /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_2.fastq \
  /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_1_paired.fastq \
  /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_1_unpaired.fastq \
  /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_2_paired.fastq \
  /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_2_unpaired.fastq \
  ILLUMINACLIP:/mnt/c/MARRIO_genomics/TruSeq3-PE-2.fa:2:30:10 \
  LEADING:3 TRAILING:3 \
  SLIDINGWINDOW:4:20 \
  MINLEN:50
```

After some time, you will get the output files containing both R1 and R2 paired and unpaired reads. You want to use the paired ones `SRR7464845_1_paired.fastq` and `SRR7464845_2_paired.fastq`.

## Quality control

For quality control of your dataset you can use the [***FastQC***](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/) software.

Download the corresponding version for you OS and execute the `run_fastqc` script. It will open a GUI application for you to open your FASTQ files for analysis.

Evaluate all parameters you find relevant for both raw and filtered reads. For instance contrast total sequences, bases, lenght, %GC, as well as graphical representation of sequence quality and content, and adpater content.

You can save all reports in both html and txt files at once for each analysis to use them again later.

Now that you have a filtered data acing all quality control parameters you need, you can [mapping those reads against a reference sequence](https://github.com/depaulats/MARRIO_genomics/blob/main/map.md).

Or you can go back to the [tutorials](https://github.com/depaulats/MARRIO_genomics/blob/main/tutorials.md). 
