# YouTube/Map Creator information

Retrieve information about creators from Teamwork.tf. [Prerequistes for using this API](https://github.com/teamworktf/website_api).

## Find YouTube creator based on SteamID

Search for a specific YouTube creator that is [listed on our website](https://teamwork.tf/creators/explore) based on their SteamID64:

```
https://teamwork.tf/api/v1/youtube-creator/steamid/{steamid}?key=YOUR_API_KEY
```

This endpoint can return multiple accounts, as multiple YouTube creator accounts can be associated to the same Steam profile. Besides the `id`, `link`, `name`, `youtube_acc` and `steam_acc` fields, all are optional and can be NULL.

**Example result:** *array*
```json
[   
    {
      "id":816,
      "link":"https:\/\/teamwork.tf\/c\/greatblue",
      "name":"Great Blue",
      "type":"casual",
      "main":null,
      "youtube_acc":"UCgRhvJsaM13emRax3rSbRKQ",
      "twitch_acc":null,
      "twitter_acc":"GreatBlueYT",
      "steam_acc":"76561198115146996",
      "discord_group":null,
      "steam_group":null,
      "thumbnail_url":"https:\/\/yt3.ggpht.com\/a\/AATXAJzb4uh4Y26WY4032c7u4AZ6x4r4Z022n6J2fA=s240-c-k-c0xffffffff-no-rj-mo"
   }
]
```

## Get created gamemaps based on SteamID

Get a list of created gamemaps based on their SteamID64. Note that this user does not have a "creator" account on the website, as this is focussed on a YouTube channel.

```
https://teamwork.tf/api/v1/map-creator/steamid/{steamid}?key=YOUR_API_KEY
```

This will return a list of associations to a gamemap. A gamemap association can be based on the full map name (e.g. `dr_bank_v12` or the normalized map name `dr_bank` (a normalized map name is without any version number or alteration of the base map).

**Example result:** *array*
```json
[
    {
      "map_name":null,
      "normalized_map_name":"vsh_dr_bank"
    }
]
```
