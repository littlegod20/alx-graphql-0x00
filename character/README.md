# Character GraphQL Queries

This directory contains GraphQL queries to fetch specific character information from the Rick and Morty GraphQL API.

## Endpoint

**GraphQL API Endpoint:** `https://rickandmortyapi.com/graphql`

## Files

### Query Files

- `character-id-1.graphql` - Query to fetch character with ID 1 (Rick Sanchez)
- `character-id-2.graphql` - Query to fetch character with ID 2 (Morty Smith)
- `character-id-3.graphql` - Query to fetch character with ID 3 (Summer Smith)
- `character-id-4.graphql` - Query to fetch character with ID 4 (Beth Smith)

### Output Files

- `character-id-1-output.json` - Expected output for character ID 1
- `character-id-2-output.json` - Expected output for character ID 2
- `character-id-3-output.json` - Expected output for character ID 3
- `character-id-4-output.json` - Expected output for character ID 4

## Query Structure

Each query uses the `character(id: ID!)` field to fetch a specific character by their ID. The queries include the following fields:

- `id` - The character's unique identifier
- `name` - The character's name
- `status` - The character's status (Alive, Dead, or unknown)
- `species` - The character's species
- `type` - The character's type or subspecies
- `gender` - The character's gender

## Usage

### Using cURL

```bash
curl -X POST https://rickandmortyapi.com/graphql \
  -H "Content-Type: application/json" \
  -d @character-id-1.graphql
```

Or with inline query:

```bash
curl -X POST https://rickandmortyapi.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query":"query { character(id: 1) { id name status species type gender } }"}'
```

### Using GraphQL Playground or Other GraphQL Clients

1. Open your GraphQL client
2. Set the endpoint to: `https://rickandmortyapi.com/graphql`
3. Copy the query from one of the `.graphql` files
4. Execute the query

### Example Query

```graphql
query {
  character(id: 1) {
    id
    name
    status
    species
    type
    gender
  }
}
```

### Example Response

```json
{
  "data": {
    "character": {
      "id": "1",
      "name": "Rick Sanchez",
      "status": "Alive",
      "species": "Human",
      "type": "",
      "gender": "Male"
    }
  }
}
```

## Notes

- The `type` field may be an empty string for characters without a specific type or subspecies
- Character IDs are integers, but returned as strings in the GraphQL response
- All queries use the same field structure for consistency
