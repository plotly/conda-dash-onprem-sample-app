## Dash On-Premise Sample App Versions 3.0.0+

<div align="center">
  <a href="https://dash.plotly.com/project-maintenance">
    <img src="https://dash.plotly.com/assets/images/maintained-by-plotly.png" width="400px" alt="Maintained by Plotly">
  </a>
</div>


This repository contains a simple Dash app that can be deployed as-is on your [Dash Deployment Server](https://plot.ly/dash/pricing/) server. This application is configured to deploy on Dash Deployment Server versions 3.0.0
and above. If you are deploying apps on an older DDS server you can clone this repository and then checkout the `dopsa-2.5` branch with:

```
git clone git@github.com:plotly/dash-on-premise-sample-app.git
cd dash-on-premise-sample-app
git checkout dopsa-2.5
```

#### Deployment Instructions

To learn more about what each of these files does and how to start from scratch, see the [Dash App Deployment Docs](https://plot.ly/dash/deployment/on-premise).

##### Required files

In order to trigger a Conda-based python deployment in Dash Enterprise, the following files should be available:

- `conda-requirements.txt`: A listing of packages to be installed via conda
- `conda-runtime.txt`: A valid miniconda runtime package name.
  - A list of valid runtimes can be fetched from the [miniconda repo](https://repo.continuum.io/miniconda/) and comes in the form of `Miniconda$VERSION`, where $VERSION is a valid Miniconda version. By way of example, both `Miniconda3-4.5.12` and `Miniconda-4.5.12` are valid contents for the `conda-runtime.txt` file.

##### Optional files

The following files will be optionally used during the deployment process:

- `.condarc`: This file will be copied into place and used by Conda as a [`.condarc` file](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/use-condarc.html). For example, alternative conda channels can be specified by setting the following as the file's contents:
    ```yaml
    channels:
      - https://anaconda-repo.example.com/conda/
    ```
- `requirements.txt`: This file will be used to install dependencies via `pip` _after_ conda-based dependencies have been installed.
- `bin/pre_compile`: An executable script that will be run before Conda is installed and executed
- `bin/post_compile`: An executable script that will be run after Conda is installed and executed

#### Authentication Instructions
Check out the following documentation for information on [privacy](https://dash.plot.ly/dash-deployment-server/privacy) and [authentication](https://dash.plot.ly/dash-deployment-server/app-authentication) settings
available for Dash applications deployed on your Dash Deployment server. Note: the `dash-auth` package is
no longer necessary with DDS 3.0.0+ and users may notice a double login if deploying apps with
`dash-auth < 1.3.0` on DDS 3.0.0 and above.
