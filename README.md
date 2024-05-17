# diaTracer

## Overview
diaTracer processes four-dimensional (intensity, m/z, retention time, ion mobility) diaPASEF scans to generate precursor-resolved “pseudo-MS/MS” spectra, facilitating direct (spectral-library free) peptide identification and quantification from diaPASEF data. diaTracer is available as a stand-alone tool and is also fully integrated in the widely used FragPipe computational platform. 
![image](https://github.com/Nesvilab/diaTracer/assets/29800230/14191096-8b91-42af-8e99-b4e3e2e5a656)

## Download
The latest diaTracer can be downloaded [here](https://msfragger-upgrader.nesvilab.org/diatracer/).

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
