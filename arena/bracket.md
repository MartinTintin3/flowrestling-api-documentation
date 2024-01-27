# Event Bracket

## Base URL

`https://arena.flowrestling.org`

## Endpoint

`/bracket` fetches the bracket information for a specific event. For duals, only the 

`GET /bracket/{eventId}`

#### Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| eventId | String | ID of the event |

#### Response (In JSON)

```typescript
{
	status: "SUCCESS",
	response: {
		guid: String, // Equivalent to the event ID provided in the request
		name: String, // Name of the event (e.g. "2019 NCAA Division I Wrestling Championships")
		timeZone: String, // Timezone of the event (e.g. "America/New_York")
		startDateTimezone: String, // ISO 8601 timestamp of the event start time in the event's timezone (e.g. "2019-03-21T11:00:00-04:00")
		endDateTimezone: String, // ISO 8601 timestamp of the event end time in the event's timezone (e.g. "2019-03-23T23:00:00-04:00")
		divisions: Array<{ // List of divisions(Aka brackets) in the event. Either Varsity & JV or just High School
			guid: String, // Division ID
			name: String, // Division name (e.g. "Varsity" or "High School" if there is no JV division)
			sequence: Number, // Pretty random, not sure what it means
			isDual: Boolean, // Whether this is a dual bracket or not
			divisionProfile: {
				guid: String, // Division profile ID (unknown purpose)
			},
			maskSeeds: Boolean, // Whether seeds are masked or not
			showSeedsTo: null, // unknown
			hidesByes: Boolean, // Whether byes are hidden or not
			measurementUnit: String, // Measurement unit used in the division (e.g. "lbs")
			firstColor: String, // First color used in a match (Usually "red")
			secondColor: String, // Second color used in a match (Usually "green")
			publishBrackets: Boolean, // Whether brackets are published or not
			publishWrestlersDateTimeUtc: String, // unknown
			bracketPhase: {
				guid: String, // Bracket phase ID (unknown purpose)
				sequenceNumber: Number, // unknown
				segmentSize: Number, // unknown
				segmentFinalsSize: Number, // unknown
			},
			weightClasses: Array<{ // List of all weight class brackets
				guid: String, // Weight class ID
				name: String, // Weight class name (e.g. "113")
				sequence: Number, // Order of the weight class in the division (e.g. 1 for 106, 2 for 113, etc.)
				divisionGuid: String, // Division ID
				boutPools: Array<{ // List of bouts pools (Usually there is only one)
					guid: String, // Bout pool ID
					name: String, // Bout pool name (e.g. "Pool A")
					sequence: Number, // Bout pool sequence (1 for the main pool)
					bracketPhase: {
						guid: String, // Bracket phase ID (unknown purpose)
						sequenceNumber: Number, // unknown
						segmentSize: Number, // unknown
						segmentFinalsSize: Number, // unknown
					},
					bracketPlacements: Array<{ // Placement list of this bracket
						guid: String, // Placement ID
						placement: Number, // Placement number (e.g. 1 for 1st, 2 for 2nd, etc.)
						wrestler: {
							guid: String, // Wrestler ID (Not identityPersonId. Specific to this event)
							firstName: String, // Wrestler first name
							lastName: String, // Wrestler last name
							team: {
								guid: String, // Team ID (Specific to this event)
								name: String, // Team name
								abbreviation: String, // Team abbreviation
								teamLogo: null, // unknown
							},
							weightClass: null, // unknown
							seed: null, // idk
							identityPersonGuid: String, // Wrestler identityPersonId (Global)
						}
					}>
				}>,
			}>,
		}>,
	}
}
```