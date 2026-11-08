# Spec: reddit.py

## Goal and user
A cleaned dataset and about three visualizations.

## Input
`reddit.ndjson` 

## Output
`redditclean.ndjson`: all original columns, plus `sentiment` `agency`.

## Rules

Sentiment categorization

The added column, `sentiment`, specifies whether content in `text_post` carries either `subliminal` or `overt` hostility.
- `subliminal`: overlooked, indirect, or normalized remarks, jokes, stereotypes
- `overt`: blatant, explicit, or offensive remarks, threats, generalizations
- `unremarkable`: unclear sentiment within post
Observations marked as `unremarkable` are dropped.

The added column, `agency`, denotes whether `subreddit` value matches either `subliminal` or `overt` hostility.
- `subliminal`: captures the `subreddit` values of `incels`, `mgtow`, `love_shy`, `rooshv`, and `avfm`
- `overt`: captures `red_pill_talk`, `pua_forum`, and `the_attraction`

## Acceptance criteria

## Performance budget

## Out of scope

## Open questions
