

# README

## Overview

This project involves performing data analysis on laser spectroscopy experiments to investigate atomic and molecular scale phenomena. The main tasks include:

- Fitting experimental data using a predefined model.
- Extracting relevant parameters from the fit results.
- Plotting various contributions like sideband contributions and changes in core level amplitudes for different run numbers.
- Comparing the results across multiple runs in combined plots.

## Requirements

The following Python libraries are required to run this code:

- `os`
- `matplotlib`
- `xarray`
- `lmfit`
- `scipy`
- `numpy`
- `pandas`
- `matplotlib.font_manager`
- `viridis` colormap

You can install the required libraries using pip:

```bash
pip install matplotlib xarray lmfit scipy numpy pandas
```

## Folder Structure

Ensure that you have the following directory structure:

```
/project_folder
    /data_folder          # Folder containing the experimental data
    /output_folder        # Folder where plots will be saved
    /code_folder          # Folder containing the code
```

## Code Breakdown

### 1. **Fitting Experimental Data**

The code uses the `lineshape` function (which is assumed to be defined elsewhere in the code) to fit data from the different run numbers. The fitting is performed for each run number and the results are stored in the `all_results` dictionary.

```python
# Perform fitting and collect results
all_results = {}
for run_number in run_numbers:
    fits = lineshape(run_number)
    all_results[run_number] = fits
```

### 2. **Plotting Sideband Contributions**

The sideband contributions for `3/2` and `5/2` are plotted for each run number. These contributions are obtained from the fitted parameters (`amp_1p` for 3/2 and `amp_2p` for 5/2).

The plots are saved as individual images for each run number and contribution type:

- **Sideband Contribution for 3/2**
- **Sideband Contribution for 5/2**
  
```python
# Plot sideband contribution for 3/2
plt.figure(figsize=(8, 6))
...
plt.savefig(plot_path, dpi=200)
```

### 3. **Plotting Change in Core Level Amplitude**

The change in core level amplitude for `3/2` and `5/2` is plotted for each run number. These values are extracted from the fitted parameters (`amp_1` for 3/2 and `amp_2` for 5/2).

These plots are also saved as individual images for each run number and amplitude type:

- **Change in Core Level Amplitude for 3/2**
- **Change in Core Level Amplitude for 5/2**

```python
# Plot change in core level amplitude for 3/2
plt.figure(figsize=(8, 6))
...
plt.savefig(plot_path, dpi=200)
```

### 4. **Comparison of Results Across Runs**

The code also compares the sideband contributions and core level amplitude changes across multiple runs for `3/2` and `5/2`. This is done by plotting the results for all run numbers in a single combined plot.

- **Combined Plot for 3/2 Sideband Contribution**
- **Combined Plot for 5/2 Sideband Contribution**
- **Combined Plot for 3/2 Change in Core Level Amplitude**
- **Combined Plot for 5/2 Change in Core Level Amplitude**

```python
# Combined plot for 3/2 sideband contribution
plt.figure(figsize=(10, 8))
...
plt.savefig(plot_path, dpi=200)
```

### 5. **Font and Plot Customizations**

Font settings and plot customization are done using the `matplotlib` library. You can customize the font settings according to your preferences:

```python
# Font settings for plots
font = {'family': 'serif', 'size': 14}
font_properties = FontProperties(**font)
```

## How to Use

1. **Prepare Your Data**: Ensure that the experimental data is available in the `data_folder`.
2. **Run the Code**: Execute the Python code to process the data and generate the plots. Make sure that the `run_numbers` and other parameters are correctly defined in the code.
3. **Check the Output**: The generated plots will be saved in the `output_folder` with filenames that correspond to the run numbers and plot types.
4. **Customize**: You can modify the font settings, plot dimensions, and other plot details to suit your preferences.

## Example Workflow

1. **Prepare Data**: Ensure your data is structured correctly in the input folder.
2. **Run Fitting and Plotting**: Run the code to fit the data and generate the desired plots.
3. **View Results**: Check the plots in the output folder.
4. **Refine Analysis**: Adjust parameters or modify the fitting function if necessary to improve the results.

## Output

After running the code, you will find the following types of plots saved in the `output_folder`:

- `Run_{run_number}_Se3d_sideband_3_2.png`: Sideband contribution for 3/2.
- `Run_{run_number}_Se3d_sideband_5_2.png`: Sideband contribution for 5/2.
- `Run_{run_number}_Se3d_amp_change_3_2.png`: Change in core level amplitude for 3/2.
- `Run_{run_number}_Se3d_amp_change_5_2.png`: Change in core level amplitude for 5/2.
- `Se3d_sideband_3_2_combined.png`: Combined sideband contribution for 3/2 across all runs.
- `Se3d_sideband_5_2_combined.png`: Combined sideband contribution for 5/2 across all runs.
- `Se3d_amp_change_3_2_combined.png`: Combined core level amplitude change for 3/2 across all runs.
- `Se3d_amp_change_5_2_combined.png`: Combined core level amplitude change for 5/2 across all runs.
