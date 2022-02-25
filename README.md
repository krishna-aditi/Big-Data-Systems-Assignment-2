Big-Data-Systems-Assignment-2
==============================
### Nowcast Analysis and Design for Federal Aviation Administration.

## Submitted by:

![image](https://user-images.githubusercontent.com/37017771/153502035-dde7b1ec-5020-4505-954a-2e67528366e7.png)

**Original SEVIR repo link:** https://github.com/MIT-AI-Accelerator/neurips-2020-sevir

**Design document source link: ** https://docs.google.com/document/d/18v4oZxatRdQRcDPXCPkx4tiK8Rqo05ZPi2sFPtx3ss0/edit?usp=sharing

**CLAAT Link**: https://codelabs-preview.appspot.com/?file_id=18v4oZxatRdQRcDPXCPkx4tiK8Rqo05ZPi2sFPtx3ss0#2

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- Overview about the project
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks
    │   ├── AnalyzeSyntheticRadar.ipynb
    │   ├── AnalyzeNowcast.ipynb
    │   └── Workflow.ipynb
    |
    ├── references         <- Assignment-2 details
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │       ├── api_workflow.jpg
    │       ├── webapp_workflow.jpg
    │       └── Skeletal_UI.png
    |
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   ├── make_nowcast_dataset.py
    │   │   ├── make_synrad_dataset.py
    │   │   ├── nowcast_generator.py
    │   │   ├── synrad_generator.py
    │   │   └── utils.py
    │   │
    │   ├── display         
    │   │   ├── display.py
    │   │   └── roebber_plot.py
    |   |
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── losses         <- Scripts for loss functions
    │   │   ├── gan_losses.py
    |   |   ├── synrad_loss.py
    |   |   ├── vggloss.py
    │   │   └── style_loss.py
    |   |
    │   ├── metrics         
    │   │   ├── histogram.py
    │   │   ├── lpips_metric.py
    │   │   └── metrics.py
    |   |
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │                     predictions
    │   │
    │   ├── readers         
    │   │   ├── normalizations.py
    │   │   ├── nowcast_reader.py
    │   │   └── synrad_reader.py
    |   |
    │   ├── utils         
    │   │   ├── trainutils.py
    │   │   └── utils.py
    |   |
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>

--------
#### What is nowcasting?
“Nowcasting is a future prediction task where the model input consists of 13 VIL images sampled at 5 minute intervals. The model is trained to produce the next 12 images in the sequence corresponding to the next hour of weather. It generates high resolution, short term weather forecasts of radar echoes, precipitation, cloud coverage or other meteorological quantities widely used in public safety, air traffic control, and many other areas that require high fidelity and rapidly updating forecasts.”

#### What are VIL images? 
VIL imagery in remote sensing is basically a radar measuring cloud precipitation. It’s the integration of reflectivity within a column of air. A radar beam is released from a satellite and it it's incidence on the clouds will reflect. The wavelength of the beam is such that it reflects only on precipitation (drizzle, snow, rain, hail) and not cloud droplets or water vapor. The reflected wave is then summed over the vertical axis to give the total precipitation at a single point. The VIL measurement is usually used in determining the size of prospective hail, the potential amount of rain under a thunderstorm, and the potential downdraft strength when combined with the height of the echo tops. VIL can be used to triage storms based on their severe potential. It is sometimes still used to assess storms for their potential severity.

#### Requirements
Set up a virtual environment with the requirements stated in the requirments.txt file.

#### Downloading SEVIR
Download information and additional resources for SEVIR data are available at https://registry.opendata.aws/sevir/
```
aws s3 sync --no-sign-request s3://sevir .
```
#### Extracting training and test data
```cd src/data
# Generates nowcast training & testing datasets
python make_nowcast_dataset.py --sevir_data ../../data/sevir --sevir_catalog ../../data/CATALOG.csv --output_location ../../data/interim/
# Generate synrad training & testing datasets
python make_synrad_dataset.py --sevir_data ../../data/sevir --sevir_catalog ../../data/CATALOG.csv --output_location ../../data/interim/
```
#### Analyzing results
The project contains the analysis notebooks for SEVIR nowcasting and the suggested design to enable distribution of the package in the form of APIs, WebApp, PyPi package, Conda package, and Docker image. 
