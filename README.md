This document describes all public endpoints that are available in the **teamwork.tf API**. Are you interested in additional information that we might be able to provide? Make sure to [contact](https://teamwork.tf/about) us!

# JSON endpoints V1 (API key required)

## Prerequisites

For the following requests, you need an API key. This can be requested via [settings](https://teamwork.tf/settings) under "optional settings". If an error occures you will receive the following JSON message:

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
* [Meet your Map lobbies](#meet-your-map-lobbies)

## Community Quickplay

Query specific information about community quickplay.

### List gamemodes

List all gamemodes that is displayed on [community quickplay](https://teamwork.tf/community/quickplay).

```
https://teamwork.tf/api/v1/quickplay?key=YOUR_API_KEY
```

Example result:
```json
{
    "gamemodes_official": [
        {
            "id": "attack-defend",
            "title": "Attack/Defend",
            "desc": "Take turns capturing enemy points and stopping the enemy from capturing yours.",
            "color": "ac3e2f"
        },
        {
            "id": "ctf",
            "title": "Capture the Flag",
            "desc": "Steal the enemy's intelligence and get it back to your base!",
            "color": "329a9d"
        },
        ...
    ],
    "gamemodes_community": [
        ...
    ]
}
```

### Get a specific gamemode

Get a specific gamemode based on the `{gamemode}` identifier (updated every 5 minutes).

```
https://teamwork.tf/api/v1/quickplay/{gamemode}?key=YOUR_API_KEY
```

Example result:
```json
{
    "id": "ctf",
    "title": "Capture the Flag",
    "desc": "Steal the enemy's intelligence and get it back to your base!",
    "color": "329a9d",
    "playing": 697
}
```

### Retrieve a list of gameservers that contain a gamemode

List all gameservers from a specific gamemode (updated every 5 minutes).

```
https://teamwork.tf/api/v1/quickplay/{gamemode}/servers?key=YOUR_API_KEY
```

Example result:
```json
[
    {
        "ip": "151.80.218.92",
        "port": "27015",
        "name": "skial.com | TURBINE+ | EU 2",
        "reachable": true,
        "provider": "skial",
        "valve_secure": true,
        "map_name": "ctf_turbine",
        "map_name_thumbnail": "/images/maps/official/ctf_turbine.jpg",
        "map_name_next": "",
        "max_players": 32,
        "gamemodes": [
            "ctf"
        ],
        "gametype": "Skial,Skial.com,SkialStats,alltalk,ctf,increased_maxplayers,norespawntime,respawntimes",
        "has_password": false,
        "has_rtd": false,
        "has_randomcrits": null,
        "has_norespawntime": true,
        "has_alltalk": true
    },
    ...
]
```

## Community Provider

Retrieve information about any of the community providers, as listed on the [provider overview](https://teamwork.tf/community/providers).

### Retrieve information from a community provider

You can request the status of a server community.

```
https://teamwork.tf/api/v1/community/provider/{slug}?key=YOUR_API_KEY
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

### Retrieve statistics of a community provider

Get live player statistics about a community provider (updated every 5 minutes). Note that "servers_total" is the amount of servers that the provider added on our website, but "servers_online" is the amount of servers that we can actually reach.

```
https://teamwork.tf/api/v1/community/provider/{slug}/stats?key=YOUR_API_KEY
```

Example result:
```json
{
    "players": 604,
    "regions_with_players": {
        "Europe": 516,
        "North America": 69,
        "Oceania": 10,
        "Asia": 9
    },
    "gamemodes": [
        "trading",
        "mvm"
    ],
    "servers_online": 99,
    "servers_total": 134
}
```

### Get serverlist from a community provider

Get live serverlist from a community provider (updated every 5 minutes).

```
https://teamwork.tf/api/v1/community/provider/{slug}/servers?key=YOUR_API_KEY
```

Example result:
```json
[
    {
        "ip": "37.59.47.178",
        "port": "27016",
        "name": "Wonder.TF | Jailbreak #1",
        "reachable": true,
        "provider": "wondertf",
        "valve_secure": true,
        "sourcecbl_secure": false,
        "map_name": "jail_minecraft_dynf_v10d",
        "map_name_thumbnail": null,
        "map_name_next": "ba_space_jail_v7",
        "max_players": 33,
        "gamemodes": [
            "breakout"
        ],
        "gametype": "TF2Stats,alltalk,arena,ba,cells,dmgspread,eu,fastdl,increased_maxplayers,jail,jailbreak,jb,norespawntime,outbreak,",
        "has_password": null,
        "has_rtd": false,
        "has_randomcrits": null,
        "has_norespawntime": true,
        "has_alltalk": true
    },
    ...
]
```

## Competitive Provider

### Retrieve specific provider information

Request a specific competitive provider.

```
https://teamwork.tf/api/v1/competitive/provider/{provider}?key=YOUR_API_KEY
```

Example result:
```json
{
    "id": "ugc",
    "name": " UGC League",
    "url": "http://ugcleague.com/",
    "description": "Play tournaments for the whole World (League).",
    "color": "4a4a4a"
}
```

### Retrieve statistics from a competitive provider

Get live statistics from a competitive provider (updated every 5 minutes).

```
https://teamwork.tf/api/v1/competitive/provider/{provider}/stats?key=YOUR_API_KEY
```

Example result:
```json
{
    "id": 1047757,
    "provider": "ugc",
    "created_at": "2017-11-27 18:50:00",
    "players": 0,
    "servers_empty": 53,
    "servers_non_empty": 0
}
```

## Map thumbnails & statistics

### Search for a specific map

Search for a specific map that is being played in TF2. Lists up to 50 results, so be specific in your search.

```
https://teamwork.tf/api/v1/map-stats/search?search_term={search}&key=YOUR_API_KEY
```

Example result:
```json
[
    {
        "map_name": "plr_hightower_event"
    },
    {
        "map_name": "plr_hightower"
    },
    ...
]
```

### Get a specific map-stats

Retrieve map statistics about a certain map (updated every 5 minutes). 

* Context field can be NULL, as we do not always have screenshots for every gamemap.
* First seen field can be NULL, as we only track gamemaps since 2017 (and a lot of maps existed before that time)
* normalized_map_name is the map name, minus any version number (e.g. ctf_2fort_b2 becomes ctf_2fort)

```
https://teamwork.tf/api/v1/map-stats/map/{map_name}?key=YOUR_API_KEY
```

Example result:
```json
{
    "map": "ctf_2fort",
    "thumbnail": "https://teamwork.tf/images/maps/official/ctf_2fort.jpg",
    "first_seen": null,
    "last_seen": "2017-11-27 18:50:00",
    "all_gamemodes": [
        "ctf",
        "randomizer"
    ],
    "all_server_types": [
        "valve",
        "community",
        "competitive"
    ],
    "highest_players": 6079,
    "highest_servers": 865,
    "alltime_avg_players": "2328.5486107448",
    "alltime_avg_players_days": 180,
    "official_map": true,
    "normalized_map_name": "ctf_2fort",
    "related_maps": [
        "ctf_2fort_freak",
        "ctf_2fort_classic_space_bd2"
    ],
    "context": {
        "normalized_map_name": "ctf_2fort",
        "created_at": {
            "date": "2017-11-14 14:42:00.000000",
            "timezone_type": 3,
            "timezone": "CET"
        },
        "file_hash": "c8484f00d8b4027c3e81e8ccf0b6ddc6",
        "map_version_sampled": 4067,
        "entity_count": 4000,
        "level_overview": {
            "image": "https://teamwork.tf/images/map_context/ctf_2fort/overview_merged.jpg",
            "context": [
                {
                    "screenHeight": 1080,
                    "scale": 9,
                    "screenWidth": 1920
                },
                {
                    "y": 0,
                    "x": -172.20995,
                    "z": 1552.0601
                }
            ]
        },
        "screenshots": [
            "https://teamwork.tf/images/map_context/ctf_2fort/spectator_0.jpg",
            "https://teamwork.tf/images/map_context/ctf_2fort/spectator_1.jpg"
        ],
        "elo_rating_best": 6
    }
}
```

### Get an image thumbnail for a map

Get an thumbnail URL for a given map. Note that image size/format depends on the source of the thumbnail. As a rule of thumb, you can expect the image size to be at least 512x286 pixels. If you query for an unknown map, or a map without a thumbnail we will respond with an error JSON object (as shown above).

```
https://teamwork.tf/api/v1/map-stats/mapthumbnail/{map_name}?key=YOUR_API_KEY
```

Example result:
```json
{
    "thumbnail": "https://teamwork.tf/images/maps/official/ctf_2fort.jpg"
}
```

### Get image context for a map

Get a list of images about the map. Depending on the map, the fields "screenshots" and "leveloverview" might be null.

```
https://teamwork.tf/api/v1/map-stats/mapimages/{map_name}?key=YOUR_API_KEY
```

Example result:
```json
{
    "thumbnail": "https://teamwork.tf/images/maps/official/ctf_2fort.jpg",
    "screenshots": [
        "https://teamwork.tf/images/map_context/ctf_2fort/spectator_0.jpg",
        "https://teamwork.tf/images/map_context/ctf_2fort/spectator_1.jpg",
        "https://teamwork.tf/images/map_context/ctf_2fort/spectator_2.jpg",
        "https://teamwork.tf/images/map_context/ctf_2fort/spectator_3.jpg",
        "https://teamwork.tf/images/map_context/ctf_2fort/spectator_4.jpg",
        "https://teamwork.tf/images/map_context/ctf_2fort/spectator_5.jpg",
        "https://teamwork.tf/images/map_context/ctf_2fort/spectator_6.jpg"
    ],
    "leveloverview": {
        "image": "https://teamwork.tf/images/map_context/ctf_2fort/overview_merged.jpg",
        "context": [
            {
                "screenHeight": 1080,
                "scale": 9,
                "screenWidth": 1920
            },
            {
                "y": 0,
                "x": -172.20995,
                "z": 1552.0601
            }
        ]
    }
}
```

## Custom serverlists

Custom serverlists are lists of gameservers filtered by the community, as shown on the [custom serverlists page](https://teamwork.tf/community/customserverlists).


### Overview
```
https://teamwork.tf/api/v1/customserverlist/?key=YOUR_API_KEY
```

Example result:
```json
[
{      
   "id":1,
   "name":"x100 servers",
   "description":"x100 is 10 times more of a clusterfuck than x10!",
   "description_large":"<p>This serverlist contains all the x100 servers out there which are being played on. Enjoy!<\/p>",
   "creator":{
      "id":76561198266675080,
      "name":"teamwork.tf"  
   },
   "subscribed":16,
   "filters":{
      "filter_hostname_whitelist":[
         "x100"
      ],
      "filter_hostname_blacklist":[
         "x1000" 
      ]   
   } 
},
...
]
```
Note that many different kind of filters exist. You can play around with the API to find all filters.

### Retrieve a specific serverlist

```
https://teamwork.tf/api/v1/customserverlist/{id}?key=YOUR_API_KEY
```

For a result look at the example above (overview).

### Retrieve the servers from a specific serverlist

```
https://teamwork.tf/api/v1/customserverlist/{id}/servers?key=YOUR_API_KEY
```

## Meet your Map lobbies

Meet your map, is a lobby system on the teamwork.tf website. This lobby system is currently hidden from the public, as this is still in beta.

### List lobbies

List all lobbies in MyM.

```
https://teamwork.tf/api/v1/meet-your-map/?key=YOUR_API_KEY
```

Example result:
```json
[
    {
        "id": 1,
        "name": "Meet your Map Lobby EU",
        "region": "EU",
        "status": "closed",
        "ad_hoc_allowed": true,
        "updated_at": {
            "date": "2017-11-25 22:52:23.000000",
            "timezone_type": 3,
            "timezone": "CET"
        }
    },
    ...
]
```

### Get a specific MyM lobby

Get the status of a specific MyM lobby. Status is either `ready`, `in-progress`, or `closed`

```
https://teamwork.tf/api/v1/meet-your-map/{id}?key=YOUR_API_KEY
```

Example result:
```json
{
    "id": 1,
    "name": "Meet your Map Lobby EU",
    "region": "EU",
    "status": "closed",
    "ad_hoc_allowed": true,
    "updated_at": {
        "date": "2017-11-25 22:52:23.000000",
        "timezone_type": 3,
        "timezone": "CET"
    }
}
```

