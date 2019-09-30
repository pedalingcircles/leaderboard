# PRISTIGE leaderboard - Specification

### Summary
Prestige is a tool that accepts a set of Strava segments as input and returns a list of Strava athletes who have completed each of the segments on a given day, displays their segment times, tallies their combined time across all segments, and calculates the gap between the athlete with the fastest combined time and all other athletes. The output can be set to provide lists of Male or Female athletes. Output is tabular / tab-delimited and easily imported to common spreadsheet applications. 

---

### Inputs
- The tool should able to accept a set of N Strava segment identifiers (e.g. URLs, IDs)
- The tool should be able to accept an input setting the results returned to include either Male or Female athletes, based on their Strava profile data. This would allow the user to easily produce Mens and Womens results.
- Optionally, users may be able to set the results returned to come from a specific Strava club. This would allow the user to limit results to participants in a given event.

### Outputs
- Tabular or tab-delimited text output
- Results will be limited to efforts on the current day (per API limitation)
- Header row
  * Place
  * Athlete Name
  * Segment Name (N columns)
    * Optionally, web output links to the segment on Strava
  * Overall Time
  * Gap

### Example outputs
https://docs.google.com/spreadsheets/d/1yz6ssraV0ZNHQGnxOu4KVDfcsVLRQsw37y6mZfVq5iU/edit#gid=0



