# README

[![DOI](https://zenodo.org/badge/164007006.svg)](https://zenodo.org/badge/latestdoi/164007006)

This artifact contains the data and code used in the paper _Analysis and Detection of Information Types ofOpen Source Software Issue Discussions_.

It comprises of three main folders: _data_, _experiments_ and _results_. The components of which are as follows:

1. **_data_**: This folder contains all the data utilized in the experiments performed.
  * **chosen_issues** - contains the comments of the chosen 15 OSS project issue discussion, retrieved from the Github API, in json format
  * **Codebook.xlsx** - the codebook to classify a sentence into a particular information type
  * **Corpus.xlsx** - the list annotated sentences and their corresponding conversational feature set.
 * **annotated\_data\_with_metadata.xlsx** - this is the file exported from _Atlas.ti_ annotation tool. It is the list of annotated sentences, along with meta information provided by the tool. Additionally, it contains phrases of comment _created at_ and _author_ annotated as _METADATA_ for the purpose of extracting conversational features.
  * **all_data.pkl** - is a pickle file containing a pandas dataframe of similar information to *Corpus.xlsx*. It contains the annotated sentences along with their conversational feature set. It also contains the document in which the sentence exists.
  * **data\_by_document.pkl** - this contains the same information as _all\_data.pkl_. The only difference is that it is a dictionary with keys as documents and values as the pandas dataframe of sentence information.

2. **_experiments_**: This folder contains all the code used to perform the experiments presented in the paper.
  * **preprocess.ipynb** - is the first step. It reads the annotations from the xlsx file exported from _Atlas.ti_ and extracts all conversational feature information of each sentence and stores it in *all\_data.pkl* and *data\_by_document.pkl*.
  * **transform_features.ipynb** - performs transformation on the conversational features such as converting categorical columns to one-hot-encoding and converting datetime features to numerically comparable values
  * **logistic_regression/random_forest** - these folders contain each of the experiments presented in the corresponding paper.

All the files in this folder are Jupyter notebooks with the extension *.ipynb*. Each file comprises of multiple *cells* containing code. These *cells* encapsulate different steps in the flow of code to enable observation of intermediate results. More about Jupyter can be found on this [Jupyter page](https://jupyterlab.readthedocs.io/en/latest/).

3. **_results_**: Is the folder containing the results of the experiments performed.

Two additional folders exist:

1. **_docker_**: This folder contains the compressed docker image with the required environment as well as the Dockerfile used to build this image

2. **_nltk_data_**: This contains the wordnet corpus required by the code to lemmatize words

## Instructions for Reproducibility:

To set up the environment for this work, refer to the file *INSTALL.md*.

1. Run all cells, in order, in *preprocess_data.ipynb*
2. Run all cells, in order, in *transform_features.ipynb*
3. Enter into either of the algorithm folders (*logistic_regression* or *random_forest*), and run all cells (in order) of the experiment you wish to reproduce.
