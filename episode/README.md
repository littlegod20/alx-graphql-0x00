# Episode GraphQL Queries

This directory contains GraphQL queries to fetch specific episode information from the Rick and Morty GraphQL API.

## Endpoint

**GraphQL API Endpoint:** `https://rickandmortyapi.com/graphql`

## Files

### Query Files

- `episode-id-1.graphql` - Query to fetch episode with ID 1 (Pilot)
- `episode-id-2.graphql` - Query to fetch episode with ID 2 (Lawnmower Dog)
- `episode-id-3.graphql` - Query to fetch episode with ID 3
- `episode-id-4.graphql` - Query to fetch episode with ID 4

### Output Files

- `episode-id-1-output.json` - Expected output for episode ID 1
- `episode-id-2-output.json` - Expected output for episode ID 2
- `episode-id-3-output.json` - Expected output for episode ID 3
- `episode-id-4-output.json` - Expected output for episode ID 4

## Query Structure

Each query uses the `episode(id: ID!)` field to fetch a specific episode by its ID. The queries include the following fields:

- `id` - The episode's unique identifier
- `name` - The episode's name
- `air_date` - The date when the episode was first aired
- `episode` - The episode code (e.g., "S01E01" for Season 1, Episode 1)

## Usage

### Using cURL

```bash
curl -X POST https://rickandmortyapi.com/graphql \
  -H "Content-Type: application/json" \
  -d @episode-id-1.graphql
```

Or with inline query:

```bash
curl -X POST https://rickandmortyapi.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query":"query { episode(id: 1) { id name air_date episode } }"}'
```

### Using GraphQL Playground or Other GraphQL Clients

1. Open your GraphQL client
2. Set the endpoint to: `https://rickandmortyapi.com/graphql`
3. Copy the query from one of the `.graphql` files
4. Execute the query

### Example Query

```graphql
query {
  episode(id: 1) {
    id
    name
    air_date
    episode
  }
}
```

### Example Response

```json
{
  "data": {
    "episode": {
      "id": "1",
      "name": "Pilot",
      "air_date": "December 2, 2013",
      "episode": "S01E01"
    }
  }
}
```

## Notes

- Episode IDs are integers, but returned as strings in the GraphQL response
- The `episode` field follows the format "S##E##" where the first number is the season and the second is the episode number
- The `air_date` field is returned as a formatted date string
- All queries use the same field structure for consistency
