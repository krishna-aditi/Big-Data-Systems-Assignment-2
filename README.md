Big-Data-Systems-Assignment-2
==============================

Nowcast Analysis for Federal Aviation Administration usecase

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
