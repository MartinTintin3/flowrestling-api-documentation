# Wrestler

## Base URL

`https://floarena-api.flowrestling.org`

## Endpoint

Fetches a list of all wrestlers with the given identityPersonId from different events

`GET /wrestlers`

#### Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `identityPersonId` | `string` | ID of the athlete |
| `orderBy` | `string` | Attribute to order by (eventEndDateTime recomended) |
| `orderDirection` | `string` | Direction to order by (asc or desc. Desc for most recent to be first) |
| `page[size]` | `integer` | Number of instances to fetch |
| `page[offset]` | `integer` | Offset for fetching |
| `fields[wrestler]` | `string` | Fields to include for wrestlers(Any attribute of the `wrestler` object). **Do not add this parameter if you want to fetch EVERY field** |
| `fields[team]` | `string` | Fields to include for teams(Any attribute of the `team` object). **Do not add this parameter if you want to fetch EVERY field** |
| `fields[division]` | `string` | Fields to include for divisions(Any attribute of the `division` object). **Do not add this parameter if you want to fetch EVERY field** |
| `fields[event]` | `string` | Fields to include for events(Any attribute of the `event` object). **Do not add this parameter if you want to fetch EVERY field** |
| `include` | `string` | Related resources to include(Any relationship of the `wrestler` object. Ex: `bracketPlacements.weightClass,division,event,weightClass,team`). |

#### Response (In JSON)

```typescript
{
	
}
```