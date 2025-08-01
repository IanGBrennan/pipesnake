---
title: Tutorial II
weight: 2
---


## Running End-to-End

The [example data](https://github.com/AusARG/pipesnake/tree/main/example) in `example/data/` holds a toy dataset for 4 samples in various forms (raw reads, alignments, PRG files). To get a better idea of how the pipeline works, we can upack [Tutorial I](https://iangbrennan.github.io/pipesnake2/docs/tutorials/tutorial-i/) and use example data to step through it.

Let's start by creating a clean directory for us to practice in. We'll copy over the example data to this directory as well.

```
# make a new directory and move into it
mkdir pipesnake_tutorials
cd pipesnake_tutorials

# copy the example data across
cp -r ~/.nextflow/assets/ausarg/pipesnake/example/data .
```
___

## Sample Sheets and Target Files
There are two required input files for any ***pipesnake*** run: 

<details>
<summary>--input</summary>

The `--input` is a  .csv sample sheet with information about the sequence file names, barcodes, adaptors, and sample identification. 

| sample_id  | read1  | read2  | barcode1  | barcode2 |  adaptor1  | adaptor2  | lineage
| ---------  | -----  | -----  | --------  | -------- |  --------  | --------  | -------
| Sample1 | /Sample1_A_R1.fastq | /Sample1_A_R2.fastq | AGGTTTGAGC | TACCTGGTCG | TCAC*ATCT | ACAC*ACAC | Crocodile
| Sample2 | /Sample2_A_R1.fastq | /Sample2_A_R2.fastq | CGGTGGAAGC | GTGTCTGAAG | TCAC*ATCT | ACAC*ACAC | Gecko
| Sample3 | /Sample3_A_R1.fastq | /Sample3_A_R2.fastq | TACTTACTGG | GAAATCCTAC | TCAC*ATCT | ACAC*ACAC | Snake
| Sample1 | /Sample1_B_R1.fastq | /Sample1_B_R2.fastq | TCACCGATAA | AGGCACACTC | TCAC*ATCT | ACAC*ACAC | Crocodile

+ The sample sheet must have the above headers, but additional columns (e.g. notes) are ok to include though will not be read. 
+ A single entry (row) corresponds to a pair of sequence read files (R1 & R2) for the same sample, but an individual sample may have multiple entries (see Sample1). 
+ `read1` and `read2` <u>must</u> indicate the absolute path to the read files. 
+ The \* in adaptor sequences indicates the placement of the barcode sequence. Information about standard Illumina adaptors and trimming can be [found here](https://knowledge.illumina.com/library-preparation/general/library-preparation-general-reference_material-list/000001314). 
+ The `lineage` designation is what you would like that sample to ultimately be called in output alignments, locus trees, and the species tree. Save your sample sheet as a comma-separated `.csv` file.
+ An example sample sheet is included in the [`ToyData_SampleInfo.csv`](https://github.com/AusARG/pipesnake/tree/main/example/data/ToyData_SampleInfo.csv)

</details>

<details>
<summary>--blat_db</summary>

The `--blat_db` is a fasta file with sequences for the targets. 

   ```console
   >RAG1  
   TATGTTCAAATGTCCTTGGAAAACTTCTGTCT...  
   >AHE-L1  
   AACTTATACAAATCTTGGATGCCATGGATCCA...
   >UCE-1520
   ACAGAGGTCGATATACCGTAGAAGATGTCCAG...
   ...
   ``` 

+ The target sequence file is simply a FASTA file of your focal loci. Locus names <u>must</u> be unique, and ideally the target sequence data is not too divergent from your samples (though BLAT is quite flexible). 
+ An example targets file is included in [`ToyData_SqCL_25Targets.fasta`](https://github.com/AusARG/pipesnake/tree/main/example/data/ToyData_SqCL_25Targets.fasta), and is appropriate for use with SqCL projects. 

</details>

___

## Running the Example Data

Now that we know what our `--input` and `--blat_db` files should be, we can run the pipeline. It's important that before you do this, you <u>must</u> open the `ToyData_SampleInfo.csv` file and correct the paths of the `read1` and `read2` files. Also, remember to set the `-profile` variable appropriately (singularity or docker). 

```
nextflow run ausarg/pipesnake -profile singularity --input data/ToyData_SampleInfo.csv --blat_db data/ToyData_SqCL_25Targets.fasta --outdir ToyData_end2end
```

Awesome. Assuming that worked, you should have an output directory that is identical to that from the `-profile test` command in [**Tutorial I**](http://localhost:1313/docs/tutorials/tutorial-i/). 


