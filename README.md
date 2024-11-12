# ISFET_APP
Application to process ISFET pH sensor data: SOAR_QC_live_script.mlx

The app requires 4 inputs:
1) The SeaFET data file. An example file is included: "SIOPier_240201_240417_SIO7JS.csv"
2) The bottle data file. An example file is included: "SOAR bottle samples.csv"
3) A file with time of tris injections. An example file is included: "SOAR tris times.csv"
4) Path to CO2SYS v3.1.2 which is included in this repository.

The follow steps outline the quality control and calibration process:
1) Select and upload input files
2.1) Enter start and end datetimes to trim the deployment if desired.
2.2) Use the brush tool to manually select outlier data points or times of biofouling or sensor error.
2.3) Apply quality control flags to bottle and tris data:
   - QC = 1, good
   - QC = 2, bad
   - QC = 3, questionable
   - QC = 4, no sensor data at time of bottle/tris sample
3) Calculate k0 calibration coefficients for bottle/tris.
3.1) Select k2 option from Martz et al. 2010 or previsouly determined value.
3.2) Plot k0 values over time and look at standard deviations of the values. Determine if within 300 uV standard deviation.
4) Based on standard deviation and number of calibration points, use a mean or linear k0 value to process and calculate corrected pH.
4.1) New figure window will open allowing the user to brush any unwanted or erroneous data.
4.2) Save the brushed data and view the final corrected pH.
5) Enter any final notes during quality control process
6) Select folder location to save processed data and quality control pdf document.
6.1) 3 files will be created: .csv file of the processed data, .mat file of the processed data, and .pdf document with all plots and notes.
   Examples of these files are in this repository:
      - "SIOPier_240201_240417_SIO7JS_QC_20240807225753.csv"
      - "SIOPier_240201_240417_SIO7JS_QC_20240807225753.mat"
      - "SIOPier_240201_240417_SIO7JS_QC_20240807225753.pdf"
6.2) Quality controlled bottle and tris files (.csv and .mat) will also be created.
Examples of these files are in this repository:
      - "Bottle_SIOPier_240201_240417_SIO7JS_QC_20240807225753.csv"
      - "Bottle_SIOPier_240201_240417_SIO7JS_QC_20240807225753.mat"
      - "Tris_SIOPier_240201_240417_SIO7JS_QC_20240807225753.csv"
      - "Tris_SIOPier_240201_240417_SIO7JS_QC_20240807225753.mat"
   
