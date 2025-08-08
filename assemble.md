# Assembling mapped reads

In order to assemble your mapped reads you will need to use the [MEGAHIT](https://github.com/voutcn/megahit) software.

```
conda deactivate  # If you are not at (base) environment
conda create --name megahit
conda activate megahit
conda install bioconda::megahit
```

In practice we will conduct a de novo assembly, but, instead of using information about the reads aligment to the reference, we are using a restricted number of reads, viz., only those mapped against the reference.

Thus, we simply run:

```
megahit --12 /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA_mapped.fastq \
  --out-dir /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA
```

After some time, you will get all the output files from the analysis in the `/mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA` folder. 

You can check its content with:

```
ls /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA
```

The nucleotide sequences of the assembled contigs are saved in `final.contigs.fa`. 

To extract the largest contig in that file into a separate FASTA file you can you [Seqtk](https://github.com/lh3/seqtk):

```
conda deactivate # We want to install it at base since this is a basic sequence manipulation tool
conda install bioconda::seqtk
```

To `subset` or data, we will need the header of that contig. First, use the size of the largest contig (only numbers, e.g., `18801`) to get its headers and 2) save its label (after the '>' sign, e.g., `k141_12`) so you can then 3) save it to a file:

```
grep "18801" /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA/final.contigs.fa
echo "k141_12" > /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA/largest-contig-header.txt
seqtk subseq /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA/final.contigs.fa /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA/largest-contig-header.txt > /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA/largest-contig.fasta
```

## Visualizing contigs

All intermediate contigs are saved in the `intermediate_contigs` folder. You can use those to visualize your contigs with the [***Bandage***](https://rrwick.github.io/Bandage/) software.

To start, run the command below to save your graphs in the FASTG format:

```
megahit_toolkit contig2fastg 99 /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA/intermediate_contigs/k99.contigs.fa > /mnt/c/MARRIO_genomics/SRR7464845/SRR7464845_mtDNA/k99.fastg
```

Next, go to the Bandage page and download the corresponding version for you OS. Execute the `Bandage` software and open the `k99.fastg` file you generated above and darw the graphs with default options (you can change those later).

Did you get a circular mitochondrial genome? 

Now that we have our largest contig, let's compare it with the reference by [sequence alignment](https://github.com/depaulats/MARRIO_genomics/blob/main/align.md).

Or you can go back to the [tutorials](https://github.com/depaulats/MARRIO_genomics/blob/main/tutorials.md). 

