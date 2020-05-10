# Teamwork.tf JSON API (for information about Team Fortress 2)

In case you see information on our website that you would like to access via our API, please create an issue for this.

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

JSON:

* [News](/NEWS.md)  *(news from various sources about Team Fortress 2)*
* [Creators](/CREATORS.md)  *(YouTube creators, Gamemap creators)*
* [Community Gameservers](/COMMUNITY-QUICKPLAY.md) *(gameservers, gamemodes, providers and statistics about players)*
* [Gamemap thumbnails & Statistics](/GAMEMAPS.md) *(gamemap thumbnails, images and statistics about players)*

Other endpoints:

* [Server image banner](/BANNER.md) *(embeddable images with gameserver information)*
