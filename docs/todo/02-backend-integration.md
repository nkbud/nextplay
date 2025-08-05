# Phase 2: Backend Integration

## Overview
Integrate external sports data sources (MLB Baseball Savant, NFL APIs), normalize incoming data, and set up a real-time data pipeline for live game events and betting updates.

## 2.1 External API Integration

### MLB Baseball Savant Integration
- [ ] Set up API credentials and authentication
- [ ] Create Lambda functions to fetch live MLB game data
- [ ] Parse and transform Baseball Savant data into GameEvents
- [ ] Handle different event types (hits, runs, errors, etc.)

### NFL Data Integration
- [ ] Research and select NFL data provider (ESPN, NFL.com, etc.)
- [ ] Set up API credentials and authentication
- [ ] Create Lambda functions for NFL data fetching
- [ ] Parse NFL game events (touchdowns, field goals, etc.)
- [ ] Handle NFL-specific event types

### Data Normalization
- [ ] Create unified event format across all sports
- [ ] Implement event type mapping
- [ ] Handle timezone conversions
- [ ] Implement data validation and error handling

## 2.2 Real-time Data Pipeline

### Event Streaming
- [ ] Set up AWS EventBridge for real-time event processing
- [ ] Create Lambda functions to process incoming sports data
- [ ] Implement event filtering and transformation
- [ ] Set up DynamoDB streams for real-time updates

### WebSocket Management
- [ ] Update AppSync subscriptions for game events
- [ ] Implement user-specific betting notifications
- [ ] Handle connection management for live betting

## Dependencies
- AWS Lambda
- AWS EventBridge
- AWS AppSync
- DynamoDB Streams
- External sports APIs (MLB, NFL)

## Estimated Time
**2-3 weeks**

## Success Criteria
- [ ] Live sports data is ingested and normalized
- [ ] Real-time events are streamed to the frontend
- [ ] WebSocket connections deliver timely updates
- [ ] Lambda functions are tested and reliable 