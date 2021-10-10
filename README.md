# MAL-Sync Backup
The main purppose of this repository is have a backup of the <a href="https://github.com/MALSync/MALSync">MAL-Sync</a> MAL to Streaming page mapping database. But using the data for other uses is allowed. For commercial use <a href="mailto:lolamtisch@gmail.com">contact us</a>.
The data is updated once a week. Wrong/missing mappings are not seldom, specially mangas, but because they are generated through all the users of MAL-Sync it should correct itself over time.

## Stats

<!--statstable-->
| Page      | Total | MalID | noMalID | AniID | noAniID |
| --------- | ----- | ----- | ------- | ----- | ------- |
| 9anime    | 13062 | 12844 | 218     | 12442 | 620     |
| Gogoanime | 8289  | 8143  | 146     | 8067  | 222     |
| Mangadex  | 46085 | 25442 | 20643   | 27003 | 19082   |
| MangaNato | 10151 | 5694  | 4457    | 6335  | 3816    |
| Twistmoe  | 2003  | 1982  | 21      | 1977  | 26      |
| MangaFox  | 7809  | 4881  | 2928    | 4920  | 2889    |
| MangaSee  | 6061  | 5166  | 895     | 5292  | 769     |
<!--/statstable-->

## Structure

An _index.json can be found in every folder containing an array of all ids

### MAL -> Streaming Page Structure:
`data/myanimelist/(anime|manga)/[id].json`  
  
anime/19815
```json
{
  "altTitle": [
    "No Game, No Life",
    "NGNL",
    "ノーゲーム・ノーライフ"
  ],
  "id": 19815,
  "type": "anime",
  "title": "No Game No Life",
  "url": "https://myanimelist.net/anime/19815/No_Game_No_Life",
  "image": "https://cdn.myanimelist.net/images/anime/5/65187.jpg",
  "category": "TV",
  "hentai": false,
  "createdAt": "2020-10-12T12:36:13.580Z",
  "updatedAt": "2020-10-15T11:36:06.203Z",
  "Pages": {
    "Aniwatch": {
      "350": {
        "...": "..."
      }
    },
    "9anime": {
      "4qkm": {
        "...": "..."
      },
      "y2p0": {
        "...": "..."
      }
    },
    "Gogoanime": {
      "no-game-no-life": {
        "...": "..."
      },
      "no-game-no-life-dub": {
        "...": "..."
      }
    },
    "Twistmoe": {
      "no-game-no-life": {
        "...": "..."
      }
    }
  }
}

```

### Streaming Page -> MAL Structure:  
`data/pages/[streaming page key]/[id].json`  
  
9anime/214
```json
{
  "identifier": "214",
  "malUrl": "https://myanimelist.net/anime/9617/K-On_Movie",
  "type": "anime",
  "page": "9anime",
  "title": "K-On! Movie",
  "url": "...",
  "image": "....",
  "hentai": false,
  "sticky": false,
  "active": true,
  "actor": null,
  "malId": 9617,
  "createdAt": "...",
  "updatedAt": "...",
  "Mal": {
    "altTitle": [],
    "id": 9617,
    "type": "anime",
    "title": "K-On! Movie",
    "url": "...",
    "image": "...",
    "category": "-",
    "hentai": false,
    "createdAt": "...",
    "updatedAt": "..."
  }
}

```

How to find the IDs can be checked in <a href="https://github.com/lolamtisch/MALSync/tree/master/src/pages">here</a>.  
`[PageKey]/main.ts -> (overview|sync):getIdentifier(url)`
