## Minecraft Endpoint
> Requires MINECRAFT endpoint on API key.

To access minecraft player information, you need to use our Minecraft Endpoint. Make sure you have an API Key before continuing!

### Get player statistics with UUID • `GET /player/uuid/{player.uuid}`


Get player statistics using an uuid. Only supports undashed UUIDs.

`{player.uuid}` • The Minecraft UUID of the target player 
- Returns `UserInfo` Object

|

### Get player statistics with username • `GET /player/username/{player.username}`

Get player statistics using an uuid. Only supports undashed UUIDs.

`{player.username}` • The Minecraft Username of the target player, case-sensitive.

- Returns `UserInfo` Object



### Example UserInfo Object
```json
 {
    "uuid": "54302e60-787f-430e-b62f-c7ec377986c1",
    "name": "RaymondDev",
    "title": "NONE",
    "rankcolor": "RAINBOW",
    "stats": {
      "overall": {
        "wins": 102,
        "losses": 87,
        "draws": 0,
        "kills": 643,
        "deaths": 1157,
        "goals": 462,
        "winstreak": 0,
        "bestWinstreak": 9
      },
      "solos": {
        "wins": 92,
        "losses": 72,
        "draws": 0,
        "kills": 590,
        "deaths": 940,
        "goals": 422,
        "winstreak": 0,
        "bestWinstreak": 9
      },
      "doubles": {
        "wins": 9,
        "losses": 13,
        "draws": 0,
        "kills": 61,
        "deaths": 209,
        "goals": 38,
        "winstreak": 0,
        "bestWinstreak": 6
      },
      "threes": {
        "wins": 0,
        "losses": 1,
        "draws": 0,
        "kills": 0,
        "deaths": 6,
        "goals": 0,
        "winstreak": 0,
        "bestWinstreak": 0
      },
      "fours": {
        "wins": 1,
        "losses": 1,
        "draws": 0,
        "kills": 0,
        "deaths": 2,
        "goals": 2,
        "winstreak": 0,
        "bestWinstreak": 1
      }
    },
    "favoritemaps": []
  }
```
### Examples
#### Python
```py
import aiohttp
import asyncio
import json


async def req(username):
    async with aiohttp.ClientSession() as session:
        async with session.get(
                url=f"https://api.mojang.com/users/profiles/minecraft/{username}"
        ) as data:
            return await data.json()


async def req2(uuid, key):
    async with aiohttp.ClientSession() as session:
        async with session.get(
                url=f"https://xincraft.net/api/v1/player/uuid/{uuid}",
                headers={
                    "xincraft-api": key
                }
        ) as data:
            jsonData = await data.json()
            return json.dumps(jsonData, sort_keys=True, indent=4)


data = asyncio.run(req("ThatHolyNon"))
d = asyncio.run(req2(data["id"], "my-api-key"))  # replace my-api-key with your api key
print(d)

```
