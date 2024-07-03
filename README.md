# diaTracer

## Overview
diaTracer is a computational tool that enables spectrum-centric analysis of Bruker's diaPASEF data-independent acquisition proteomics data, facilitating direct (“spectral-library free”) peptide identification and quantification. diaTracer processes diaPASEF raw mass spectrometry data (.d files) and performs three-dimensional (m/z, retention time, ion mobility) peak tracing and feature detection, groups precursor and fragment signals, and generates “pseudo-MS/MS” spectra (in mzML format). These pseudo-MS/MS spectra can then be processed as DDA spectra using MSFragger or any other search engine. diaTracer supports analysis of any diaPASEF proteomics data, including data requiring semi-tryptic (e.g. N-terminomics) or nonspecific (e.g. HLA immunopeptidomics) searches, searches allowing for chemical (e.g. chemical proteomics) or biological modifications (e.g. phosphoproteomics). diaTracer is fast, making direct DIA analysis of large sample cohorts possible. Furthermore, diaTracer enables unrestricted identification of post-translational modifications from diaPASEF data using open/mass offset searches.

diaTracer is available as a stand-alone tool and is fully integrated into FragPipe computational platform.

![image](https://github.com/Nesvilab/diaTracer/assets/29800230/14191096-8b91-42af-8e99-b4e3e2e5a656)
Overview of diaTracer and its place within the FragPipe computational platform. 
diaTracer applies a 3D feature detection algorithm to detect signals from all possible precursors and fragments in MS1 and MS2 diaPASEF data. Pseudo-MS/MS spectra are generated through precursor-fragment clustering and can be processed as DDA data using MSFragger and FragPipe to build a spectral library directly from the data. A hybrid spectral library can also be generated if DDA data are available. This spectral library is then used to extract quantification using DIA-NN.


## System requirements
1. Java 11+
2. 'ext' folder from the latest [MSFragger](https://msfragger.arsci.com/upgrader/).
3. The latest [FragPipe](https://github.com/Nesvilab/FragPipe/releases/latest) (optional).


## Download
The latest diaTracer can be downloaded [here](https://msfragger-upgrader.nesvilab.org/diatracer/).


## Release note
The up-to-date release note can be found in [CHANGELOG.md](CHANGELOG.md).


## How to run diaTracer
### In FragPipe
1. Download [FragPipe](http://fragpipe.nesvilab.org/) from [here](https://github.com/Nesvilab/FragPipe/releases/latest).
2. Follow the tutorial.

### Standalone usage in command line interface
Run `java -jar diaTracer-1.1.4.jar` to get options.

```shell
java -jar diaTracer-1.1.4.jar --dFilePath <.d file path> --threadNum <thread number>

options:
 -d,--dFilePath <arg>           .d file path
 -dI,--deltaApexIM <arg>        Ion mobility delta range for ms1 and ms2
                                match. default 0.01
 -dR,--deltaApexRT <arg>        Apex scan delta range for ms1 and ms2
                                match. default 3
 -h,--help                      Help
 -help                          Help
 -mC,--ms1MS2Corr <arg>         MS1 and MS2 correlation threshold.
                                default: 0.3
 -mF,--massDefectFilter <arg>   Apply mass defect filter. 1: apply; 0: not
                                apply. default: 1
 -mO,--massDefectOffset <arg>   Mass defect offset. default: 0.1
 -r,--writeInter <arg>          write inter files . 1: write; 0: not
                                write. default: 0
 -rM,--RFMax <arg>              Top N peaks in the spectrum. default: 500
 -t,--threadNum <arg>           thread number
 -w,--workDir <arg>             work directory
```

### Test data
Here is one [.d](https://drive.google.com/file/d/1li-pBT006Vnx6yShax9PsMF2Le_oKMSR/view?usp=drive_link) file from the [Florian Meier et al.](https://www.nature.com/articles/s41592-020-00998-0). Please download and unzip it.

```shell
java -jar diaTracer-1.1.4.jar --dFilePath ./20200505_Evosep_100SPD_SG06-16_MLHeLa_100ng_py8_S2-C1_1_2731.d --workDir ./ --writeInter 0 --deltaApexIM 0.01 --deltaApexRT 3 --ms1MS2Corr 0.3 --massDefectFilter 0 --massDefectOffset 0.1 --RFMax 500 --threadNum 12
```
After runing the above command, a mzML file named `20200505_Evosep_100SPD_SG06-16_MLHeLa_100ng_py8_S2-C1_1_2731_diaTracer.mzML` will be generated in the same path of `.d` file. The running time will be around 10 minutes using 12 threads.

## Publication
<a href="https://doi.org/10.1101/2024.05.25.595875" target="_blank">diaTracer enables spectrum-centric analysis of diaPASEF proteomics data</a>
<br>
Kai Li, Guo Ci Teo, Kevin L. Yang, Fengchao Yu, Alexey I. Nesvizhskii
<br>
bioRxiv, DOI: 10.1101/2024.05.25.595875
