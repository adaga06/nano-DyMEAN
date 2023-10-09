# nano-DyMEAN

## Description
Personal modifications of the dyMEAN framework tailored for Nanobody analysis.
We start with DyMEAN paper implimentation, and modify that scripts to avoid the use of lighchain explicly.
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
Following are the metrics obtained after training exclusively on heavy chains:


## Modifications
Key modifications were made to several files to enhance the framework's compatibility with Nanobodies in training and testing. Altough for now, we have used their checkpoint to see the results, to see how much we loose in terms of performace if light chain is lost:
- **Preprocessing & Dataloading**: `dataset.py`, `framework_templates.py`, `pdb_utils.py`
- **CDR File Generation**: `generate.py`
- **Metrics Calculation**: `calculate_metrics.py`

For ease of reference, all changes in these files are commented, highlighting the differences from the original dyMEAN implementation.

## Provided Files
Only the modified files are provided in this repository. These can replace their counterparts in the original dyMEAN framework.

## Additional Resources
A comprehensive Jupyter Notebook is included, offering insights into CDR (Complementarity-Determining Regions) design. The notebook covers:

1. **Complex Classes**: Introduction to the structures of interest.
2. **Graph Features**: Discussion on graph-based features derived from the structures.
3. **Dataloading**: Procedures for loading and preprocessing data.
4. **Example Datapoint**: A walkthrough of an example datapoint, which in our context is an Antigen-antibody complex. Note: The provided antibody may or may not include a light chain.
5. **Machine Learning Modules**: Overview of the neural network architectures and algorithms used.
6. **Utility Functions**: Auxiliary functions that support the main framework.
7. **Trainer Class**: The class responsible for orchestrating the training process.

## Results Overview or reproducibility of results from DyMEAN Paper using their checkpoint.

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

## Reproducibility Metrics after training on heavy chain alone:

