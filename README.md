## Clarifying psychology with large language models

Workshop at ECP 2026

By [Dirk Wulff](https://www.mpib-berlin.mpg.de/person/93374/2549)

Psychology suffers from a proliferation of constructs and measures: different scales carry the same label while measuring different things (jangle fallacies), and scales with different labels measure the same thing (jingle fallacies). This workshop shows how large language models (LLMs) can help clarify the structure of psychological constructs and measures by placing items and constructs in a shared semantic space — an approach developed in [Wulff & Mata (2025, *Nature Human Behaviour*)](https://doi.org/10.1038/s41562-024-02089-y).

The workshop consists of an introductory talk, a self-guided hands-on exercise, a joint walkthrough of the exercise, and an outlook. In the exercise, you will use a language model to extract features (embeddings) from personality items, evaluate how well the resulting item similarities predict empirically observed item correlations, visualize the structure of the item pool, and re-assign items to personality constructs.

### Schedule

09:00 - 09:45: Introduction & Q&A<br>
09:45 - 10:45: Self-guided exercise, incl. setup ([exercise.ipynb](exercise.ipynb) / [exercise.Rmd](exercise.Rmd))<br>
10:45 - 11:15: Walkthrough<br>
11:15 - 12:00: Outlook & Q&A

### Materials

- [`exercise.ipynb`](exercise.ipynb) — the exercise as a Python (Jupyter) notebook (runs locally or in Google Colab)
- [`exercise.Rmd`](exercise.Rmd) — the exercise as an R Markdown notebook (an automatically generated analog of the Python version)
- [`items.csv`](items.csv) — 300 personality items (`factor`, `construct`, `item`) from the International Personality Item Pool (IPIP)
- [`item_corrs.csv`](item_corrs.csv) — observed correlations between all item pairs, based on participant responses
- [`ipip_items.csv`](ipip_items.csv) — the full IPIP: 3,805 item–scale assignments from 36 personality inventories, for the final exercise task
- [`ClarifyingPsych_2026ECP.pdf`](ClarifyingPsych_2026ECP.pdf) — the presentation slides

### Setup

You can work through the exercise in one of three ways: **Python in the cloud (Google Colab)**, **Python (local)**, or **R (local)**. The exercise is identical in all three. No setup ahead of the workshop is required: the recommended way is Google Colab, which runs in the browser, needs no installation, and only requires a Google account. Choose one of the local options if you already have a working Python or R environment on your laptop, or to reproduce the analysis on your own machine after the workshop.

#### Option 1: Python in the cloud (Google Colab) — recommended

1. If you do not have a Google account, you will need to create one (it can be deleted after the workshop).
2. Open the notebook in Colab: [exercise.ipynb in Colab](https://colab.research.google.com/github/dwulff/ClarifyingPsych_2026ECP/blob/main/exercise.ipynb)
3. Run the first code cell: it installs the required packages and clones this repository so that the data files are available. That's it.

Note: When connecting Colab to your Google account, you need to grant all the permissions it requests — otherwise the notebook cannot run. This includes clicking "Run anyway" if Colab warns that the notebook was not authored by Google. The permissions can be revoked after the workshop in your [Google account settings](https://myaccount.google.com/connections).

For the two local options, first clone this repository (or download it as a ZIP via the green `<> Code` button and unpack it):

```
git clone https://github.com/dwulff/ClarifyingPsych_2026ECP.git
```

#### Option 2: Python (local)

1. Make sure you have Python 3.10–3.13 installed (3.14 is not yet supported by one of the dependencies).
2. Install the required packages (ideally in a fresh virtual environment):
```
cd ClarifyingPsych_2026ECP
python -m venv venv
source venv/bin/activate      # on Windows: venv\Scripts\activate
pip install -r requirements.txt
```
3. Open `exercise.ipynb` in Jupyter (`jupyter lab exercise.ipynb`) or in an IDE such as VS Code, making sure the notebook runs from within the repository folder (so that the data files are found).

#### Option 3: R (local)

The R version accesses the Python libraries `sentence-transformers` and `pacmap` from R via `reticulate` (there is no native R implementation of these libraries).

1. Make sure you have [R](https://cran.r-project.org/) (and ideally [RStudio](https://posit.co/download/rstudio-desktop/)) installed.
2. Install the required R packages:
```r
install.packages(c("reticulate", "ggplot2"))
```
3. Install the required Python packages into reticulate's environment (one-time setup; this will also install Python itself if none is found):
```r
reticulate::py_install(c("sentence-transformers", "pacmap"))
```
4. Open `exercise.Rmd` in RStudio and run the chunks.

Note: No Hugging Face account or access token is needed — all models used in the exercise are openly available.

### Resources

[Wulff & Mata (2025). Semantic embeddings reveal and address taxonomic incommensurability in psychological measurement. *Nature Human Behaviour*.](https://doi.org/10.1038/s41562-024-02089-y)

[Wulff & Mata (2025). Escaping the jingle-jangle jungle: Increasing conceptual clarity in psychology using large language models. *Current Directions in Psychological Science*.](https://doi.org/10.1177/09637214251382083)

[Hussain, Binz, Mata, & Wulff (2024). A tutorial on open-source large language models for behavioral science. *Behavior Research Methods*.](https://doi.org/10.3758/s13428-024-02455-8)

[International Personality Item Pool (IPIP)](https://ipip.ori.org/)

[The fine-tuned personality model on Hugging Face](https://huggingface.co/dwulff/mpnet-personality)
