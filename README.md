# teamwork.tf public API

This document holds all available developer functions that available to the public. Are you interested in additional information that we might be able to provide? Make sure to [contact](http://dev.teamwork.tf/about) us!

## Banner image for gameservers

You can request two type of image banners for any (populated) TF2 gameserver. The two formats are available at:

```
https://teamwork.tf/community/quickplay/  ip:port  /550x125.png
https://teamwork.tf/community/quickplay/  ip:port  /675x125.png
```

**Example:**

[![](https://teamwork.tf/community/quickplay/74.91.127.172:27017/675x125.png)](https://teamwork.tf/community/quickplay/74.91.127.172:27017/675x125.png)

## JSON requests (API key required)

For the following requests, you need an API key. This can be requested via [settings](https://teamwork.tf/settings) under "optional settings".

### V1: News

#### overview

Get an overview of the last 20 news items posted. All these news items are also displayed on the site at [news](https://teamwork.tf/news)

```
https://teamwork.tf/api/v1/news?key=YOUR_API_KEY
```

Example result:
```json
[
    {
        "hash": "627a5ffa7d94986cccbaae96ab04c5da",
        "provider": "reddit-news",
        "type": "reddit-post",
        "title": "He was doing this the whole game - is this some new exploit?",
        "link": "https://i.redd.it/h3fedl4z4b001.jpg",
        "created_at": {
            "date": "2017-11-26 20:46:02.000000",
            "timezone_type": 3,
            "timezone": "CET"
        }
    },
    {
        "hash": "b7c21db42b885e2013406112d1ca0693",
        "provider": "kritzkast",
        "type": "yt-video",
        "title": "UGC EU Highlander Platinum Season 23 Lower Bracket Finals",
        "link": "https://www.youtube.com/watch?v=ekSuHeh-L4Y",
        "created_at": {
            "date": "2017-11-26 15:54:53.000000",
            "timezone_type": 3,
            "timezone": "CET"
        }
    },
    ...
```

#### specific article

Get a specific news article.

```
https://teamwork.tf/api/v1/news/hash/HASH_ID?key=YOUR_API_KEY
```

Example result:
```json
{
        "hash": "64d9be7afb4fcc3db8c7945fa2afdf1a",
        "provider": "ozfortress",
        "type": "blog-post",
        "title": "Suns out, Guns out!",
        "link": "http://ozfortress.com/showthread.php?t=67243&goto=newpost",
        "created_at": {
            "date": "2017-11-26 09:10:54.000000",
            "timezone_type": 3,
            "timezone": "CET"
        }
    }
```

### V1: Community Quickplay

Query specific information about community quickplay.



### V1: Community Provider

### Specific provider basic information

You can request the status of a server community.

```
https://teamwork.tf/api/v1/community/provider/PROVIDER_SLUG?key=YOUR_API_KEY
```


Example result:
```json
{
    "id": "vaticancity",
    "name": "Vatican City",
    "description": "Some description with markdown",
    "website": "http://www.the-vaticancity.com/",
    "rules_url": "",
    "steam_group_url": "https://steamcommunity.com/groups/thevaticancity",
    "location_focus": "",
    "statistics": "https://teamwork.tf/community/provider/vaticancity/stats.json",
    "image": "https://teamwork.tf/images/providers/community/vaticancity.png"
}
```

