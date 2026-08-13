# Hello World API — Design

## Overview

A single, minimal Ballerina service exposes one public HTTP endpoint that returns a fixed greeting message. It has no authentication, no persistence, no dependencies, and no other components — the entire system is one deployable service serving one story.

## Context (C1)

```mermaid
graph TD
    consumer["API Consumer"]
    system(("Hello World API"))

    consumer -->|"HTTP GET"| system
```

## Domain model (ER)

```mermaid
erDiagram
    GREETING {
        string message
    }
```

The greeting is a fixed, stateless value — not a persisted entity — so the model above exists only to describe the shape of the response body.

## Key flows

```mermaid
sequenceDiagram
    participant Consumer as API Consumer
    participant API as Hello World API

    Consumer->>API: GET /greeting
    API-->>Consumer: 200 OK { "message": "Hello, World!" }
```