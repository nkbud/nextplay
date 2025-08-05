# Phase 1: Data Model Refactor

## Overview
Refactor the GraphQL schema to support sports betting functionality, replacing movie-related types with game events, bets, and user management.

## 1.1 GraphQL Schema Updates

### Core Schema Changes
- [ ] **Replace Movies type with GameEvents type**
  - [ ] Update schema.graphql file
  - [ ] Remove movie-specific fields (name, poster, plot, date)
  - [ ] Add sports-specific fields (gameId, sport, eventType, description, timestamp, player, team, odds, isLive, status)

- [ ] **Replace Reviews type with Bets type**
  - [ ] Remove review-specific fields (type, votes, topMovie, topVotes)
  - [ ] Add betting-specific fields (userId, gameEventId, amount, odds, potentialWinnings, status, createdAt, resolvedAt)

- [ ] **Add Users type for user accounts and balances**
  - [ ] Add fields: id, username, email, balance, totalBets, totalWinnings, createdAt

- [ ] **Add Games type to represent individual games/matches**
  - [ ] Add fields: id, sport, homeTeam, awayTeam, startTime, endTime, status, score

- [ ] **Update Message type to ChatMessage for betting chat**
  - [ ] Add fields: userId, username, message, timestamp

- [ ] **Update subscriptions for real-time betting updates**
  - [ ] Create subscriptions for game events
  - [ ] Create subscriptions for bet updates
  - [ ] Create subscriptions for user balance changes

## 1.2 New Schema Structure

### GameEvents Type
```graphql
type GameEvents @model {
  id: ID!
  gameId: String!
  sport: String! # MLB, NFL, etc.
  eventType: String! # "home_run", "touchdown", "field_goal", etc.
  description: String!
  timestamp: AWSDateTime!
  player: String
  team: String!
  odds: Float
  isLive: Boolean!
  status: String! # "pending", "completed", "cancelled"
}
```

### Bets Type
```graphql
type Bets @model {
  id: ID!
  userId: String!
  gameEventId: String!
  amount: Float!
  odds: Float!
  potentialWinnings: Float!
  status: String! # "pending", "won", "lost", "cancelled"
  createdAt: AWSDateTime!
  resolvedAt: AWSDateTime
}
```

### Users Type
```graphql
type Users @model {
  id: ID!
  username: String!
  email: String!
  balance: Float!
  totalBets: Int!
  totalWinnings: Float!
  createdAt: AWSDateTime!
}
```

### Games Type
```graphql
type Games @model {
  id: ID!
  sport: String!
  homeTeam: String!
  awayTeam: String!
  startTime: AWSDateTime!
  endTime: AWSDateTime
  status: String! # "scheduled", "live", "finished"
  score: String
}
```

### ChatMessage Type
```graphql
type ChatMessage {
  userId: String!
  username: String!
  message: String!
  timestamp: AWSDateTime!
}
```

## 1.3 GraphQL Operations Updates

### Queries to Update
- [ ] **Update listMoviess to listGameEvents**
- [ ] **Update listReviewss to listBets**
- [ ] **Add listUsers query**
- [ ] **Add listGames query**
- [ ] **Add getUser query**
- [ ] **Add getGame query**

### Mutations to Update
- [ ] **Update createMovies to createGameEvent**
- [ ] **Update updateMovies to updateGameEvent**
- [ ] **Update deleteMovies to deleteGameEvent**
- [ ] **Update createReviews to createBet**
- [ ] **Update updateReviews to updateBet**
- [ ] **Add createUser mutation**
- [ ] **Add updateUser mutation**
- [ ] **Add createGame mutation**
- [ ] **Add updateGame mutation**

### Subscriptions to Update
- [ ] **Update onUpdateMovies to onUpdateGameEvent**
- [ ] **Update onCreateMovies to onCreateGameEvent**
- [ ] **Update onDeleteMovies to onDeleteGameEvent**
- [ ] **Update onUpdateReviews to onUpdateBet**
- [ ] **Add onCreateBet subscription**
- [ ] **Add onUpdateUser subscription**
- [ ] **Add onCreateGame subscription**
- [ ] **Add onUpdateGame subscription**

## 1.4 Database Migration Strategy

### Data Migration
- [ ] **Create migration scripts**
  - [ ] Export existing movie data
  - [ ] Transform movie data to game event format
  - [ ] Import transformed data into new schema
  - [ ] Validate data integrity

### Backward Compatibility
- [ ] **Maintain temporary compatibility**
  - [ ] Keep old queries working during transition
  - [ ] Create data transformation layer
  - [ ] Gradually migrate frontend components

## 1.5 Testing Schema Changes

### Unit Tests
- [ ] **Test new GraphQL operations**
  - [ ] Test GameEvents CRUD operations
  - [ ] Test Bets CRUD operations
  - [ ] Test Users CRUD operations
  - [ ] Test Games CRUD operations

### Integration Tests
- [ ] **Test schema relationships**
  - [ ] Test user-bet relationships
  - [ ] Test game-event relationships
  - [ ] Test real-time subscriptions

## 1.6 Documentation Updates

### API Documentation
- [ ] **Update GraphQL documentation**
  - [ ] Document new types and fields
  - [ ] Update query examples
  - [ ] Update mutation examples
  - [ ] Update subscription examples

### Schema Documentation
- [ ] **Create schema documentation**
  - [ ] Document field descriptions
  - [ ] Document relationships between types
  - [ ] Document business rules and constraints

## Dependencies
- AWS AppSync
- GraphQL schema compiler
- DynamoDB tables
- AWS Amplify CLI

## Estimated Time
**2-3 weeks**

## Success Criteria
- [ ] All new GraphQL types are defined and working
- [ ] All CRUD operations are functional
- [ ] Real-time subscriptions are working
- [ ] Data migration is complete
- [ ] Unit tests are passing
- [ ] Documentation is updated 