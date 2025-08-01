---
title: Installation
weight: 2
---

If you hope to run ***pipesnake*** on an HPC, cluster, or similar, contact your IT to see if *nextflow* and *Docker/Singularity* are already installed. If they are, jump straight down to **Installing *pipesnake***. 


If you'd like to run the pipeline locally, follow the installation instructions below.

</details>

## Installing nextflow
<details>
<summary>nextflow Instructions</summary>

***pipesnake*** relies on having *nextflow* installed (version >=23.04.1). 

Our advice is to follow the official [nextflow installation instructions](https://www.nextflow.io/docs/latest/install.html#installation). 

<details>
<summary>Having trouble?</summary>

For the vast majority of people *nextflow* installation should be relatively painless. If that's not you, follow along below. *nextflow* requires a recent version of Java (11+). You can check which Java you're running by opening up a terminal and typing 
```
java -version
``` 
If you need a newer version of Java, you can start by installing SDK with the command 
```
curl -s "https://get.sdkman.io" | bash
```
Once that installation has completed, close your terminal and open a fresh one. You should then be able to install a newer Java with SDK, e.g. 
```
sdk install java 17.0.6-amzn
```
Finally, you can download *nextflow* with 
```
wget -qO- https://get.nextflow.io | bash
```
then make the binary executable with 
```
chmod +x nextflow
```
Feel free to move the nextflow file to the directory of your choice, and add it to your `$PATH` variable so you can call it with `$ nextflow` instead of specifying the full path name.
</details>

</details>



## Installing Docker or Singularity
<details>
<summary>Container Instructions</summary>

*nextflow* works by operating software that has been containerized by *Docker* or *Singularity*. Recently, *Singularity* changed their name to *Apptainer*, we'll stick with *Singularity* for consistency.

Our advice is to follow the official [*Docker*](https://docs.docker.com/engine/install/) or [*Singularity*](https://apptainer.org/docs/admin/main/installation.html). 

<details>
<summary>Having Trouble?</summary>

If you're running into trouble installing *Docker*, consider using [*Docker Desktop*](https://docs.docker.com/desktop/), a streamlined version with a useful interface. 

If you're running into trouble installing *Singularity*, try following [these instructions](https://singularity-tutorial.github.io/01-installation/).
</details>


</details>

## Installing pipesnake

Once you've got _nextflow_ and your container operator working, install ***pipesnake*** with:
```
nextflow pull ausarg/pipesnake
```

You can test that your installation worked (this will end with a "Validation of pipeline" error, ignore it):
```
nextflow run ausarg/pipesnake

N E X T F L O W   ~  version 24.10.0

Launching `pipesnake_dev_28072025/main.nf`

------------------------------------------
  ausarg/pipesnake v1.2
------------------------------------------
...

```

## Where is it?
Typically, ***pipesnake*** will be installed in ` ~/.nextflow/assets/ausarg/pipesnake `.
If you want to work from a different directory, you can clone the repository and work from there.
```
git clone https://github.com/AusARG/pipesnake.git ~/Desktop/pipesnake
Cloning into 'Desktop/pipesnake'...

# test the install
nextflow run ~/Desktop/pipesnake
```




