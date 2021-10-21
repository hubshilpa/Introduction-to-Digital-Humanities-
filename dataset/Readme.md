## Table of contents of this README:
- [A) Brief description](a--brief-description)
- [B) Files description](b--files-description)
- [C) Details on the collection procedure](c--details-on-the-collection-procedure)

## A) Brief description

This corpus contains a metadata collection of fictional conversations on sci-fi movies extracted from the [orginal dataset](../original_dataset):

- 220,579 conversational exchanges between 10,292 pairs of movie characters **CHANGE**
- involves 631 characters from 100 movies
- in total 304,713 utterances **CHANGE**
- movie metadata included:
	- genres
	- release year
	- IMDB rating
	- number of IMDB votes
- character metadata included:
	- gender (for 1,327 characters)

## B) Files description

In all files the field separator is a comma (",")

- movie_titles_metadata.txt **CHANGE**
	- contains information about each movie title
	- fields: 
		- movieID, 
		- movie title,
		- movie year, 
	   	- IMDB rating,
		- no. IMDB votes,
 		- genres in the format ['genre1','genre2',�,'genreN']

- scifi_characters.csv
	- contains information about each movie character
	- fields:
		- characterID
		- character_name
		- movieID
		- movie_title
		- gender ("f" for female, "m" for male, "n" for neutral, "x" for unknown characters)

- movie_lines.csv: this is the same as in the [orginal dataset](../original_dataset). 
	- contains the actual text of each utterance
	- fields:
		- lineID
		- characterID (who uttered this phrase)
		- movieID
		- character_name
		- text_utterance: text of the utterance

- movie_convos_scifi.csv
	- the structure of the conversations
	- fields
		- characterID of the first character involved in the conversation
		- characterID of the second character involved in the conversation
		- movieID of the movie in which the conversation occurred
		- list of the utterances that make the conversation, in chronological 
			order: ['lineID1','lineID2',�,'lineIDN']
			has to be matched with movie_lines.csv to reconstruct the actual content

- sum_movie_convos_scifi.csv
	- the sum of the number of lines created using the [project notebook](project.ipynb)
	- Fields
	 	- characterID of the first character involved in the conversation
		- movieID of the movie in which the conversation occurred
		- sum_utterance: sum of the list of the utterances that make the conversation
		- gender
	

## C) Details on the collection procedure

We started with the [orginal dataset](../original_dataset), which we got from [Kaggle](https://www.kaggle.com/Cornell-University/movie-dialog-corpus). In order to answer our research question: "How were female (and female coded) characters represented in Science Fiction films between the years 1970 and 2010?" and the subquestions we needed to add more metadata for the gender, since in the [orginal dataset](../original_dataset) 66.6% was unlabeled ("?"), 22.7% male ("m"/ "M") and 10.7% female ("f"/"F"). This metadata on gender was added manually by looking at the movie scripts or finding the cast on the The Internet
 Movie Database (IMDB) website of the movie. Furthermore, we discarded all the movies without the genre "sci-fi" in the genres list column and all the movies before 1970, we were left with 107 unique titles with the metadata of 1,327 characters, IMDB ratings, no. of IMDB votes, genres and release year. Furthermore, from the [orginal dataset](../original_dataset) we discared the position on movie credits metadata, since a lot of this information was unlabeled. 
 
 Using simple data processing heuristics in Python (see [project notebook](project.ipynb)) we collected the sum of the number of lines (list utterances) by using the movie_convos_scifi and linking this to the characterID in scifi_characters.csv ..


After discarding all movies that could not be matched or that had less than 5 IMDB 
votes, we were left with 617 unique titles with metadata including genre, release 
year, IMDB rating and no. of IMDB votes and cast distribution.  We then identified 
the pairs of characters that interact and separated their conversations automatically 
using simple data processing heuristics. After discarding all pairs that exchanged 
less than 5 conversational exchanges there were 10,292 left, exchanging 220,579 
conversational exchanges (304,713 utterances).  After automatically matching the names 
of the 9,035 involved characters to the list of cast distribution, we used the 
gender of each interpreting actor to infer the fictional gender of a subset of 
3,321 movie characters (we raised the number of gendered 3,774 characters through
 manual annotation). Similarly, we collected the end credit position of a subset 
of 3,321 characters as a proxy for their status.
