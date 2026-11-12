# Spec: reddit.py

## Goal and user
A cleaned dataset and comparison displays to better contextualize the Reddit manosphere.

## Input
`reddit.ndjson` 

## Output
`redditclean.ndjson`: all original columns, plus `sentiment` and `agency`.

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

## Acceptance criteria
1. Testable Criteria
- Data processed in row increments without fully loading into RAM.
- All 12.79 GB of original data in `reddit.ndjson` read in as NDJSON file without error.
- All changes to data appended to `redditclean.ndjson` and original dataset left unchanged.
- Each observation within `redditclean.ndjson` has valid value for `sentiment`, `agency`, `subreddit`, and `text_post`.
- No duplicates of `id_post` column.

2. Batch Processing
- Primary data-reading packages are `json`, `pandas `, `DuckDB`, and `[scikit-learn]([(https://scikit-learn.org/stable/auto_examples/semi_supervised/plot_semi_supervised_newsgroups.html)])`.
- Data initially processed in batches of 1000 observations.
- Each batch thereafter tested at sizes 5,000, 10,000, 25,000, and 50,000.
- Processing time and peak memory usage recorded for each batch.
- Final batch size determined based on all recorded values of memory usage.
- Optimal batch size occurs where memory usage allows for consistent and quick processing speed.
   
## Performance budget
All 12.79 GB of data may not exceed available system memory. 

## Out of scope
Data will not include information beyond `reddit.ndjson`. Program will not perform more than categorization and analysis of data.

## Open questions
