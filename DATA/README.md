# Data Folder
## Purpose
This folder stores all datasets used in the project. It includes the initial downloaded Navier–Stokes simulation files, in the `../DATA/OriginalData` folder, as well as the final processed data, in the `../DATA/PreProcessedData` folder, used for model training and evaluation. The processed dataset removes the vertical velocity channel to reduce dimensionality while retaining the features necessary for reconstruction modeling.

# Metadata

## Data Summary
The project uses a 2D turbulent fluid-flow dataset generated from numerical Navier–Stokes simulations. Each file originally contains four physical channels across 39 time steps. The raw dataset structure is:
- Shape (raw): (39 time steps, 4 channels, 128 height, 256 width)
- Raw channels:
    - u: horizontal velocity
    - v: vertical velocity
    - p: pressure
    - ω: vorticity

Exploratory analysis showed that the v channel contributes minimal high-frequency structure and exhibits negligible variation across flow regimes. Because of this limited informational value, the v channel is removed during preprocessing.

The final dataset used for modeling has the structure:
- Shape (processed): (39 time steps, 3 channels, 128 height, 256 width)
- Processed channels:
    - u (horizontal velocity)
    - p (pressure)
    - ω (vorticity)

The dataset provides multiple flow regimes across increasing Reynolds numbers to support model generalization. Data are stored in `.npy` format and designed for evaluating machine learning methods that reconstruct or model fluid dynamics.

## Provenance
The dataset originates from the PARCv2 project released on Zenodo, which provides physics-based fluid simulations for research on spatiotemporal modeling. All data were generated via numerical solvers, not real-world measurements. The training and test folders in the release are distinct and were used as provided to avoid leakage.
Source: Zenodo record 13909869 https://zenodo.org/records/13909869

## License

The dataset is distributed under CC BY 4.0, permitting reuse and modification with attribution. Associated code in the PARCv2 repository is licensed under MIT. These licenses allow unrestricted research use when authors are credited.

## Ethical Statements

There are no human subjects or privacy concerns. The main ethical consideration is accurate reporting of reconstruction results and avoiding claims beyond simulated environments. Dataset usage requires acknowledging simulation limits and refraining from overstating physical realism.

## Data Dictionary
| Field | Description                                          | Type    |
| ----- | ---------------------------------------------------- | ------- |
| u     | horizontal velocity                                  | float32 |
| v     | vertical velocity                                    | float32 |
| p     | pressure                                             | float32 |
| ω     | vorticity                                            | float32 |
| T     | number of time steps per sample (39)                 | int     |
| H     | grid height (128)                                    | int     |
| W     | grid width (256)                                     | int     |
| Re    | Reynolds number associated with each simulation file | int     |

All files share identical spatial and temporal structure.

