# **Investigating female representation in Science Fiction movies**

## Table of Contents
- [The provenance of the data](#the-provenance-of-the-data)
- [The data model used for the research questions](#the-data-model-used-for-the-research-questions)
- [The curation of the data and the choices made](#the-curation-of-the-data-and-the-choices-made)
- [The steps taken to annotate or enrich the data](#the-steps-taken-to-annotate-or-enrich-the-data)
- [Tools](#tools)

## The provenance of the data
The [orginal dataset](original_dataset) used is created by Danescu-Niculescu-Mizil & Lee (2011) and includes movie metadata. The dataset was constructed by extracting movie scripts from publicly available websites and linking these to IMDB movie data for their study on conversational adaptation mechanisms of characters in movies. 

Movies were removed from the database if a movie script was not found. The IMDB score was added to enrich the data, while movies with less than five IMDB votes were taken out of the database. Furthermore, characters with less than five conversational exchanges were removed. Metadata was added to include the gender and position in credits for the characters. 

The data is clearly labeled and organized making information regarding items like genre or character lists of a film easily accessible. Additionally the sources for materials such as the script information are provided with URLs for the source material allowing for additional verification of accuracy. 
The data is labeled by using a field separator: " +++$+++ ", whereby the description about the data in the field can be found in the files description in the [README](https://github.com/hubshilpa/Introduction-to-Digital-Humanities-/tree/main/original_dataset#readme)


## The data model used for the research questions

<p align="center">
  <img width="700" src="data_model_image.png" alt="Figure 1:  A model of the data that will be used in this research.">
</p>

## The curation of the data and the choices made

The [dataset](original_dataset) we used was downloaded from the [Kaggle](https://www.kaggle.com/Cornell-University/movie-dialog-corpus) website and put into Google Spreadsheets (see [Excel file](https://github.com/hubshilpa/Introduction-to-Digital-Humanities-/blob/main/dataset/orginal_movie_data.xlsx) to see how the spreadsheet with the orginal dataset looked like. A copy of this spreadsheet was used to enrich the data (see [the enriched dataset Excel file](https://github.com/hubshilpa/Introduction-to-Digital-Humanities-/blob/main/dataset/movie_data.xlsx). 

On the quality of the [orginal dataset](original_dataset), we thought it is unreliable. In the first place the dataset is unreliable, because of the fact that some scripts, as well as characters, seem to be randomly selected. On many occasions the scripts used for the dataset are not the ones that ended up being used for the movie. As a consequence, some prominent characters have disappeared from our data. Additionally, the characters mentioned are also not always representative of the movie’s actual main cast. Minor roles are repeatedly presented as equal to the main characters. 

Another problem is characters being mentioned twice, or even characters that are not strictly characters being included in the data, simply because they had lines like ‘audience’. Also sometimes main characters from movies were not even in the dataset, so the dataset does not show all the characters in the movie. From this dataset alone, it is therefore not possible to tell just how important each character is. This is solved by by manually removing unnecessary data. Also to make the dataset better we manually added more data on the gender metadata. 

Another issue regarding the gender is that some of them ended up being changed in the movie, whereby the raw scripts also do not include all characters listed. We have no information on the actors that portrayed the roles, because we are mainly working with the gender of the character in the scripts. The dataset is relatively unbiased, since the movie scripts and ratings available online do not require any interpretation or subjectivity.

The choices we made to answer our research question will be discussed in the next section: [The steps taken to annotate or enrich the data](#the-steps-taken-to-annotate-or-enrich-the-data).
 
## The steps taken to annotate or enrich the data
To answer our research question we need to follow the next steps. Firstly, we will need to filter on only science fiction movies. After that, we can use the movie lines metadata to examine the average amount of lines females have by comparing the list utterance by female characters to the total amount of text. IMDB ratings and average of female characters per movies is also going to be used to investigate whether movies with higher female representation receive higher or lower scores

See the [details on the collection procedure of the readme of the dataset](https://github.com/hubshilpa/Introduction-to-Digital-Humanities-/tree/main/dataset#c-details-on-the-collection-procedure) for more details. 

## Tools 
The tools used to  enrich the orginal dataset of Danescu-Niculescu-Mizil & Lee (2011) are: 
* Google Spreadsheets,  
* Python, jupyter notebook
* IMDB cast website or fan-wikis, and 
* scripts of movies 

