# dfr_lq

Code used to generate LDA topic models analyzed in the article, “Computational Topic Models of the *Library Quarterly* (1931-2015). 

## Data access
Metadata and unigrams for 8,808 items from the *Library Quarterly* (LQ) were retrieved from JSTOR's Data for Research (DfR) platform using the query, *jcode:libraryq*. Each article from the journal is represented in the DfR download via:
1. an XML file with metadata for each article and 
2. a tab-delimited TXT file listing the ngrams for each article.

As of Fall 2020 JSTOR has plans to sunset the DfR platform, but its function has already been migrated to the [Digital Scholar Workbench website](https://tdm-pilot.org/). Researchers seeking to replicate the topic models can reach out to the authors for access to the underlying data.

## Using this code

The code used to import and analyze the LQ data is available in four IPython notebooks in this repository, each of which are explained in greater depth below: 1_import_r.ipynb, 2_clean.ipynb, 3_lda_models.ipynb, and 4_tm_analysis.ipynb.

### Set-up
To execute the code in the Jupyter notebooks in this repository on your own, we recommend first 
reading and following our [setup instructions](setup.md), especially if the goal in
doing so is to replicate our results.

### Data import, cleaning and analysis
1. [1_import_r.ipynb](https://github.com/chennesy/dfr_lq/blob/master/1_import_r.ipynb) - Thomas Klebel’s [jstor package](https://docs.ropensci.org/jstor/) for the programming language R (2018) was leveraged to reformat the metadata XML files into a single CSV file containing key metadata for the entire corpus. 
2. [2_clean.ipynb](https://github.com/chennesy/dfr_lq/blob/master/2_clean.ipynb) - The metadata was then imported into Python and combined with the ngrams for each article. To prepare the corpus for topic modeling, the words in the ngram files were stemmed using the Natural Language Toolkit’s Snowball Stemmer (Bird, Loper, and Klein 2009). 
3. [3_lda_models.ipynb](https://github.com/chennesy/dfr_lq/blob/master/3_lda_models.ipynb) - This notebook may be skipped for purposes of replicability. It used scikit-learn's GridSearchCV from the model_selection module to find the “best performing” model and parameters, including the number of topics (40) that were ultimately applied to the LQ corpus. 
4. [4_tm_analysis.ipynb](https://github.com/chennesy/dfr_lq/blob/master/4_tm_analysis.ipynb) - Used to generate and analyze the topic model. See the article and supplemental appendix for more information. 

## Suggested citation (forthcoming)
Hennesy, C. & Naughton, D. (2022). Computational Topic Models of the *Library Quarterly* (1931-2015). *portal: Libraries & the Academy* 22(2).
