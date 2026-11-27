<h1 align="center">Fit DTI</h1>

<p align="center">
  Fits the diffusion tensor to DWI within a brain mask with DIPY (dipy_fit_dti, weighted least squares) and outputs FA, MD, RD, AD and other DTI maps.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/bl.app.60"><img src="https://img.shields.io/badge/Brainlife-bl.app.60-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-see_LICENSE-lightgrey.svg" alt="License"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Fits the diffusion tensor to DWI within a brain mask with DIPY (dipy_fit_dti, weighted least squares) and outputs FA, MD, RD, AD and other DTI maps.**

Runs dipy_fit_dti (DIPY 1.1.1) on a DWI with its bvals, bvecs and a brain mask. Use it to compute standard DTI scalar maps for tract profiling or group analyses. Needs a brain mask aligned to the DWI; b0_threshold sets which volumes count as b=0.

| | |
|---|---|
| **Inputs** | `neuro/dwi` · `neuro/mask` |
| **Outputs** | `neuro/tensor` |
| **Container** | `brainlife/dipy:1.1.1` |
| **Resources** | 8 CPUs |
| **Run it** | [doi.org/10.25663/bl.app.60](https://doi.org/10.25663/bl.app.60) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `dwi` | `neuro/dwi` | yes | DWI image with bvals and bvecs. |
| `mask` | `neuro/mask` (brain) | yes | Brain mask in the same space as the DWI; the tensor is fitted only inside it. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `output` | `neuro/tensor` | DTI maps written by dipy_fit_dti (tensor, FA, MD, RD, AD, colour FA and related maps). |

<details>
<summary><b>Parameters</b> (2)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `b0_threshold` | number | `50` | Threshold used to find b=0 directions |
| `bvecs_tol` | number | `0.01` | Threshold used to check that norm(bvec) = 1 +/- bvecs_tolb-vectors are unit vectors |

</details>

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/bl.app.60](https://doi.org/10.25663/bl.app.60), choose `neuro/dwi`, `neuro/mask` from your project, set the parameters and press **Execute**. The results are saved to your project as `neuro/tensor`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `brainlife/dipy:1.1.1`), [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "bvals": "/path/to/dwi/bvals",
       "bvecs": "/path/to/dwi/bvecs",
       "dwi": "/path/to/dwi/dwi",
       "mask": "/path/to/mask/mask",
       "b0_threshold": 50,
       "bvecs_tol": 0.01
   }
   ```

3. Run `./main`.

## DIPY

- This is a Brainlife wrapper App stemming from the [`dipy_fit_dti`](https://dipy.org/documentation/latest/reference_cmd/dipy_fit_dti/) workflow.
- This single wrapper is exposed through an apps registered on [Brainlife.io](https://brainlife.io).
- More information about DIPY : [https://dipy.org/](https://dipy.org/).
- More information about the command line `dipy_fit_dti`: [Command line Reference](https://dipy.org/documentation/latest/reference_cmd/dipy_fit_dti/).

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- Fit DTI. brainlife.io App. [doi:10.25663/bl.app.60](https://doi.org/10.25663/bl.app.60)
- Garyfallidis E, et al. Dipy, a library for the analysis of diffusion MRI data. Front Neuroinform 8:8 (2014). [doi:10.3389/fninf.2014.00008](https://doi.org/10.3389/fninf.2014.00008)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

- Serge Koudoro
- Javier Ricardo Guaje Guerra

**Contributors**

- Soichi Hayashi

## Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io, which runs this App, is publicly funded by Wellcome, the U.S. National Institutes of Health and the U.S. National Science Foundation; acknowledging that support helps keep it running.</sub>

## License

See [LICENSE](LICENSE).
