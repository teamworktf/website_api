# News articles from Team Fortress 2 websites

Retrieve news articles from Team Fortress 2 related websites. [Prerequistes for using this API](https://github.com/teamworktf/website_api).

## List latest articles

Get an overview of the last 20 news items posted. All these news items are also displayed on the site at [news](https://teamwork.tf/news).

```
https://teamwork.tf/api/v1/news?key=YOUR_API_KEY
```

Pagination is also supported, you can append `&page=2` to the URL to request older articles.

Searching for specific news providers is also possible, you can append `&provider=NAME` to the URL to request only articles from this provider. For a list of all providers, please view the [news](https://teamwork.tf/news) page.

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
]
```

## Retrieve specific article

Get a specific news article. Note that we do not store the contents of a news article.

```
https://teamwork.tf/api/v1/news/hash/{hash}?key=YOUR_API_KEY
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
