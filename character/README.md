# Character GraphQL Queries

This directory contains GraphQL queries to fetch character information from the Rick and Morty GraphQL API, including both individual character queries and paginated character list queries.

## Endpoint

**GraphQL API Endpoint:** `https://rickandmortyapi.com/graphql`

## Files

### Query Files

#### Single Character Queries

- `character-id-1.graphql` - Query to fetch character with ID 1 (Rick Sanchez)
- `character-id-2.graphql` - Query to fetch character with ID 2 (Morty Smith)
- `character-id-3.graphql` - Query to fetch character with ID 3 (Summer Smith)
- `character-id-4.graphql` - Query to fetch character with ID 4 (Beth Smith)

#### Paginated Character List Queries

- `characters-page-1.graphql` - Query to fetch characters from page 1
- `characters-page-2.graphql` - Query to fetch characters from page 2
- `characters-page-3.graphql` - Query to fetch characters from page 3
- `characters-page-4.graphql` - Query to fetch characters from page 4

### Output Files

#### Single Character Outputs

- `character-id-1-output.json` - Expected output for character ID 1
- `character-id-2-output.json` - Expected output for character ID 2
- `character-id-3-output.json` - Expected output for character ID 3
- `character-id-4-output.json` - Expected output for character ID 4

#### Paginated Character List Outputs

- `characters-page-1-output.json` - Expected output for page 1
- `characters-page-2-output.json` - Expected output for page 2
- `characters-page-3-output.json` - Expected output for page 3
- `characters-page-4-output.json` - Expected output for page 4

## Query Structure

### Single Character Queries

Each query uses the `character(id: ID!)` field to fetch a specific character by their ID. The queries include the following fields:

- `id` - The character's unique identifier
- `name` - The character's name
- `status` - The character's status (Alive, Dead, or unknown)
- `species` - The character's species
- `type` - The character's type or subspecies
- `gender` - The character's gender

### Paginated Character List Queries

Each query uses the `characters(page: Int)` field to fetch a paginated list of characters. The queries include the following fields in the `results` array:

- `id` - The character's unique identifier
- `name` - The character's name
- `status` - The character's status (Alive, Dead, or unknown)
- `image` - URL to the character's image/avatar

## Usage

### Using cURL

#### Single Character Query

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

#### Paginated Character List Query

```bash
curl -X POST https://rickandmortyapi.com/graphql \
  -H "Content-Type: application/json" \
  -d @characters-page-1.graphql
```

Or with inline query:

```bash
curl -X POST https://rickandmortyapi.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query":"query { characters(page: 1) { results { id name status image } } }"}'
```

### Using GraphQL Playground or Other GraphQL Clients

1. Open your GraphQL client
2. Set the endpoint to: `https://rickandmortyapi.com/graphql`
3. Copy the query from one of the `.graphql` files
4. Execute the query

### Example Queries

#### Single Character Query

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

#### Paginated Character List Query

```graphql
query {
  characters(page: 1) {
    results {
      id
      name
      status
      image
    }
  }
}
```

### Example Responses

#### Single Character Response

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

#### Paginated Character List Response

```json
{
  "data": {
    "characters": {
      "results": [
        {
          "id": "1",
          "name": "Rick Sanchez",
          "status": "Alive",
          "image": "https://rickandmortyapi.com/api/character/avatar/1.jpeg"
        },
        {
          "id": "2",
          "name": "Morty Smith",
          "status": "Alive",
          "image": "https://rickandmortyapi.com/api/character/avatar/2.jpeg"
        }
      ]
    }
  }
}
```

## Notes

- The `type` field may be an empty string for characters without a specific type or subspecies
- Character IDs are integers, but returned as strings in the GraphQL response
- All single character queries use the same field structure for consistency
- Paginated character list queries return an array of characters in the `results` field
- Each page typically contains 20 characters
- The `image` field contains the full URL to the character's avatar image
