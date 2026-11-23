## Data

`reddit.ndjson` contains thousands of Reddit posts within anti-feminist forums capturing fifty-six subreddit communities and spanning from 2005 to 2018. 
It contains twelve key-value pairs. 

The data lives on [Zenodo](https://zenodo.org/records/4007913).

A forum is a general discussion platform.
A Subreddit is community on Reddit that is united by a particular interest, hobby, ideology, or other cultural identity. Each Subreddit is moderated and subject to unique rules.
A thread is a themed conversation where Reddit community members discuss relevant ideas, reply to other comments, and upvote or downvote comments.

## Dictionary
| Key | Description | Type | Example |
|---|---|---|---|
| author | usernamae | String | artlone |
| crawled_at | date and time of extrapolation | date/time | 2019-06-24 16:07:18.594158 |
| date_post | date and time of post | date/time | Temporal analysis |
| id_post | Unique post identifier | String/Integer | 2015-11-20 20:49:46 |
| id_post_interaction | other posts quoting this post | list | [] |
| joined_author | date author joined | date/time | 2014-07-01 00:00:00 |
| links | external url within post | list | [["http","freebeacon.com","\/blog\/hillary-clinton-sting\/"]["http","freebeacon.com","\/blog\/hillary-clinton-sting\/"]] |
| messages_author | number of author's messages | integer | 47.0 |
| number_post | number of posts within thread | integer | 1 |
| resume_author | author biography | string | null |
| text_post | main text in post | string | I just thought I'd share this. It sure made me laugh: http:\/\/freebeacon.com\/blog\/hillary-clinton-sting\/  |
| thread | url for discussion | string | https:\/\/d2ec906f9aea-003845.vbulletin.net\/forum\/avfm-central\/the-avfm-lounge\/17452-prominent-grandmother |



