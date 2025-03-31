# Astropix_LFndry_Test

![alt text](https://github.com/ucycg/Astropix_LFndry_Test/blob/main/docu/Astropix_LFndry_Testchip.png =100x20)

This super repository shares all necessary steps and procedures including the required software in order to make various analogue measurements with the Astropix-LFoundry-Testchip.

The measurements conducted so far are:

1. Analogue Ampout measurements via Tektronix MDO3024 oscilloscope
2. I-V Curve of the -HV photodiode with an 2470 Keithley SMU
3. Anaolgue Hitbus signal measurement after the Astropix comparator

### Repository structure

So far the Astropix_LFndry_Test repository contains 3 different sub repositories.

1. The astropix-firmware fork contains the HDL design for the Nexus Video FPGA to interact with the Testchip (Unit under Test) via a USB computer interface

2. The astropix-python-LFndry-Test fork supplies python scripts to configure the hardware registers of the Testchip / UUT as well as setting other input parameters  

3. Finally the Measurements_TestScriptProcessor contains TSP and Python
scripts to execute I-V measurements with the 2470 SMU used to generate a 
HV signal

More Detailed description about the installation procedure and about the single repository is available inside the repositories README file

## SETUP AND EXAMPLE USAGE

In this section all necessary steps are detailed in order to begin with an Astropix-LFoundry-Testchip measurement.

First of all the requirements until this step here are listed.

1. AstPx_LFndry_Tst PCB is needed with a bonded Astropix-LFoundry-Testchip
2. Further a Nexus Video FPGA Testboard and a connected  GECCO PCB including an injection card for Ampout/Hitbus measurements
3. Power Supply with 3 distinct sources for the Gecco PCB to generate Testchip voltages
4. SMU to generate the HV Signal 
5. SMA connector cables for analogue oscilloscope measurement and to connect the SMU with the PCB

### Setup
