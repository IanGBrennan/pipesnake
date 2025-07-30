---
title: Installation
weight: 2
---

## Installing `nextflow`
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

## Installing `pipesnake`

Once you've got nextflow working, installing pipesnake is as easy as:
```
nextflow pull ausarg/pipesnake
```


