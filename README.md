# nano-DyMEAN

## Description
Personal modifications of the dyMEAN framework tailored for Nanobody analysis
We start with DyMEAN paper implementation and modify that script to avoid the use of light chain explicitly.
the input for dyMEAN is just the json files(train.json, valid.json and test.json) and all_structure folders which has all pdb structures

## Results Overview or reproducibility of results from DyMEAN Paper using their checkpoint.

| Metric                 | Score  | Pearson Correl. | Lowest (PDB) | Highest (PDB) |
|------------------------|--------|-----------------|--------------|---------------|
| AAR                    | 0.4299 | -0.528          | 0.083 (2xwt) | 0.857 (1ic7)  |
| CAAR                   | 0.2719 | -0.308          | 0.0 (5hi4)   | 0.800 (1ic7)  |
| RMSD(CA) Aligned       | 1.051  | 0.533           | 0.592 (1ic7) | 1.751 (3bn9)  |
| RMSD(CA) CDRH3         | 8.1015 | 0.375           | 0.763 (1ic7) | 22.540 (3w9e) |
| RMSD(CA) CDRH3 Aligned | 1.5784 | 0.422           | 0.417 (1a2y) | 3.778 (4ydk)  |
| TMscore                | 0.9726 | -0.443          | 0.9487 (4dvr)| 0.9896 (1ic7) |
| LDDT                   | 0.8451 | -0.346          | 0.7863 (4ydk)| 0.8991 (1ic7) |
| DockQ                  | 0.4089 | -0.411          | 0.138 (4fqj) | 0.971 (1ic7)  |

## Reproducibility Metrics
Although for now, we have used their checkpoint to see the results, for complete reproducibility, we are training it from scratch and reporting the results.

| Metric                 | Score      | Pearson Correl. | Lowest (PDB)          | Highest (PDB)         |
|------------------------|------------|-----------------|-----------------------|-----------------------|
| AAR                    | 0.3944     | -0.2831         | 0.1333 (5f9o)         | 0.6364 (2adf)         |
| CAAR                   | 0.2580     | -0.1452         | 0.0000 (5hi4)         | 0.7500 (2adf)         |
| RMSD(CA) Aligned       | 1.9963     | 0.4876          | 1.6099 (3k2u)         | 2.7405 (3ffd)         |
| RMSD(CA) CDRH3         | 12.3620    | 0.1425          | 5.1546 (2xqy)         | 24.7095 (5bv7)        |
| RMSD(CA) CDRH3 Aligned | 1.9514     | 0.8618          | 1.0713 (1fe8)         | 4.0119 (3bn9)         |
| TMscore                | 0.9058     | -0.3828         | 0.8652 (3ffd)         | 0.9321 (3k2u)         |
| LDDT                   | 0.5891     | -0.4897         | 0.5514 (4ydk)         | 0.6161 (3l95)         |
| DockQ                  | 0.2820     | -0.0482         | 0.0580 (5hi4)         | 0.5520 (1w72)         |



## Modifications
Key modifications were made to several files to enhance the framework's compatibility with Nanobodies in training and testing. Although for now, we have used their checkpoint to see the results, to see how much we lose in terms of performance if light chain is lost:
- **Preprocessing & Dataloading**: `dataset.py`, `framework_templates.py`, `pdb_utils.py`
- **CDR File Generation**: `generate.py`
- **Metrics Calculation**: `calculate_metrics.py`

For ease of reference, all changes in these files are commented on, highlighting the differences from the original dyMEAN implementation.

## Provided Files
Only the modified files are provided in this repository. These can replace their counterparts in the original dyMEAN framework.


## Results Overview of Antibody without considering Light chain using their checkpoint.

| Metric                 | Score  | Pearson Correl. | Lowest (PDB) | Highest (PDB) |
|------------------------|--------|-----------------|--------------|---------------|
| AAR                    | 0.432  | -0.511          | 0.133 (5f9o) | 0.857 (1ic7)  |
| CAAR                   | 0.286  | -0.299          | 0.0 (4ffv)   | 0.800 (1ic7)  |
| RMSD(CA) Aligned       | 1.177  | 0.385           | 0.711 (4ffv) | 2.204 (3bn9)  |
| RMSD(CA) CDRH3         | 8.070  | 0.376           | 0.742 (1ic7) | 22.473 (3w9e) |
| RMSD(CA) CDRH3 Aligned | 1.612  | 0.411           | 0.546 (1a2y) | 3.831 (4ydk)  |
| TMscore                | 0.945  | -0.367          | 0.902 (4ydk) | 0.972 (4ffv)  |
| LDDT                   | 0.823  | -0.355          | 0.737 (4ydk) | 0.876 (5d93)  |
| DockQ                  | 0.411  | -0.381          | 0.136 (4fqj) | 0.970 (1ic7)  |

## Reproducibility Metrics after training from scratch without considering Light chain:

| Metric                 | Score    | Pearson Correl. | Lowest (PDB)     | Highest (PDB)    |
|------------------------|----------|-----------------|------------------|------------------|
| AAR                    | 0.392    | -0.279          | 0.133 (5f9o)     | 0.636 (2adf)     |
| CAAR                   | 0.256    | -0.142          | 0.000 (5hi4)     | 0.750 (2adf)     |
| RMSD(CA) Aligned       | 2.520    | 0.748           | 2.082 (1fe8)     | 3.162 (4fqj)     |
| RMSD(CA) CDRH3         | 12.286   | 0.149           | 5.266 (2xqy)     | 24.601 (5bv7)    |
| RMSD(CA) CDRH3 Aligned | 2.015    | 0.849           | 1.033 (5d93)     | 4.148 (3bn9)     |
| TMscore                | 0.789    | -0.546          | 0.750 (1osp)     | 0.827 (5d93)     |
| LDDT                   | 0.559    | -0.477          | 0.514 (4ydk)     | 0.590 (5d93)     |
| DockQ                  | 0.285    | -0.047          | 0.076 (3uzq)     | 0.505 (1w72)     |


## Additional Resources
A comprehensive Jupyter Notebook is included, offering insights into CDR (Complementarity-Determining Regions) design. The notebook covers:

1. **Complex Classes**: Introduction to the structures of interest.
2. **Graph Features**: Discussion on graph-based features derived from the structures.
3. **Dataloading**: Procedures for loading and preprocessing data.
4. **Example Datapoint**: A walkthrough of an example datapoint, which in our context is an Antigen-antibody complex. Note: The provided antibody may or may not include a light chain.
5. **Machine Learning Modules**: Overview of the neural network architectures and algorithms used.
6. **Utility Functions**: Auxiliary functions that support the main framework.
7. **Trainer Class**: The class responsible for orchestrating the training process.
