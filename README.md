# NHL API Documentation

This document aims to serve as an unofficial reference for the NHL API. Corrections and/or suggestions are welcome.

## Base URL

All endpoints described in this document are relative to the following base URL:

```
https://api-web.nhle.com/
```



## Player Information

### Players

#### Get Game Log
- **Endpoint**: `/v1/player/{player}/game-log/{season}/{game-type}`
- **Method**: GET
- **Description**: Retrieve the game log for a specific player, season, and game type.
- **Parameters**:
  - `player` (int) - Player ID
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
  - `game-type` (int) - Game type (guessing 2 for regular season, 3 for playoffs)
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/player/8478402/game-log/20232024/2"
```

#### Get Specific Player Info
- **Endpoint**: `/v1/player/{player}/landing`
- **Method**: GET
- **Description**: Retrieve information for a specific player.
- **Parameters**:
  - `player` (int) - Player ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/player/8478402/landing"
```

#### Get Game Log As of Now
- **Endpoint**: `/v1/player/{player}/game-log/now`
- **Method**: GET
- **Description**: Retrieve the game log for a specific player as of the current moment.
- **Parameters**:
  - `player` (int) - Player ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/player/8478402/game-log/now"
```
### Skaters

#### Get Current Skater Stats Leaders
- **Endpoint**: `/v1/skater-stats-leaders/current`
- **Method**: GET
- **Description**: Retrieve current skater stats leaders.
- **Parameters**:
  - `categories` (query, string) - Optional
  - `limit` (query, int) - Optional
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/skater-stats-leaders/current?categories=goals&limit=5"
```

#### Get Skater Stats Leaders for a Specific Season and Game Type
- **Endpoint**: `/v1/skater-stats-leaders/{season}/{game-type}`
- **Method**: GET
- **Description**: Retrieve skater stats leaders for a specific season and game type.
- **Parameters**:
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
  - `game-type` (int) - Game type (guessing 2 for regular season, 3 for playoffs)
- **Parameters**:
  - `categories` (query, string) - Optional
  - `limit` (query, int) - Optional
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/skater-stats-leaders/20222023/2?categories=assists&limit=3"
```

### Goalies

#### Get Current Goalie Stats Leaders
- **Endpoint**: `/v1/goalie-stats-leaders/current`
- **Method**: GET
- **Description**: Retrieve current goalie stats leaders.
- **Request Parameters**:
  - `categories` (query, string) - Optional
  - `limit` (query, int) - Optional
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/goalie-stats-leaders/current?categories=wins&limit=5"
```

#### Get Goalie Stats Leaders by Season
- **Endpoint**: `/v1/goalie-stats-leaders/{season}/{game-type}`
- **Method**: GET
- **Description**: Retrieve goalie stats leaders for a specific season and game type.
- **Parameters**:
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
  - `game-type` (int) - Game type (guessing 2 for regular season, 3 for playoffs)
- **Request Parameters**:
  - `categories` (query, string) - Optional
  - `limit` (query, int) - Optional
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/goalie-stats-leaders/20232024/2?categories=wins&limit=3"
```

### Player Spotlight

#### Get Players
- **Endpoint**: `/v1/player-spotlight`
- **Method**: GET
- **Description**: Retrieve information about players in the "spotlight".
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/player-spotlight"
```



## Team Information

### Standings

#### Get Standings
- **Endpoint**: `/v1/standings/now`
- **Method**: GET
- **Description**: Retrieve the standings as of the current moment.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/standings/now"
```

#### Get Standings by Date
- **Endpoint**: `/v1/standings/{date}`
- **Method**: GET
- **Description**: Retrieve the standings for a specific date.
- **Parameters**:
  - `date` (string) - Date in YYYY-MM-DD format
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/standings/2023-11-10"
```

#### Get Standings information for each Season
- **Endpoint**: `/v1/standings-season`
- **Method**: GET
- **Description**: Retrieves information for each season's standings
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/standings-season"
```

### Stats

#### Get Club Stats Now
- **Endpoint**: `/v1/club-stats/{team}/now`
- **Method**: GET
- **Description**: Retrieve current statistics for a specific club.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/club-stats/TOR/now"
```

#### Get Club Stats for the Season for a Team
- **Endpoint**: `/v1/club-stats-season/{team}`
- **Method**: GET
- **Description**: Returns an overview of the stats for each season for a specific club. Seems to only indicate the gametypes played in each season.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/club-stats-season/TOR"
```

#### Get Club Stats by Season and Game Type
- **Endpoint**: `/v1/club-stats/{team}/{season}/{game-type}`
- **Method**: GET
- **Description**: Retrieve the stats for a specific team, season, and game type.
- **Parameters**:
  - `team` (string) - Three-letter team code
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
  - `game-type` (int) - Game type (guessing 2 for regular season, 3 for playoffs)
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/club-stats/TOR/20232024/2"
```


#### Get Team Scoreboard
- **Endpoint**: `/v1/scoreboard/{team}/now`
- **Method**: GET
- **Description**: Retrieve the scoreboard for a specific team as of the current moment.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/scoreboard/TOR/now"
```

### Roster

#### Get Team Roster As of Now
- **Endpoint**: `/v1/roster/{team}/current`
- **Method**: GET
- **Description**: Retrieve the roster for a specific team as of the current moment.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/roster/TOR/current"
```

#### Get Team Roster by Season
- **Endpoint**: `/v1/roster/{team}/{season}`
- **Method**: GET
- **Description**: Retrieve the roster for a specific team and season.
- **Parameters**:
  - `team` (string) - Three-letter team code
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/roster/TOR/20232024"
```

#### Get Roster Season for Team
- **Endpoint**: `/v1/roster-season/{team}`
- **Method**: GET
- **Description**: Seems to just return a list of all of the seasons that the team played.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/roster-season/TOR"
```

#### Get Team Prospects
- **Endpoint**: `/v1/prospects/{team}`
- **Method**: GET
- **Description**: Retrieve prospects for a specific team.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/prospects/TOR"
```

### Schedule

#### Get Team Season Schedule As of Now
- **Endpoint**: `/v1/club-schedule-season/{team}/now`
- **Method**: GET
- **Description**: Retrieve the season schedule for a specific team as of the current moment.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/club-schedule-season/TOR/now"
```

#### Get Team Season Schedule
- **Endpoint**: `/v1/club-schedule-season/{team}/{season}`
- **Method**: GET
- **Description**: Retrieve the season schedule for a specific team and season.
- **Parameters**:
  - `team` (string) - Three-letter team code
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/club-schedule-season/TOR/20232024"
```

#### Get Month Schedule As of Now
- **Endpoint**: `/v1/club-schedule/{team}/month/now`
- **Method**: GET
- **Description**: Retrieve the monthly schedule for a specific team as of the current moment.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/club-schedule/TOR/month/now"
```

#### Get Month Schedule
- **Endpoint**: `/v1/club-schedule/{team}/month/{month}`
- **Method**: GET
- **Description**: Retrieve the monthly schedule for a specific team and month.
- **Parameters**:
  - `team` (string) - Three-letter team code
  - `month` (string) - Month in YYYY-MM format
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/club-schedule/TOR/month/2023-11"
```

#### Get Week Schedule
- **Endpoint**: `/v1/club-schedule/{team}/week/{date}`
- **Method**: GET
- **Description**: Retrieve the weekly schedule for a specific team and date.
- **Parameters**:
  - `team` (string) - Three-letter team code
  - `date` (string) - Date in YYYY-MM-DD format
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/club-schedule/TOR/week/2023-11-10"
```

#### Get Week Schedule As of Now
- **Endpoint**: `/v1/club-schedule/{team}/week/now`
- **Method**: GET
- **Description**: Retrieve the weekly schedule for a specific team as of the current moment.
- **Parameters**:
  - `team` (string) - Three-letter team code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/club-schedule/TOR/week/now"
```




## League Schedule Information

### Schedule

#### Get Current Schedule
- **Endpoint**: `/v1/schedule/now`
- **Method**: GET
- **Description**: Retrieve the current schedule.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/schedule/now"
```

#### Get Schedule by Date
- **Endpoint**: `/v1/schedule/{date}`
- **Method**: GET
- **Description**: Retrieve the schedule for a specific date.
- **Parameters**:
  - `date` (string) - Date format: YYYY-MM-DD
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/schedule/2023-11-10"
```

### Schedule Calendar

#### Get Schedule Calendar As of Now
- **Endpoint**: `/v1/schedule-calendar/now`
- **Method**: GET
- **Description**: Retrieve the schedule calendar as of the current moment.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/schedule-calendar/now"
```

#### Get Schedule Calendar for a Specific Date
- **Endpoint**: `/v1/schedule-calendar/{date}`
- **Method**: GET
- **Description**: Retrieve the schedule calendar for a specific date.
- **Parameters**:
  - `date` (string) - Date in YYYY-MM-DD format
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/schedule-calendar/2023-11-10"
```



## Game Information

### Daily Scores

#### Get Daily Scores As of Now
- **Endpoint**: `/v1/score/now`
- **Method**: GET
- **Description**: Retrieve daily scores as of the current moment.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/score/now"
```

#### Get Daily Scores by Date
- **Endpoint**: `/v1/score/{date}`
- **Method**: GET
- **Description**: Retrieve daily scores for a specific date.
- **Parameters**:
  - `date` (string) - Date format: YYYY-MM-DD
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/score/2023-11-10"
```

#### Get Scoreboard
- **Endpoint**: `/v1/scoreboard/now`
- **Method**: GET
- **Description**: Retrieve the overall scoreboard as of the current moment.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/scoreboard/now"
```

### Where to Watch
#### Get Streams
- **Endpoint**: `/v1/where-to-watch`
- **Method**: GET
- **Description**: Retrieve information about streaming options.
- **Parameters**:
  - `include` (query, string) - Optional
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/where-to-watch"
```

### Gamecenter
#### Get Play By Play
- **Endpoint**: `/v1/gamecenter/{game-id}/play-by-play`
- **Method**: GET
- **Description**: Retrieve play-by-play information for a specific game.
- **Parameters**:
  - `game-id` (int) - Game ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/gamecenter/2023020204/play-by-play"
```

#### Get Landing
- **Endpoint**: `/v1/gamecenter/{game-id}/landing`
- **Method**: GET
- **Description**: Retrieve landing information for a specific game.
- **Parameters**:
  - `game-id` (int) - Game ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/gamecenter/2023020204/landing"
```

#### Get Boxscore
- **Endpoint**: `/v1/gamecenter/{game-id}/boxscore`
- **Method**: GET
- **Description**: Retrieve boxscore information for a specific game.
- **Parameters**:
  - `game-id` (int) - Game ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/gamecenter/2023020204/boxscore"
```
### Network

#### Get TV Schedule for a Specific Date
- **Endpoint**: `/v1/network/tv-schedule/{date}`
- **Method**: GET
- **Description**: Retrieve the TV schedule for a specific date.
- **Parameters**:
  - `date` (string) - Date in YYYY-MM-DD format
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/network/tv-schedule/2023-11-10"
```

#### Get Current TV Schedule
- **Endpoint**: `/v1/network/tv-schedule/now`
- **Method**: GET
- **Description**: Retrieve the current TV schedule.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/network/tv-schedule/now"
```

### Odds
#### Get Partner Game Odds
- **Endpoint**: `/v1/partner-game/{country-code}/now`
- **Method**: GET
- **Description**: Retrieve odds for games in a specific country as of the current moment.
- **Parameters**:
  - `country-code` (string) - Country code
- **Response**: JSON format

###### Example using cURL:

```bash
curl -L -X GET "https://api-web.nhle.com/v1/partner-game/US/now"
```



## Season

#### Get Seasons
- **Endpoint**: `/v1/season`
- **Method**: GET
- **Description**: Retrieve a list of all season IDs past & present in the NHL.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/season"
```



## Miscellaneous

### Meta

#### Get Meta Information
- **Endpoint**: `/v1/meta`
- **Method**: GET
- **Description**: Retrieve meta information.
- **Request Parameters**:
  - `players` (query, string) - Optional
  - `teams` (query, string) - Optional
  - `seasonStates` (query, string) - Optional (Unsure what the options might be here)
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/meta?players=8478402&teams=EDM,TOR"
```

#### Get Game Information
- **Endpoint**: `/v1/meta/game/{game-id}`
- **Method**: GET
- **Description**: Retrieve information for a specific game.
- **Parameters**:
  - `game-id` (int) - Game ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/meta/game/2023020204"
```

### OpenAPI Specification

#### Get OpenAPI Specification
- **Endpoint**: `/model/v1/openapi.json`
- **Method**: GET
- **Description**: Retrieve the OpenAPI specification. (Seems to return 404 currently)
- **Response**: JSON or YAML format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/model/v1/openapi.json"
```

### Unknown
#### Get Location
- **Endpoint**: `/v1/location`
- **Method**: GET
- **Description**: Not sure what this one is for. Returns a country code.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/location"
```


---
*For the full WADL with extended resources: [WADL Link](https://api-web.nhle.com/application.wadl?detail=true)*
