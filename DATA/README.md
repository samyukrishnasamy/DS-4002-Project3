# Data Folder
## Purpose
This folder stores all datasets used in the project. It includes the initial downloaded Navier–Stokes simulation files as well as the final processed data used for model training and evaluation.

# Metadata

## Data Summary
The project uses a 2D turbulent fluid-flow dataset generated from numerical Navier–Stokes simulations. Each file contains a sequence of fluid states at a fixed Reynolds number. Every simulation has the same structure:
- Shape: (39 time steps, 4 channels, 128 height, 256 width)
- Channels:
    - u: horizontal velocity
    - v: vertical velocity
    - p: pressure
    - ω: vorticity
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

