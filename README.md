# 4-parameter model of modified recombination (4-modrec)

This repository provides a modified version of the cosmology code [CAMB](https://github.com/cmbant/CAMB) implementing the four-parameter model of modified recombination, **4-modrec**.

## Model

We consider a phenomenological four-parameter model to modify the redshift evolution of the ionized fraction $x_e(z)$, hereafter denoted by `4-modrec`. This model is motivated by recombination histories obtained from magnetohydrodynamic simulations in the presence of primordial magnetic fields (PMF), and is used here as a flexible parametrization of departures from the standard ionization history. It is given by

$$
x_e(z) = x_e^{(0)}(z - \Delta z_{\mathrm{shift}}) \left\lbrace 1 + A_{\mathrm{b}}  \mathrm{exp} \left[ - \frac{(z - z_{\mathrm{b}})^2}{2 \sigma_{\mathrm b}^2} \right] \right\rbrace,
$$

where, for a given set of cosmological parameters, $x_e^{(0)}$ is the output of the standard recombination model implemented in `RECFAST`.

The four parameters are:

| Code parameter | Description |
| --- | --- |
| `zref` | Reference redshift $z_{\mathrm b}$ at which the Gaussian-shaped bump is centered. |
| `amds` | Amplitude $A_{\mathrm b}$ of the Gaussian-shaped bump. |
| `sigw` | Width $\sigma_{\mathrm b}$ of the Gaussian-shaped bump. |
| `dzin` | Overall shift of the unmodified ionization history in redshift, quantified by $\Delta z_{\mathrm{shift}}$. |

The flat $\Lambda$CDM limit is recovered for $A_{\mathrm b}=0$ and $\Delta z_{\mathrm{shift}}=0$, with $z_{\mathrm b}$ and $\sigma_{\mathrm b}$ then becoming irrelevant.

## Installation

Clone the repository and build the provided modified CAMB:

```bash
git clone --recursive https://github.com/hamidmirpoorian/4modrec.git
cd 4modrec/CAMB
python setup.py build
```

## Running with Cobaya

The repository includes [planck_pplusmb_bao_4mod.yaml](planck_pplusmb_bao_4mod.yaml), an example MCMC configuration. Set `theory.camb.path` in the YAML to the absolute path of your cloned `CAMB` directory.

From the repository root, test initialization with Cobaya:

```bash
cobaya-run --test planck_pplusmb_bao_4mod.yaml
```

## Citation and acknowledgements

If you use this model, please cite:

- S. H. Mirpoorian, K. Jedamzik, and L. Pogosian, **Modified recombination and the Hubble tension**, *Phys. Rev. D* **111**, 083519 (2025). [arXiv:2411.16678](https://arxiv.org/abs/2411.16678) · [DOI](https://doi.org/10.1103/PhysRevD.111.083519)
- S. H. Mirpoorian, K. Jedamzik, and L. Pogosian, **Is dynamical dark energy necessary? DESI BAO and modified recombination**, *JCAP* **12**, 050 (2025). [arXiv:2504.15274](https://arxiv.org/abs/2504.15274) · [DOI](https://doi.org/10.1088/1475-7516/2025/12/050)
