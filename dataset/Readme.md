## Table of contents of this README:
- [A. Brief description](#a-brief-description)
- [B. Files description](#b-files-description)
- [C. Details on the collection procedure](#c-details-on-the-collection-procedure)

## A. Brief description

This corpus contains a metadata collection on sci-fi movies extracted from the [orginal dataset](../original_dataset):

- involves 631 characters from 100 movies
- movie metadata included:
	- genres
	- release year
	- IMDB rating
	- number of IMDB votes
- character metadata included:
	- gender (for 1,327 characters)

## B. Files description

In all files the field separator is a comma (","), except for in the two Excel files. The [movie_date](movie_data.xlsx) Excel file has all the other .csv files as separate sheets and also includes the analysis (results/graphs) of our paper. The [orginal_movie_dataset](orginal_movie_data.xlsx) Excel file has all the data of the [orginal dataset](../original_dataset) in seperate sheets.

- [movie_titles_scifi_chronological.csv](movie_titles_scifi_chronological.csv)
	- contains information about each movie title
	- fields: 
		- movieID, 
		- movie_title,
		- movie_year, 
	   	- IMDB_rating,
		- number_of_IMDB_votes, 
 		- genres in the format: ['genre1','genre2',�,'genreN']

- [scifi_characters.csv](scifi_characters.csv)
	- contains information about each movie character
	- fields:
		- characterID
		- character_name
		- movieID
		- movie_title
		- gender ("f" for female, "m" for male, "n" for neutral, "x" for unknown characters)

- [movie_lines.csv](movie_lines.csv)
	*this is the same as in the [orginal dataset](../original_dataset)* 
	- contains the actual text of each utterance
	- fields:
		- lineID
		- characterID (who uttered this phrase)
		- movieID
		- character_name
		- text_utterance: text of the utterance

- [movie_convos_scifi.csv](movie_convos_scifi.csv)
	- the structure of the conversations
	- fields
		- characterID_1: characterID of the first character involved in the conversation
		- characterID_2: characterID of the second character involved in the conversation
		- movieID of the movie in which the conversation occurred
		- list_utterance: list of the utterances that make the conversation, in chronological 
			order: ['lineID1','lineID2',�,'lineIDN']
			has to be matched with movie_lines.csv to reconstruct the actual content

- [sum_movie_convos_scifi.csv](sum_movie_convos_scifi.csv)
	- the sum of the number of lines created using the [project notebook](project.ipynb)
	- Fields
	 	- characterID_1: characterID of the first character involved in the conversation
		- movieID of the movie in which the conversation occurred
		- sum_utterance: sum of the list of the utterances that make the conversation
		- gender
	

## C. Details on the collection procedure

We started with the [orginal dataset](../original_dataset), which we got from [Kaggle](https://www.kaggle.com/Cornell-University/movie-dialog-corpus). In order to answer our research question: *"How were female (and female coded) characters represented in Science Fiction films between the years 1970 and 2010?"* and the subquestions we needed to add more metadata for the gender, since in the [orginal dataset](../original_dataset) 66.6% was unlabeled ("?"), 22.7% male ("m"/ "M") and 10.7% female ("f"/"F"). This metadata on gender was added manually by looking at the movie scripts or finding the cast on the The Internet
 Movie Database (IMDB) website of the movie. Furthermore, we discarded all the movies without the genre "sci-fi" in the genres list column and all the movies before 1970, we were left with 100 unique titles with the metadata of 1,327 characters, IMDB ratings, no. of IMDB votes, genres and release year. Furthermore, from the [orginal dataset](../original_dataset) we discared the position on movie credits metadata, since a lot of this information was unlabeled. In addition, we cleaned up the release year data, since some of the years had: "/I" behind some years. 
 
Using simple data processing heuristics in Python (see [project notebook](project.ipynb)) we collected the sum of the number of lines (list utterances) by using the movie_convos_scifi and linking this to the characterID in [scifi_characters.csv](scifi_characters.csv), we also got the gender; all this information was put into a new spreadsheet, which is the[sum_movie_convos_scifi.csv](sum_movie_convos_scifi.csv) data. To get the amount of words (text_utterance) from [movie_lines.csv](movie_lines.csv) we matched the characterID to the [scifi_characters.csv](scifi_characters.csv) characterID to get the relevant characters and their gender. 
