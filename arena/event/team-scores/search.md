# Team Scores

## Base URL

`https://arena.flowrestling.org`

## Endpoint

Fetches team scores for a specific scoring group of a specific event.

`GET /event/{eventId}/team-scores/search?group={groupGuid}`

#### Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| eventId | String | ID of the event |
| groupGuid | String | ID of the team scoring group (Found using the [team-scores-groups](../team-scores-groups.md) endpoint) |

#### Response (In JSON)

```typescript
{
	status: "SUCCESS",
	response: Array<{ // List of teams and their scores/placements
		guid: String, // unknown
		rank: Number, // Rank (aka place) of the team
		score: Float, // Score of the team
		champSide: null, // unknown
		conSide: null, // unknown
		place1: Number, // Number of first place finishes
		...
		place16: Number, // Number of sixteenth place finishes
		team: { // Team information
			guid: String, // Team ID
			name: String, // Team name
		}
	}>
}
```