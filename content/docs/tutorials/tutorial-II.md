---
title: Tutorial II
weight: 2
---


## Running End-to-End


## Content and Options

The [example data](https://github.com/AusARG/pipesnake/tree/main/example) holds a toy dataset (reduced read files, 25 target loci) for 4 samples. 

You can run the example data to test your system setup either by
1. following the instructions in the [Quick-Start guide](https://github.com/AusARG/pipesnake/wiki/2.-Quick-Start) which automatically runs the example based on the Nextflow `-profile test`
2. following the instructions below by using local data files

___

## Running the Example Locally

To run the example data 
1. follow the nextflow and pipesnake installation instructions in the [Quick-Start guide](https://github.com/AusARG/pipesnake/wiki/2.-Quick-Start)
2. make sure to change file paths in the *ToyData_SampleInfo.csv* file to direct to the read files (full paths within your working directory).
3. run the example analysis with read filtering:
```
nextflow run pipesnake/ --input pipesnake/example/data/ToyData_SampleInfo.csv --outdir pipesnake/TEST2 --blat_db pipesnake/example/data/ToyData_SqCL_25Targets.fasta --filter pipesnake/example/data/ToyData_SqCL_Filter.fasta -profile [docker/singularity/conda choose accordingly]
```
4. or run the example analysis without read filtering:
```
nextflow run pipesnake/ --input pipesnake/example/data/ToyData_SampleInfo.csv --outdir pipesnake/TEST2 --blat_db pipesnake/example/data/ToyData_SqCL_25Targets.fasta -profile [docker/singularity/conda choose accordingly]
```

---

## Monitoring Resource Usage

The included example dataset runs on a mid-tier local machine (88 CPU, 94 Gb memory) in <4 minutes.  
Once your analysis is done, you can find information on resource usage in the `tracing/pipeline_info/` directory of your output directory.  

---
