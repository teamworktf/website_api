# YouTube/Map Creator information

Retrieve information about creators from Teamwork.tf. [Prerequistes for using this API](https://github.com/teamworktf/website_api).

## Find YouTube creator based on SteamID

Search for a specific YouTube creator that is [listed on our website](https://teamwork.tf/creators/explore) based on their Steam ID64:

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

## Find Gamemap creator based on SteamID

Search for a specific Gamemap creator that is listed on our website based on their Steam ID64:

```
https://teamwork.tf/api/v1/map-creator/steamid/{steamid}?key=YOUR_API_KEY
```
