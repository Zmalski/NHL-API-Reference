# NHL API Documentation

This document aims to serve as an unofficial reference for the NHL APIs. Corrections and/or suggestions are welcome.

Please note that there appears to be *two* primary sources for official NHL APIs. (api-web.nhle.com and api.nhle.com/stats/rest). This document is broken into distinct sections detailing each API.

## Table of Contents
### [api-web.nhle.com](#nhl-web-api-documentation)
1. [Base URL](#base-url)
2. [Player Information](#player-information)
   1. [Players](#players)
      1. [Get Game Log](#get-game-log)
      2. [Get Specific Player Info](#get-specific-player-info)
      3. [Get Game Log As of Now](#get-game-log-as-of-now)
   2. [Skaters](#skaters)
      1. [Get Current Skater Stats Leaders](#get-current-skater-stats-leaders)
      2. [Get Skater Stats Leaders for a Specific Season and Game Type](#get-skater-stats-leaders-for-a-specific-season-and-game-type)
   3. [Goalies](#goalies)
      1. [Get Current Goalie Stats Leaders](#get-current-goalie-stats-leaders)
      2. [Get Goalie Stats Leaders by Season](#get-goalie-stats-leaders-by-season)
   4. [Player Spotlight](#player-spotlight)
      1. [Get Players](#get-players)
3. [Team Information](#team-information)
   1. [Standings](#standings)
      1. [Get Standings](#get-standings)
      2. [Get Standings by Date](#get-standings-by-date)
      3. [Get Standings information for each Season](#get-standings-information-for-each-season)
   2. [Stats](#stats)
      1. [Get Club Stats Now](#get-club-stats-now)
      2. [Get Club Stats for the Season for a Team](#get-club-stats-for-the-season-for-a-team)
      3. [Get Club Stats by Season and Game Type](#get-club-stats-by-season-and-game-type)
      4. [Get Team Scoreboard](#get-team-scoreboard)
   3. [Roster](#roster)
      1. [Get Team Roster As of Now](#get-team-roster-as-of-now)
      2. [Get Team Roster by Season](#get-team-roster-by-season)
      3. [Get Roster Season for Team](#get-roster-season-for-team)
      4. [Get Team Prospects](#get-team-prospects)
   4. [Schedule](#schedule)
      1. [Get Team Season Schedule As of Now](#get-team-season-schedule-as-of-now)
      2. [Get Team Season Schedule](#get-team-season-schedule)
      3. [Get Month Schedule As of Now](#get-month-schedule-as-of-now)
      4. [Get Month Schedule](#get-month-schedule)
      5. [Get Week Schedule](#get-week-schedule)
      6. [Get Week Schedule As of Now](#get-week-schedule-as-of-now)
4. [League Schedule Information](#league-schedule-information)
   1. [Schedule](#schedule-1)
      1. [Get Current Schedule](#get-current-schedule)
      2. [Get Schedule by Date](#get-schedule-by-date)
   2. [Schedule Calendar](#schedule-calendar)
      1. [Get Schedule Calendar As of Now](#get-schedule-calendar-as-of-now)
      2. [Get Schedule Calendar for a Specific Date](#get-schedule-calendar-for-a-specific-date)
5. [Game Information](#game-information)
   1. [Daily Scores](#daily-scores)
      1. [Get Daily Scores As of Now](#get-daily-scores-as-of-now)
      2. [Get Daily Scores by Date](#get-daily-scores-by-date)
      3. [Get Scoreboard](#get-scoreboard)
   2. [Where to Watch](#where-to-watch)
      1. [Get Streams](#get-streams)
   3. [Game Events](#game-events)
      1. [Get Play By Play](#get-play-by-play)
      2. [Get Landing](#get-landing)
      3. [Get Boxscore](#get-boxscore)
      4. [Get Game Story](#get-game-story)
   4. [Network](#network)
      1. [Get TV Schedule for a Specific Date](#get-tv-schedule-for-a-specific-date)
      2. [Get Current TV Schedule](#get-current-tv-schedule)
   5. [Odds](#odds)
      1. [Get Partner Game Odds](#get-partner-game-odds)
6. [Playoff Information](#playoff-information)
   1. [Overview](#overview)
      1. [Playoff Series Carousel](#playoff-series-carousel)
   2. [Schedule](#schedule-2)
      1. [Get Playoff Series Schedule](#get-playoff-series-schedule)
   3. [Bracket](#bracket)
      1. [Get Playoff Bracket](#get-playoff-bracket)
7. [Season](#season)
   1. [Get Seasons](#get-seasons)
8. [Draft](#draft)
   1. [Get Draft Rankings](#get-draft-rankings)
   2. [Get Draft Rankings by Date](#get-draft-rankings-by-date)
   3. [Get Draft Tracker Now](#get-draft-tracker-now)
   4. [Get Draft Picks Now](#get-draft-picks-now)
   5. [Get Draft Picks](#get-draft-picks)
9. [Miscellaneous](#miscellaneous)
   1. [Meta](#meta)
      1. [Get Meta Information](#get-meta-information)
      2. [Get Game Information](#get-game-information)
      3. [Get Location](#get-location)
      4. [Get Playoff Series Metadata](#get-playoff-series-metadata)
   2. [Postal Lookup](#postal-lookup)
      1. [Get Postal Code Information](#get-postal-code-information)
   3. [Game Replays](#game-replays)
      1. [Get Goal Replay](#get-goal-replay)
      2. [Get Play Replay](#get-play-replay)
   4. [Additional Game Content](#additional-game-content)
      1. [Get Game Right Rail Content](#get-game-right-rail-content)
      2. [Get WSC Play By Play](#get-wsc-play-by-play)
   5. [OpenAPI Specification](#openapi-specification)
      1. [Get OpenAPI Specification](#get-openapi-specification)
---
### [api.nhle.com/stats/rest](#nhl-stats-api-documentation)
1. [Base URL](#base-url-1)
2. [Players](#players-1)
   1. [Players](#players-2)
      1. [Get Player Information](#get-player-information)
   2. [Skaters](#skaters)
      1. [Get Skater Leaders](#get-skater-leaders)
      2. [Get Skater Milestones](#get-skater-milestones)
      3. [Get Skater Information](#get-skater-information)
      4. [Get Skater Stats](#get-skater-stats)
   3. [Goalies](#goalies)
      1. [Get Goalie Leaders](#get-goalie-leaders)
      2. [Get Goalie Stats](#get-goalie-stats)
      3. [Get Goalie Milestones](#get-goalie-milestones)
   4. [Draft](#draft)
      1. [Get Draft Information](#get-draft-information)
4. [Teams](#teams)
   1. [Get Team Information](#get-team-information)
   2. [Get Team By ID](#get-team-by-id)
   3. [Get Team Stats](#get-team-stats)
   4. [Get Franchise Information](#get-franchise-information)
5. [Season](#season)
   1. [Get Component Season](#get-component-season)
   2. [Get Season](#get-season)
6. [Game](#game)
   1. [Get Game Information](#get-game-information-1)
   2. [Get Game Metadata](#get-game-metadata)
7. [Miscellaneous](#miscellaneous-1)
   1. [Configuration](#configuration)
      1. [Get Configuration](#get-configuration)
   2. [Ping the Server](#ping-the-server)
   3. [Get Country Information](#get-country-information)
   4. [Get Shift Charts](#get-shift-charts)
   5. [Glossary](#glossary)
      1. [Get Glossary](#get-glossary)
   6. [Content Module](#content-module)
      1. [Get Content Module](#get-content-module)


---


# NHL Web API Documentation

This section provides documentation for the NHL Web API (https://api-web.nhle.com/).


## Base URL

All endpoints described in this section are relative to the following base URL:

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
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
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
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
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
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
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
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
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

### Game Events
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

#### Get Game Story
- **Endpoint**: `/v1/wsc/game-story/{game-id}`
- **Method**: GET
- **Description**: Retrieve game story information for a specific game.
- **Parameters**:
  - `game-id` (int) - Game ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/wsc/game-story/2023020204"
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



## Playoff Information

### Overview

#### Playoff Series Carousel
- **Endpoint**: `/v1/playoff-series/carousel/{season}/`
- **Method**: GET
- **Description**: Retrieve an overview of each playoff series.
- **Parameters**:
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/playoff-series/carousel/20232024/"
```

### Schedule

#### Get Playoff Series Schedule
- **Endpoint**: `/v1/schedule/playoff-series/{season}/{series_letter}/`
- **Method**: GET
- **Description**: Retrieve the schedule for a specific playoff series.
- **Parameters**:
  - `season` (int) - Season in YYYYYYYY format, where the first four digits represent the start year of the season, and the last four digits represent the end year.
  - `series_letter` (string) - Single letter indicating which series to retrieve. Is sequential in alphabetical order.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/schedule/playoff-series/20232024/a"
```

### Bracket

#### Get Playoff Bracket
- **Endpoint**: `/v1/playoff-bracket/{year}`
- **Method**: GET
- **Description**: Retrieve the current bracket for a specific year's playoffs.
- **Parameters**:
  - `year` (int) - Year in YYYY format
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/playoff-bracket/2022"
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

## Draft

#### Get Draft Rankings
- **Endpoint** `/v1/draft/rankings/now`
- **Method**: GET
- **Description**: Retrieve a list of all draft prospects by category of prospect as of the current moment.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/draft/rankings/now"
```

#### Get Draft Rankings by Date
- **Endpoint** `/v1/draft/rankings/{season}/{prospect_category}`
- **Method**: GET
- **Description**: Retrieve a list of all draft prospects by category of prospect for a specific season.
- **Parameters**:
  - `season` (int) - Season in YYYY format
  - `prospect_category` (int) - Prospect Category (1 - North American Skater, 2 - International Skater, 3 - North American Goalie, 4 - International Goalie)
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/draft/rankings/2023/1"
```

#### Get Draft Tracker Now
- **Endpoint**: `/v1/draft-tracker/picks/now`
- **Method**: GET
- **Description**: Retrieve current draft tracker information with the most recent draft picks.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/draft-tracker/picks/now"
```

#### Get Draft Picks Now
- **Endpoint**: `/v1/draft/picks/now`
- **Method**: GET
- **Description**: Retrieve the most recent draft picks information.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/draft/picks/now"
```

#### Get Draft Picks
- **Endpoint** `https://api-web.nhle.com/v1/draft/picks/{season}/{round}`
- **Method**: GET
- **Description**: Retrieve a list of draft picks for a specific season.
- **Parameters**:
  - `season` (int) - Season in YYYY format
  - `round` (string) - Selectable round (1-7, 1 for round 1 etc.) or `all` for all selectable rounds
- **Response**: JSON format

###### Example using cURL:
```bash
curl -X GET "https://api-web.nhle.com/v1/draft/picks/2023/all"
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

#### Get Location
- **Endpoint**: `/v1/location`
- **Method**: GET
- **Description**: Returns country code that the webserver thinks the user is in.
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/location"
```

#### Get Playoff Series Metadata
- **Endpoint**: `/v1/meta/playoff-series/{year}/{series_letter}`
- **Method**: GET
- **Description**: Retrieve metadata for a specific playoff series.
- **Parameters**:
  - `year` (int) - Year in YYYY format
  - `series_letter` (string) - Single letter identifying the playoff series
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/meta/playoff-series/2023/a"
```

### Postal Lookup

#### Get Postal Code Information
- **Endpoint**: `/v1/postal-lookup/{postalCode}`
- **Method**: GET
- **Description**: Retrieves information based on a postal code.
- **Parameters**:
  - `postalCode` (string) - Postal (or zip) code to look up
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/postal-lookup/90210"
```

### Game Replays

#### Get Goal Replay
- **Endpoint**: `/v1/ppt-replay/goal/{game-id}/{event-number}`
- **Method**: GET
- **Description**: Retrieves goal replay information for a specific game and event.
- **Parameters**:
  - `game-id` (int) - Game ID
  - `event-number` (int) - Event number within the game
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/ppt-replay/goal/2023020204/12"
```

#### Get Play Replay
- **Endpoint**: `/v1/ppt-replay/{game-id}/{event-number}`
- **Method**: GET
- **Description**: Retrieves replay information for a specific game and event.
- **Parameters**:
  - `game-id` (int) - Game ID
  - `event-number` (int) - Event number within the game
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/ppt-replay/2023020204/12"
```

### Additional Game Content

#### Get Game Right Rail Content
- **Endpoint**: `/v1/gamecenter/{game-id}/right-rail`
- **Method**: GET
- **Description**: Retrieves sidebar content for the game center view.
- **Parameters**:
  - `game-id` (int) - Game ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/gamecenter/2023020204/right-rail"
```

#### Get WSC Play By Play
- **Endpoint**: `/v1/wsc/play-by-play/{game-id}`
- **Method**: GET
- **Description**: Retrieves WSC (World Showcase) play-by-play information for a specific game.
- **Parameters**:
  - `game-id` (int) - Game ID
- **Response**: JSON format

###### Example using cURL:

```bash
curl -X GET "https://api-web.nhle.com/v1/wsc/play-by-play/2023020204"
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

---

*For the full WADL with extended resources: [WADL Link](https://api-web.nhle.com/application.wadl?detail=true)*




---
# NHL Stats API Documentation

This section provides documentation for the NHL Stats API (https://api.nhle.com/stats/rest).


## Base URL

All endpoints described in this section are relative to the following base URL:

```
https://api.nhle.com/stats/rest
```

## Players

### Players

#### Get Player Information
- **Endpoint**: `/{lang}/players`
- **Method**: GET
- **Description**: Retrieve basic player information. (Responses limited to 5 results)
- **Parameters**:
  - `lang` (string) - Language code
- **Request Parameters**:
  - `include` (query, string) - Optional
  - `exclude` (query, string) - Optional
  - `cayenneExp` (query, string) - Optional
  - `sort` (query, string) - Optional
  - `dir` (query, string) - Optional
  - `start` (query, int) - Optional
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/players?limit=3&sort=lastName&dir=asc&cayenneExp=currentTeamId=7"
```

### Skaters

#### Get Skater Leaders
- **Endpoint**: `/{lang}/leaders/skaters/{attribute}`
- **Method**: GET
- **Description**: Retrieve skater leaders for a specific attribute.
- **Parameters**:
  - `attribute` (string) - Skater attribute
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/leaders/skaters/points"
```

#### Get Skater Milestones
- **Endpoint**: `/{lang}/milestones/skaters`
- **Method**: GET
- **Description**: Retrieve skater milestones.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/milestones/skaters"
```

#### Get Skater Information
- **Endpoint**: `/{lang}/skater`
- **Method**: GET
- **Description**: Retrieve skater information.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/skater"
```

#### Get Skater Stats
- **Endpoint**: `/{lang}/skater/{report}`
- **Method**: GET
- **Description**: Retrieve skater stats for a specific report.
- **Parameters**:
  - `report` (string) - Skater report
  - `lang` (string) - Language code
- **Request Parameters**:
  - `isAggregate` (query, boolean) - Optional
  - `isGame` (query, boolean) - Optional
  - `factCayenneExp` (query, string) - Optional
  - `include` (query, string) - Optional
  - `exclude` (query, string) - Optional
  - `cayenneExp` (query, string) - **Required**
  - `sort` (query, string) - Optional
  - `dir` (query, string) - Optional
  - `start` (query, int) - Optional
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/skater/summary?limit=72&start=17&sort=points&cayenneExp=seasonId=20232024"
```



### Goalies

#### Get Goalie Leaders
- **Endpoint**: `/{lang}/leaders/goalies/{attribute}`
- **Method**: GET
- **Description**: Retrieve goalie leaders for a specific attribute.
- **Parameters**:
  - `attribute` (string) - Goalie attribute
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/leaders/goalies/gaa"
```

#### Get Goalie Stats
- **Endpoint**: `/{lang}/goalie/{report}`
- **Method**: GET
- **Description**: Retrieve goalie stats for a specific report.
- **Parameters**:
  - `report` (string) - Goalie report
  - `lang` (string) - Language code
- **Request Parameters**:
  - `isAggregate` (query, boolean) - Optional
  - `isGame` (query, boolean) - Optional
  - `factCayenneExp` (query, string) - Optional
  - `include` (query, string) - Optional
  - `exclude` (query, string) - Optional
  - `cayenneExp` (query, string) - **Required**
  - `sort` (query, string) - Optional
  - `dir` (query, string) - Optional
  - `start` (query, int) - Optional
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/goalie/summary?limit=72&start=15&sort=wins&cayenneExp=seasonId=20232024"
```

#### Get Goalie Milestones
- **Endpoint**: `/{lang}/milestones/goalies`
- **Method**: GET
- **Description**: Retrieve goalie milestones.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/milestones/goalies"
```

### Draft

#### Get Draft Information
- **Endpoint**: `/{lang}/draft`
- **Method**: GET
- **Description**: Retrieve draft information.
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/draft"
```



## Teams
#### Get Team Information
- **Endpoint**: `/{lang}/team`
- **Method**: GET
- **Description**: Retrieve list of all teams.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/team"
```

#### Get Team By ID
- **Endpoint**: `/{lang}/team/id/{id}`
- **Method**: GET
- **Description**: Retrieve information for a specific team by ID.
- **Parameters**:
  - `lang` (string) - Language code
  - `id` (string) - Team ID
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/team/id/10"
```

#### Get Team Stats
- **Endpoint**: `/{lang}/team/{report}`
- **Method**: GET
- **Description**: Retrieve team stats for a specific report.
- **Parameters**:
  - `report` (string) - Team report
  - `lang` (string) - Language code
- **Request Parameters**:
  - `isAggregate` (query, boolean) - Optional
  - `isGame` (query, boolean) - Optional
  - `factCayenneExp` (query, string) - Optional
  - `include` (query, string) - Optional
  - `exclude` (query, string) - Optional
  - `cayenneExp` (query, string) - Optional
  - `sort` (query, string) - Optional
  - `dir` (query, string) - Optional
  - `start` (query, int) - Optional
  - `limit` (query, int) - Optional (**Note:** a limit of -1 will return all results)
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/team/summary?sort=shotsForPerGame&cayenneExp=seasonId=20232024%20and%20gameTypeId=2"
```

### Get Franchise Information
- **Endpoint**: `/{lang}/franchise`
- **Method**: GET
- **Description**: Retrieve list of all franchises.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/franchise"
```



## Season

#### Get Component Season
- **Endpoint**: `/{lang}/componentSeason`
- **Method**: GET
- **Description**: Retrieve component season information.
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/componentSeason"
```

#### Get Season
- **Endpoint**: `/{lang}/season`
- **Method**: GET
- **Description**: Retrieve season information.
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/season"
```


## Game

#### Get Game Information
- **Endpoint**: `/{lang}/game`
- **Method**: GET
- **Description**: Retrieve game information.
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/game"
```

#### Get Game Metadata
- **Endpoint**: `/{lang}/game/meta`
- **Method**: GET
- **Description**: Retrieve metadata for game.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/game/meta"
```




## Miscellaneous

### Configuration

#### Get Configuration
- **Endpoint**: `/{lang}/config`
- **Method**: GET
- **Description**: Retrieve configuration information.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/config"
```

### Ping the Server
- **Endpoint**: `/ping`
- **Method**: GET
- **Description**: Ping the server to check connectivity.
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/ping"
```

### Get Country Information
- **Endpoint**: `/{lang}/country`
- **Method**: GET
- **Description**: Retrieve country information. Returns list of all countries with a hockey presence(?)
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/country"
```


### Get Shift Charts
- **Endpoint**: `/{lang}/shiftcharts?cayenneExp=gameId={game_id}`
- **Method**: GET
- **Description**: Retrieve shift charts for a specific game.
- **Parameters**:
  - `lang` (string) - Language code
  - `game-id` (int) - Game ID
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/shiftcharts?cayenneExp=gameId=2021020001"
```


### Glossary

#### Get Glossary
- **Endpoint**: `/{lang}/glossary`
- **Method**: GET
- **Description**: Retrieve the glossary for a specific language.
- **Parameters**:
  - `lang` (string) - Language code
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/glossary"
```

### Content Module
#### Get Content Module
- **Endpoint**: `/{lang}/content/module/{templateKey}`
- **Method**: GET
- **Description**: Retrieve content module information for a specific template.
- **Parameters**:
  - `lang` (string) - Language code
  - `templateKey` (string) - Template key/name
- **Response**: JSON format

##### Example using cURL:

```bash
curl -X GET "https://api.nhle.com/stats/rest/en/content/module/overview"
```



---

*For the full WADL with extended resources: [WADL Link](https://api.nhle.com/stats/rest/application.wadl?detail=true)*
