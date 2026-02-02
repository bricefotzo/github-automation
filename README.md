# Github automation
![](https://komarev.com/ghpvc/?username=bricefotzo&color=brightgreen&label=Views) <br>
In this repository I'm using python to automate the github taks. As I often use github to host and manage versions of my projects, I found it useful to automate some tasks like add, commit push or even create and [delete](https://bricefotzo.medium.com/how-to-delete-many-git-repositories-at-once-fe4e9ed61751) repositories. 

### Requirements to use this template:
-----------
 - Git ([Install Git](https://git-scm.com/downloads) if it's not already done)
 - Python 3 ([Install Python](https://www.python.org/downloads/) if it's not already done)
 - Cookiecutter Python Package >= 1.4.0 ([Install Cookiecutter](http://cookiecutter.readthedocs.org/en/latest/installation.html) if it's not already done)  
 - [NEW] - [Install uv](https://docs.astral.sh/uv/getting-started/installation/)

## Setup your environment

1. Get the code
``` bash
git clone https://github.com/bricefotzo/github-automation.git
```
2. Install dependencies with uv
``` bash
uv sync
```


## Automate add, commit and push 
> We'll use the file [add-commit-push.py](https://github.com/BriceFotzo/github-automation/blob/master/add-commit-push.py). <br>

As those 3 commands can be used frequently (daily,hourly or after finishing some tasks), I made a little trick to reduce them to one line. 
I just have to run the following command:
``` bash
uv run add-commit-push.py --commit 'Type your commit message'
```
## Automate the deletion 
> We'll use the file [delete_repos.py](https://github.com/BriceFotzo/github-automation/blob/master/delete_repos.py). <br>

I often want to delete repositories(often many at once), so I wrapped the process in the delete_repos.py. Find more details in this [medium article](https://bricefotzo.medium.com/how-to-delete-many-git-repositories-at-once-fe4e9ed61751).
To delete repositories, you just have to run this:
``` bash
uv run delete_repos.py
```
## Automate the creation
> We'lle use the file [create_repo.py](https://github.com/BriceFotzo/github-automation/blob/master/create_repo.py) and some functions in [utils.py](https://github.com/BriceFotzo/github-automation/blob/master/utils.py).
<br>

When starting a new project, it's important to have a clean and user friendly structure to share it with colleagues. As I work in data science, I use the [cookiecutter data science structure](https://drivendata.github.io/cookiecutter-data-science/). It's _a logical, reasonably standardized, but flexible project structure for doing and sharing data science work._ accoding to the contributors.

>You can find other types of cookiecutter templates following this [link](https://github.com/topics/cookiecutter-template).

### Setting up your github projects environment

**Step 1** - Create a workspace for your projects
``` bash
mkdir my-data-science-projects
```
**Step 2** - Clone this repository and set the environment
``` bash
git clone https://github.com/BriceFotzo/github-automation
```
**Step 3** - Navigate to the repository and create a .env file to set environment variables
``` bash
cd github-automation
touch .env
```
**Step 4** - In the .env file, set those variables:

>GITHUB_USER = '{username}' <br>
>GITHUB_API = "https://api.github.com"<br>
>GITHUB_TOKEN='ghp_XXXXXXXXXXXXXXXXXXXXXXX'<br>
>GITHUB_URL='https://github.com/{username}'

### Starting a new project 

Every time you'll start a new project, follow those steps:
Navigate first to your **data science projects** folder.
``` bash
cd my-data-science-projects
```
Then run the following command to setup a new project with (project name, project repository name, your name, a license and a python version)
``` bash
uv run create_repo.py
```
Follow the instructions to setup your repostiory. Both local and online repositories will be created.
You can then start developping.
Don't forget to add, commit and push changes every day or every important change (mainly when your code works!)

### The resulting directory structure
------------

The directory structure of your new project looks like this: 

```
├── LICENSE
├── Makefile           <- Makefile with commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default Sphinx project; see sphinx-doc.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
├── src                <- Source code for use in this project.
│   ├── __init__.py    <- Makes src a Python module
│   │
│   ├── data           <- Scripts to download or generate data
│   │   └── make_dataset.py
│   │
│   ├── features       <- Scripts to turn raw data into features for modeling
│   │   └── build_features.py
│   │
│   ├── models         <- Scripts to train models and then use trained models to make
│   │   │                 predictions
│   │   ├── predict_model.py
│   │   └── train_model.py
│   │
│   └── visualization  <- Scripts to create exploratory and results oriented visualizations
│       └── visualize.py
│
└── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io
```



