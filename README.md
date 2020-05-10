In case you see information on our website that you would like to access via our API, please create an issue for this.

# Using our JSON API

## Prerequisites

For all JSON requests you need an API key. This can be requested via [settings](https://teamwork.tf/settings) under "optional settings". If an error occures you will receive the following JSON message:

```json
{
    "error": "ERROR_CODE"
}
```

## Rate limit

Our API has a rate limit of max 30 requests a minute. If you exceed this limit, your API key will be banned for 10 minutes.

## Endpoint overview

* [News](#news)
* [Community Quickplay](#community-quickplay)
* [Community Provider](#community-provider)
* [Competitive Provider](#competitive-provider)
* [Map thumbnails & Statisitics](#map-thumbnails--statistics)
* [Custom serverlists](#custom-serverlists)

