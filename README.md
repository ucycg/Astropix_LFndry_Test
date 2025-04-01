# Astropix_LFoundry_Test

<p align="center">
    <img src="docu/Astropix_LFndry_Testchip.png" alt="placeholder" width="30%" height="30%">
</p>

This super repository shares all necessary steps and procedures including the required software in order to make various analogue measurements with the Astropix-LFoundry-Testchip.

The measurements conducted so far are:

1. Analog Ampout measurements via Tektronix MDO3024 oscilloscope
2. I-V Curve of the -HV photodiode with an 2470 Keithley SMU
3. Analog Hitbus signal measurement after the Astropix comparator

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

#### Ampout and Hitbus measurements

First of all the generated bitfile for the FPGA hardwaredesign has to be installed via the PROG. USB micro port. This can be executed via Vivado directly in the GUI mode via the Hardware Manager 

Click on open target and afterwards on Program device and select the correct bitstream file for the measurement setup.

Afterwards we can start the Power Supply and supply the Gecco PCB with 

1. Voltage: 2.7V for VDD3.3
2. Voltage: 1.8V for POW4 which represents the VDD voltage for the Testchip
3. Voltage: 0V for POW6 which sets the ground potential for Vminus Port of the Testchip

After that the 2470 SMU can be connected directly to the SMA -HV port on
the TestPCB here the -HV Potential is flexible between 0V and ~ -200V

#### I-V Curve Measurement

The actual setup up for the I-V curve measurement is much simpler.

Only the 2470 SMU and the Testpcb with the bonded chip is required.

So far the SMU 2470 has been controlled via a LAN connection. With that an easy control for sweeps is possible via the provided python script in the Measurements_TestScriptProcessor repository.

1. To begin the measurements only connect the -HV potential from the SMU to the SMA connector on the testpcb and then power up the SMU.

2. The provided script RES_SVMI_TSP.py for the I-V Curve measurement first sweeps the voltage between 0V and -200V in steps of 10V. Afterwards the respective measured current at that point is stored inside a .csv file.

3. Finally a basic I-V curve can be plotted from the .csv file with the plot_ui.py script.

Further the LF_TST_PREC_BREAKDOWN_SVMI_TSP.py performs a more narrow analysis around the actualy fully depleted diode operation region.
(-196/-205V in steps of 0.1V).





## Results

### Ampout and Hitbus Measurements

### I-V Curve Measurements

With an increasing negative potential the depletion region of the reversed biased photosensor diode increases as well until it becomes fully depleted at around -200V 


