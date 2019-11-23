# **Work in Progress**

# mkmlproject

Command-line utility that creates flexible ML project structure - with directories and files.

It can also create notebooks from templates for predefined pipelines with updated data.


## Directory Structure
- Create organized ML project structure
- Useful for sharing data science work
- Intended as a good starting point for ML projects, but can be modified using the ```structure.json``` (To do)
- You will thank yourself, read why [below](#Why-do-we-need-Project-Structure)

From PEP 8:
> Consistency within a project is more important. Consistency within one module or function is the most important.... However, know when to be inconsistent -- sometimes style guide recommendations just aren't applicable. When in doubt, use your best judgment. Look at other examples and decide what looks best. And don't hesitate to ask!


## Notebook Template rendering
- Create new baseline notebooks from templates
- Add cells to existing notebooks from templates
- Change the template variable from corresponding yaml files (To do)
- Predefined templates of simple data extraction and baseline notebooks frequently used models (To do)


## Usage

```
import mkmlproject
mkmlproject create -d 'home_dir' 'Project Name'
mkmlproject render -t 'Template File' -o 'Output Notebook' -d 'Output Location'
mkmlproject config # change default project dir structure and details
```

----

# Why do we need Project Structure

Ever tried to reproduce an analysis that you did a few months ago or even a few years ago? You may have written the code, but it's now impossible to decipher whether you should use ```make_figures.py.old, make_figures_working.py or new_make_figures01.py``` to get things done. Here are some questions we've learned to ask with a sense of existential dread:

- Are we supposed to go in and join the column X to the data before we get started or did that come from one of the notebooks?
- Come to think of it, which notebook do we have to run first before running the plotting code: was it "process data" or "clean data"?
- Where did the shapefiles get downloaded from for the geographic plots?
- Et cetera, times infinity.

These types of questions are painful and are symptoms of a disorganized project. A good project structure encourages practices that make it easier to come back to old work, for example separation of concerns, abstracting analysis as a DAG, and engineering best practices like version control.

----

A well-defined, standard project structure means that a newcomer can begin to understand an analysis without digging in to extensive documentation. It also means that they don't necessarily have to read 100% of the code before knowing where to look for very specific things.

Well organized code tends to be self-documenting in that the organization itself provides context for your code without much overhead. People will thank you for this because they can:

- Collaborate more easily with you on this analysis
- Learn from your analysis about the process and the domain
- Feel confident in the conclusions at which the analysis arrives


An example of this is the Filesystem Hierarchy Standard for Unix-like systems. The /etc directory has a very specific purpose, as does the /tmp folder, and everybody (more or less) agrees to honor that social contract. That means a Red Hat user and an Ubuntu user both know roughly where to look for certain types of files, even when using each other's system — or any other standards-compliant system for that matter!

Ideally, that's how it should be when a colleague opens up your ML project.

You can read more about it [here](http://drivendata.github.io/cookiecutter-data-science/). This project is inspired from [Github Repo](https://github.com/cookiecutter/cookiecutter)


---

### Current project structure that will be created

```
├── data
│   ├── [external]     <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
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
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
├── README.md          <- The top-level README for developers using this project.

```
