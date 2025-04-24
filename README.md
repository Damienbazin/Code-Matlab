# Code-Matlab
Matlab code used to get some plot in the report

Most of the code used in this project is written as MATLAB Live Scripts (.mlx), which cannot be properly displayed on GitHub and are best viewed using the MATLAB application. For convenience, I will also provide standard MATLAB script (.m) versions of the files

# --------------------------------------------------------------------------------------------------------------------------------------

# 1: spot_contrast_aperture_change.m ou spot_contrast_aperture_change.mlx

This MATLAB script analyzes the evolution of iSCAT contrast values for particles observed under different aperture settings (`apt1` to `apt4`). It tracks individual spots detected in `apt1` across the other datasets and compares their contrast values (after applying a cube-root transformation) to evaluate contrast consistency and quality.

## Features
- Loads and processes seven `.mat` files, each corresponding to a different aperture setting.
- Filters spots from `apt1` based on a specific third-root contrast range.
- Matches filtered spots with those in other datasets using KD-tree proximity search.
- Computes third-root contrast values for matched spots.
- Identifies the aperture setting with the best average contrast.
- Produces plots:
  - **Figure 2-(h)**: Evolution of third-root contrast across aperture settings.
  - **Figure 3**: Comparison of average contrast between `apt1` and `apt2.5`.

##  Required Input Files
The script expects the following `.mat` files in the working directory:
- `candidates_apt1.mat`
- `candidates_apt1p5.mat`
- `candidates_apt2.mat`
- `candidates_apt2p5.mat`
- `candidates_apt3.mat`
- `candidates_apt3p5.mat`
- `candidates_apt4.mat`

Each file must contain a `candidates` struct with at least:
- `pos_x`, `pos_y`: spot coordinates
- `iscat.ctr`: iSCAT contrast values

## Output
- Matched contrast values stored in memory
- Plots of third-root contrast evolution across aperture indices
- Console output summarizing filtering and matching steps
- Mean and standard deviation of contrast per aperture
  
## Notes
- The original version of this script is a MATLAB Live Script (`.mlx`) and is best viewed in the MATLAB desktop environment.

# --------------------------------------------------------------------------------------------------------------------------------------

# courbe_violin_spfi_2.m ou courbe_violin_spfi_2.mlx

This MATLAB script visualizes iSCAT contrast distributions for silica beads of varying sizes under two illumination wavelengths (440 nm and 740 nm). It generates **violin plots** representing third-root transformed contrast values, fits linear regressions to the medians, and estimates the **Limit of Detection (LOD)** for each wavelength.

## Features
- Loads `.mat` data files containing iSCAT contrast and RVT values for various particle sizes and wavelengths.
- Filters data based on contrast intensity and RVT thresholds.
- Applies third-root transformation to contrast values.
- Generates side-by-side violin plots for:
  - 440 nm (blue) and 740 nm (orange) illumination
- Computes and displays the median contrast for each group.
- Fits linear regressions through the origin for LOD estimation.
- Outputs LOD values for both wavelengths and their average.
- Produces plots:
  - **figure 5**: Calibration curve between iSCAT contrast and silica bead size for LOD estimation

## Expected Input Files
The script expects `.mat` files containing structures with the following fields:
- `iSCAT440`, `iSCAT740`: contrast values at 440 nm and 740 nm
- `RVT`: a metric used for filtering spots

Examples:
- `spfi_w3_440.mat`
- `spfi_w3_740.mat`

These files must be located in the same directory as the script.

## Output
- A figure displaying violin plots and linear regression lines
- Console output with:
  - Regression coefficients
  - Calculated LODs at 440 nm, 740 nm, and their average

## Notes
- This script is designed for data visualization and calibration of iSCAT systems based on particle size and illumination conditions.
- The figure produced contributes to the quantification of the system’s sensitivity.

# --------------------------------------------------------------------------------------------------------------------------------------







