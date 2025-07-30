---
title: Tutorial I
weight: 2
---


## Running Test Data

You can simultaneously download the pipeline and run a test example with a single command. 

<details>
<summary>Using Docker</summary>
   
```
nextflow run ausarg/pipesnake -profile test,docker --outdir <OUTDIR>
```

</details>

<details>
<summary>Using Singularity</summary>

If you are using `singularity`, first use [`nf-core download`](https://nf-co.re/tools/#downloading-pipelines-for-offline-use) to download the singularity images for the necessary software before running the pipeline. If you don't already have `nf-core` ([`nf-core/tools`](https://nf-co.re/tools)) installed, you can do that easily in a variety of ways (e.g. conda, pip, etc), [see here](https://nf-co.re/tools#installation). 

   ```
   nf-core download ausarg/pipesnake
   ```
Once you have installed `pipesnake` with `nf-core` you can run the test. 
   ```
   nextflow run ausarg/pipesnake -profile test,singularity --outdir <OUTDIR>
   ```
</details>

### Results

Depending on your compute resources, the test data might take up to 10 minutes, but generally less. Once it has completed, we can check out all the outputs. 

