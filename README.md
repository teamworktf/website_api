# teamwork.tf API

This document holds all available developer functions that available to the public.

## Banner image for gameservers

You can request two type of image banners for any (populated) TF2 gameserver. The two formats are available at:

```
https://teamwork.tf/community/quickplay/  ip:port  /550x125.png
https://teamwork.tf/community/quickplay/  ip:port  /675x125.png
```

**Example:**

[![](https://teamwork.tf/community/quickplay/74.91.127.172:27017/675x125.png)](https://teamwork.tf/community/quickplay/74.91.127.172:27017/675x125.png)

## Server community information

You can request the status of a server community through JSON. This information is available at:

```
https://teamwork.tf/community/provider/  provider-slug  .json
```

**Example:**

[https://teamwork.tf/community/provider/vaticancity.json](vaticancity)

```
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

To retrieve additional statistics about the server community:

```
https://teamwork.tf/community/provider/  provider-slug  /stats.json
```

**Example:**

[https://teamwork.tf/community/provider/vaticancity/stats.json](vaticancity)

```
{

    "players": 124,
    "regions_with_players": [
        "North America",
        "Europe"
    ],
    "gamemodes": [
        "trading",
        "achievement",
        "mge-mod"
    ],
    "servers": [
        {
            "ip": "95.172.92.149",
            "port": 27015
        },
        ...
    ]

}
```
