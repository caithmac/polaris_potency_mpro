# Antiviral Potency Prediction using Gaussian Process Regression

This repository contains code for predicting antiviral potency (pIC50 values) of molecules against SARS-CoV-2 and MERS-CoV main proteases (Mpro) using Gaussian Process Regression. This approach was developed for the ASAP Discovery x OpenADMET Competition (March 2025).


## Approach 1 :  (GP_only.ipynb)

We implemented a straightforward Gaussian Process Regression model with molecular fingerprints as input features:

1. **Data Representation**: 
   - Molecules are represented as ECFP fingerprints using the Datamol library
   - Each molecule is converted from SMILES string to a binary fingerprint vector

2. **Model Architecture**:
   - Two separate Gaussian Process models (one for each viral target)
   - Linear kernel for covariance function (alternative kernels available)
   - Trained using exact marginal log likelihood optimization

3. **Training Procedure**:
   - Adam optimizer with learning rate decay
   - 100 training epochs
   - Hyperparameter settings: initial learning rate = 0.1, decay factor = 0.95

### Key Components

- `TanimotoKernel`: A custom kernel implementing Tanimoto similarity for binary fingerprints
- `GPRegressionModel`: A configurable GP model with multiple kernel options
- `train_gp_model`: Function for training GP models with learning rate scheduling

### Performance

This baseline model provides a solid foundation for antiviral potency prediction. The Gaussian Process approach offers several advantages:

- Provides uncertainty estimates along with predictions
- Works well with limited training data
- Captures non-linear relationships between molecular structure and activity

### Potential Improvements

Future iterations could explore:

- Different molecular representations (graph-based features, pharmacophore fingerprints)
- Alternative kernels (Tanimoto, RBF, Matern)
- Hyperparameter optimization via cross-validation
- Multi-task learning to leverage correlations between targets
- Ensemble methods combining multiple models

### Usage

The code is organized into a single Python notebook (`GP_only.ipynb`) that handles the entire workflow from data loading to prediction submission.

### Dependencies

- PyTorch
- GPyTorch
- RDKit (via Datamol)
- NumPy
- Pandas
- Polaris (for competition data access)

## Authors

[Satya Pratik Srivastava]
