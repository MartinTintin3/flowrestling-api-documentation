# FloArena-API Documentation

## Base URL

`https://arena.flowrestling.org`

## Endpoint

[GET /bracket/{eventId}](./bracket.md) - Fetch bracket information for a specific event. **Does not return match results if the event is a dual**

[GET /event/{eventId}/team-scores-groups](./event/team-scores-groups.md) - Fetches list of groups of team scores for a specific event. This is required to fetch team scores for a specific event. Use the `guid` attribute of the response to fetch the actual [team scores](./event/team-scores/search.md)

[GET /event/{eventId}/team-scores/search?group={groupGuid}](./event/team-scores/search.md) - Fetches team scores for a specific scoring group of a specific event.