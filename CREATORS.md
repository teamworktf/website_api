# YouTube/Map Creator information

Retrieve information about creators from Teamwork.tf. [Prerequistes for using this API](https://github.com/teamworktf/website_api).

## Find YouTube creator based on SteamID

Search for a specific map that is being played in TF2. Lists up to 50 results, so be specific in your search.

```
https://teamwork.tf/api/v1/map-stats/search?search_term={search}&key=YOUR_API_KEY
```

Example result:
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
