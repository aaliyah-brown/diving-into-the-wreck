# Spec: reddit.py

## Goal and user
The program examines forum posts within the Reddit manosphere. Each post will be classified into an agency level depending on the subcommunity in which it lives. Then, each post will be labeled as subliminally harmful or overtly threatening. The main focus is to accurately perform sentiment analysis by identifying keywords and key phrases that signal uniquely unequivocal connotations. 

## Input
`reddit.ndjson` 

## Output
`redditclean.ndjson`: all original columns, plus `sentiment` and `agency`.
A cleaned dataset and comparison displays to better contextualize the Reddit manosphere.

## Rules
1. Sentiment categorization

The added column, `sentiment`, specifies whether content in `text_post` carries either `subliminal` or `overt` hostility.
- `subliminal`: overlooked, indirect, or normalized remarks, jokes, stereotypes
- `overt`: blatant, explicit, or offensive remarks, threats, generalizations
- `unremarkable`: unclear sentiment within post
- `neither`: no definite attitude

The added column, `agency`, denotes whether `subreddit` value matches either `subliminal` or `overt` hostility.
- `subliminal`: captures the `subreddit` values of `incels`, `mgtow`, `love_shy`, `rooshv`, and `avfm`
- `overt`: captures `red_pill_talk`, `pua_forum`, and `the_attraction`

2. Classification process \\
To build `sentiment` column:

### 2. Classification Process

To build `sentiment` column:
1. Drop missing and irrelevant observations within `text_post`.
2. Build unique lexicon dictionary of words and phrases with corresponding attitude.
3. Identify textual patterns in data set.
4. Examine accuracy of text classifier and adjust parameters accordingly.
  
3. Missing values
- Duplicate values of `id_post` dropped
- `NaN` and `unremarkable` values of `sentiment` dropped

## Requirements
Functional requirements:
- FR-01: Read in `reddit.ndjson` and verify presence of the fields `text_post`, `author`, and `subreddit`.
- FR 02: Prepare data by deriving new variables and removing duplicate, missing, or ambiguous text content.
- FR-03: Peruse lexicon within each value of `text_post`, match lexicon to corresponding sentiment class, and display results. 

Non-functional requirements:
- NFR-01: Read in `reddit.ndjson` within ten minutes and return an error message for ingestion failure.
- NFR-02: Preserve each value of `text_post` so that raw data is unchanged throughout data analysis.
- NFR-03: Honor anonymity of each identifier of `user_id` and `author` and conceal user information from analysis.
   
## Performance budget
All 12.79 GB of data may not exceed available system memory. 

## In scope
- Information only within `reddit.ndjson`.
- Cleaned Reddit data for usability and clarity. 
- Sentiment analysis only for`text_posts`.
- Comparison of aggregate, not individual user, findings.

## Out of scope
- Finding correlation of Reddit usage to real-world violence. 
- Proving causation between Reddit activity and real-world violence. 
- Determining motives, characteristics, or true identities of individual users. 
- Tracking live updates or edits made to existing text posts. 
- Comparing individual Reddit users against other individuals.
