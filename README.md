# Hubble Diagram with Type Ia Supernovae

Analysis of Type Ia supernova observations to construct and model the Hubble diagram, estimate the Hubble constant at low redshift, and compare empirical luminosity distances with linear, nonlinear, and FLRW cosmological models.

## Overview

This project uses observations of Type Ia supernovae to investigate the relationship between redshift and luminosity distance.

The analysis starts from distance modulus and redshift measurements and progressively compares different descriptions of the Hubble relation. At low redshift, the relationship is approximated as linear, while higher-redshift observations are used to investigate deviations from this approximation.

The notebook also calculates luminosity distances using an FLRW cosmological model and compares these theoretical values with the empirical distances obtained from the supernova data.

## Analysis

The notebook performs the following steps:

1. **Load and organize the supernova data**

   * Supernova identifier
   * Redshift
   * Distance modulus
   * Distance modulus uncertainty
   * Probability associated with a low-mass host galaxy

2. **Convert distance modulus to luminosity distance**

   The observed distance modulus is converted to luminosity distance in Mpc.

3. **Construct the empirical Hubble relation**

   The relationship between redshift and luminosity distance is visualized and fitted using linear regression.

4. **Investigate the low-redshift regime**

   A subset of five low-redshift supernovae is used to estimate the Hubble constant from the relation

   ```text
   H₀ ≈ cz / dL
   ```

5. **Compare linear and nonlinear models**

   The notebook evaluates a linear approximation and a nonlinear expression for luminosity distance as a function of redshift. The nonlinear model introduces a deceleration parameter `q`.

6. **Calculate FLRW luminosity distances**

   Luminosity distances are calculated using an FLRW cosmological model with:

   * `H₀ = 70`
   * `Ωₘ = 0.3`

   The resulting theoretical distances are compared with the empirical supernova distances.

7. **Visualize the Hubble diagram**

   The resulting relationships and fitted models are plotted to examine how well each approximation describes the observations.

## Data

The analysis uses a dataset containing **579 Type Ia supernovae**.

The original dataset contains the following variables:

| Variable                      | Description                                        |
| ----------------------------- | -------------------------------------------------- |
| `Supernova Name`              | Supernova identifier                               |
| `Redshift`                    | Measured redshift                                  |
| `Distance Modulus`            | Distance modulus                                   |
| `Distance Modulus Error`      | Uncertainty in the distance modulus                |
| `Low mass galaxy probability` | Probability associated with a low-mass host galaxy |

The notebook expects the data to be available as:

```text
data.txt
```

with tab-separated columns.

## Methods

### Luminosity Distance

The distance modulus is converted to luminosity distance in megaparsecs:

```python
10**(((mu + 5) / 5) - 6)
```

where `mu` is the distance modulus.

### Linear Model

A linear regression is used to model the relationship between redshift and luminosity distance:

```python
LinearRegression()
```

The linear approximation is particularly relevant in the low-redshift regime.

### Nonlinear Model

The notebook also fits the nonlinear relation:

```text
dL(z) = (cz/H₀) [1 + (1-q)z/2]
```

where:

* `c` is the speed of light;
* `H₀` is the Hubble constant;
* `q` is the deceleration parameter.

The parameter `q` is estimated using `scipy.optimize.curve_fit`.

### FLRW Model

The notebook calculates luminosity distance using an FLRW cosmological model with:

```text
H₀ = 70
Ωₘ = 0.3
```

The corresponding distance is obtained through numerical integration of the cosmological expansion relation and multiplication by `(1 + z)`.

The resulting FLRW luminosity distances are then compared with the empirical distances derived from the supernova observations.

## Technologies

The analysis is implemented in Python using:

* **Pandas** — data manipulation
* **NumPy** — numerical computation
* **Matplotlib** — visualization
* **SciPy** — numerical integration and nonlinear parameter fitting
* **scikit-learn** — linear regression

## Repository Structure

```text
hubble_graphics_for_type_one_a_supernovas/
├── README.md
└── Gráfico_de_Hubble_usando_supernovas_Tipo_1a.ipynb
```

The main notebook contains the complete analysis, including data processing, model fitting, calculations, and visualizations.

## Running the Notebook

The notebook was developed in Google Colab and includes a Colab integration link.

To run it locally:

```bash
pip install pandas numpy matplotlib scipy scikit-learn
```

Then open:

```text
hubble_diagram_ia_supernova.ipynb
```

Make sure that `data.txt` is available in the notebook's working directory.

Alternatively, the notebook can be opened directly in Google Colab.

## Results

The analysis demonstrates the transition from the approximately linear Hubble relation at low redshift to increasingly important nonlinear effects at higher redshift.

The notebook compares:

* observed luminosity distances;
* linear estimates;
* nonlinear estimates;
* luminosity distances calculated from an FLRW model.

It also provides an estimate of the Hubble constant using the low-redshift supernova subset.

The numerical results and corresponding plots are contained in the Jupyter notebook.
