# FloArena-API Documentation

## Base URL

`https://floarena-api.flowrestling.org`

## Endpoint

Provides a list of bouts about specific wrestlers and other information such as their location, team, and record.

`GET /bouts`

#### Parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `identityPersonId` | `string` | ID of the athlete. |
| `hasResult` | `boolean` | Wether to filter for bouts that have results (true or false). |
| `page[size]` | `integer` | Number of bouts to fetch. |
| `page[offset]` | `integer` | Offset for bout fetching. |
| `fields[wrestler]` | `string` | Fields to include for wrestlers(Any attribute of the `wrestler` object). **Do not add this parameter if you want to fetch EVERY field** |
| `fields[team]` | `string` | Fields to include for teams(Any attribute of the `team` object). **Do not add this parameter if you want to fetch EVERY field** |
| `fields[bout]` | `string` | Fields to include for bouts(Any attribute of the `bout` object). **Do not add this parameter if you want to fetch EVERY field** |
| `include` | `string` | Related resources to include(Any attribute of the `bout` object. Ex: `bottomWrestler.team,topWrestler.team, weightClass,topWrestler.division,bottomWrestler.division`). |

#### Response (In JSON)

```typescript
{
    links: {
        first: String, // URL to the first page of results
        next: String, // URL to the next page of results (page[offset] increases by page[size])
        last: String // URL to the last page of results
    },
    data: Array<{
        type: "bout", // Type of resource (bout)
        id: String, // ID of the bout
        attributes: {
            createdByUserId: String, // ID of the user who created the bout
            createdDateTimeUtc: String, // Date and time the bout was created (UTC format)
            modifiedByUserId: String, // ID of the user who modified the bout
            modifiedDateTimeUtc: String, // Date and time the bout was modified (UTC format)
            bottomWrestlerId: String, // ID of the bottom wrestler
            boutPoolId: String, // ID of the bout pool
            eventId: String, // ID of the event
            mat: String, // ID of the mat
            roundNameId: String, // ID of the round name
            topWrestlerId: String, // ID of the top wrestler
            redWrestler: String, // ID of the red wrestler
            winnerWrestlerId: String, // ID of the winner wrestler
            weightClassId: String, // ID of the weight class
            matchQueueId: String, // ID of the match queue
            dualId: String | null, // ID of the dual (null if not a dual)
            boutNumber: String | null, // Bout number (null if a dual)
            boutNumberSort: String | null, // Bout number sort (null if a dual)
            comments: String | null, // Comments
            goDateTime: String, // Date and time the bout started (UTC format)
            endDateTime: String, // Date and time the bout ended (UTC format)
            isInProgress: Boolean, // Whether the bout is in progress
            isConsolation: Boolean, // Whether the bout is a consolation bout
            isPrinted: Boolean, // Whether the bout is printed
            loserToBoutId: String | null, // ID of the loser to bout (null if not a consolation bout)
            loserToTop: Boolean | null, // Whether the loser to is on top (null if not a consolation bout)
            result: String, // Result of the bout (score and time. ex: "7-2 2:51")
            topWrestlerScore: Integer, // Score of the top wrestler
            bottomWrestlerScore: Integer, // Score of the bottom wrestler
            matchResultTime: String, // Time of the match result (ex: "2:51")
            matchResultPeriod: Integer | null, // Period of the match result (null if not a period)
            roundSpot: Integer, // Round spot 
            bracketSize: Integer, // Bracket size
            trueRound: Integer, // True round
            winnerPoints: Integer, // Points of the winner
            topPlacementPoints: Integer, // Placement points of the top wrestler
            bottomPlacementPoints: Integer, // Placement points of the bottom wrestler
            isPlace: Boolean, // Whether the bout is a place bout
            naturalRound: Integer, // Natural round
            maxPlace: Integer, // Maximum place
            guaranteedPlace: Integer, // Guaranteed place
            sequenceNumber: Integer, // Sequence number
            bracketType: Integer, // Bracket type
            winType: String, // Win type (ex: "F" or "TF")
            winnerToBoutId: String | null, // ID of the winner to bout (null if not a consolation bout)
            winnerToTop: Boolean | null, // Whether the winner to is on top (null if not a consolation bout)
            isTopBye: Boolean, // Whether the top wrestler is a bye
            isBottomBye: Boolean, // Whether the bottom wrestler is a bye
            isRepechageTop: Boolean, // Whether the top wrestler is a repechage
            isConfirmed: Boolean, // Whether the bout is confirmed
            boutVideoUrl: String | null, // URL of the bout video (null if no video)
            segmentNumber: Integer | null, // Segment number (null if not a segment)
            staticSequenceNumber: Integer | null, // Static sequence number (null if not a static sequence)
            publishVideoDateTimeUtc: String | null, // Date and time the video was published (UTC format)
            announcerCalls: String | null // Announcer calls
        },
        relationships: {
            bottomWrestler: {
                data: {
                    type: "wrestler", // Type of resource (wrestler)
                    id: String, // ID of the bottom wrestler
                }
            },
            weightClass: { // Exists only if weightClass field is included for fields[bout]
                data: {
                    type: "weightClass", // Type of resource (weightClass)
                    id: String, // ID of the weight class
                }
            },
            topWrestler: {
                data: {
                    type: "wrestler", // Type of resource (wrestler)
                    id: String, // ID of the top wrestler
                }
            },
        }
    }>,
    included: Array<{ // Each type of resource is included only if it is included in the "include" parameter
        type: "weightClass", // Type of resource (weightClass)
        id: String, // ID of the weight class
        attributes: {
            createdByUserId: String, // ID of the user who created the weight class
            createdDateTimeUtc: String, // Date and time the weight class was created (UTC format)
            modifiedByUserId: String, // ID of the user who modified the weight class
            modifiedDateTimeUtc: String, // Date and time the weight class was modified (UTC format)
            eventId: String, // ID of the event
            divisionId: String, // ID of the division (High School, Varsity, JV, etc.)
            name: String, // Name of the weight class (ex: "126")
            sequence: Integer, // Sequence number
            minWeight: Float, // Minimum weight
            maxWeight: Float, // Maximum weight
            maxWrestlerCount: Integer | null, // Maximum number of wrestlers (null if no maximum)
        },
    } | {
        type: "wrestler", // Type of resource (wrestler)
        id: String, // ID of the wrestler (Not the same as the identityPersonId)
        attributes: {
            identityPersonId: String, // ID of the athlete
            createdByUserId: String, // ID of the user who created the wrestler
            createdDateTimeUtc: String, // Date and time the wrestler was created (UTC format)
            modifiedByUserId: String, // ID of the user who modified the wrestler
            modifiedDateTimeUtc: String, // Date and time the wrestler was modified (UTC format)
            teamId: String, // ID of the team the wrestler is on
            eventId: String, // ID of the event
            divisionId: String, // ID of the division (High School, Varsity, JV, etc.)
            gradeId: String, // ID of the grade
            weightClassId: String, // ID of the weight class
            otbId: Integer, // ID of the wrestler (custom to the event)
            firstName: String, // First name
            lastName: String, // Last name
            bracketSpot: Integer | null, // Bracket spot (null if not in a bracket)
            city: String, // City
            zipCode: String, // Zip code
            state: String, // State
            dateOfBirth: null, // unknown
            gender: null, // unknown
            exactWeight: Float, // Weight at weigh-ins
            exactWeight2: null, // unknown
            exactWeight3: null, // unknown
            paid: Boolean, // Whether the wrestler has paid
            withdrawn: Boolean, // Whether the wrestler has withdrawn
            isSkinChecked: Boolean, // Whether the wrestler has been skin checked
            isTeamScorer: Boolean, // Whether the wrestler is a team scorer
            nwcaId: null, // unknown
            opcNumber: null, // unknown
            previousPlace: null, // unknown
            record: String, // Record (ex: "20-8")
            seed: Integer | null, // Seed in event(null if not seeded)
            draw: null, // unknown
            seedingCriteria1: null, // unknown
            seedingCriteria2: null, // unknown
            seedingCriteria3: null, // unknown
            seedingCriteria4: null, // unknown
            seedingCriteria5: null, // unknown
            custom1: null, // unknown
            custom2: null, // unknown
            usaWrestlingCardNum: null, // unknown
            isWeighInOk: Boolean, // Whether the wrestler has weighed in
            regionPlace: null, // unknown
            sectionPlace: null, // unknown
            onlineRegistrationStatus: String, // Online registration status (ex: "complete")
            nickname: null, // unknown
            source: String, // Source (ex: "online-registration")
            skillLevelId: null, // unknown
            tier: null, // unknown
            exempt: null, // unknown
            comments: null, // unknown
            location: {
                id: String, // ID of the location
                name: String, // Name of the location
                address: null, // unknown
                googlePlaceId: String, // Google place ID
                city: String, // City
                state: String, // State
                country: String, // Country
                latitude: Float, // Latitude
                longitude: Float, // Longitude
                zipCode: String, // Zip code
            },
            fullName: String, // Full name (Last name, First name)
            grade: {
                type: "grade", // Type of resource (grade)
                id: String, // ID of the grade
                attributes: {
                    name: String, // Name of the grade (ex: "HS Freshman")
                    sequence: Integer, // Sequence number
                    numericValue: Integer, // Numeric value (ex: 9 for HS Freshman)
                }
            },
        },
        relationships: {
            team: {
                data: {
                    type: "team", // Type of resource (team)
                    id: String, // Team ID
                }
            },
            division: {
                data: {
                    type: "division", // Type of resource (division)
                    id: String, // Division ID
                }
            }
        }
    } | {
        type: "team", // Type of resource (team)
        id: String, // ID of the team
        attributes: {

        }
    } | {

    }>,
    meta: {
        total: Integer // Total number of bouts (length of data array)
    },
}
```