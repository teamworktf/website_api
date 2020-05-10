# Community Quickplay

Retrieve information about (community) gameservers within Team Fortress 2. [Prerequistes for using this API](https://github.com/teamworktf/website_api).

# List gamemodes

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

# Retrieve a list of gameservers that contain a gamemode

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

# Community Provider

Retrieve information about any of the community providers, as listed on the [provider overview](https://teamwork.tf/community/providers).

## Retrieve information from a community provider

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

## Retrieve statistics of a community provider

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

## Get serverlist from a community provider

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

# Competitive Provider

## Retrieve specific provider information

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

## Retrieve statistics from a competitive provider

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

# Custom serverlists

Custom serverlists are lists of gameservers filtered by the community, as shown on the [custom serverlists page](https://teamwork.tf/community/customserverlists).


## Overview
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

## Retrieve a specific serverlist

```
https://teamwork.tf/api/v1/customserverlist/{id}?key=YOUR_API_KEY
```

For a result look at the example above (overview).

## Retrieve the servers from a specific serverlist

```
https://teamwork.tf/api/v1/customserverlist/{id}/servers?key=YOUR_API_KEY
```

Retrieve a list of gameservers that are in this serverlist. See [this as an example](#user-content-retrieve-a-list-of-gameservers-that-contain-a-gamemode).
