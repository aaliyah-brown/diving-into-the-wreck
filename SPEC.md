# Spec: reddit.py

## Goal and user
A cleaned dataset and about three visualizations.

## Input
`reddit.ndjson` 

## Output
`redditclean.ndjson`: all original columns, plus `sentiment` and `agency`.

## Rules

Sentiment categorization

The added column, `sentiment`, specifies whether content in `text_post` carries either `subliminal` or `overt` hostility.
- `subliminal`: overlooked, indirect, or normalized remarks, jokes, stereotypes
- `overt`: blatant, explicit, or offensive remarks, threats, generalizations
- `unremarkable`: unclear sentiment within post

The added column, `agency`, denotes whether `subreddit` value matches either `subliminal` or `overt` hostility.
- `subliminal`: captures the `subreddit` values of `incels`, `mgtow`, `love_shy`, `rooshv`, and `avfm`
- `overt`: captures `red_pill_talk`, `pua_forum`, and `the_attraction`

Missing values
- Duplicate values of `id_post` dropped
- `NaN` and `unremarkable` values of `sentiment` dropped

## Acceptance criteria

## Performance budget

## Out of scope

## Open questions
