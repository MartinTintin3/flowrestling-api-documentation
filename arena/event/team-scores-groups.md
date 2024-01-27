# FloArena-API Documentation

## Base URL

`https://arena.flowrestling.org`

## Endpoint

Fetches list of groups of team scores for a specific event. Required to fetch team scores for a specific event. Use the `guid` attribute of the response to fetch the actual [team scores](./team-scores/search.md)

`GET /event/{eventId}/team-scores-groups`

#### Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| eventId | String | ID of the event |

#### Response (In JSON)

```typescript
{
	status: "SUCCESS",
	response: Array<{ // Usually there is only one group (Ex. "High School" or "Varsity")
		guid: String, // ID of the team group
		name: String, // Name of the team group (Ex. "High School" or "Varsity")
		placesAwarded: Number, // Number of places awarded in the team group
		divisionGuids: String, // ID of the division the team group is in
	}>
}
```