## Architecture Overview 

This document details the architecture of PackFuture, highlighting design principles, folder structure, and key patterns used to ensure maintainability, performance, and scalability.

## High-Level Structure

```
pack-future/
├─ app/             
│  ├─ (home)                  # /
│  │  ├─ AboutUs.tsx
|  |  └─ ...etc     
│  ├─ consulting/             # /consulting    
│  │  ├─ page.tsx       
│  ├─ recruiting/             # /recruiting
|  |  ├─ page.tsx
│  ├─ automation_materials/   # /automation_materials              
│  │  ├─ page.tsx
|  ├─ contatct/               # /contact
|  |   ├─ page.tsx
│  └─ api/                
│     └─ submit
|      └─ route.ts         
├─ compoents/                 # Reusable + page-level components     
├─ store/                     # State managment
├─ img/                       # Static assets
└─ utils/                     # Helpers 
```
---
## Routing & Route Groups

The application uses the Next.js App Router for file-based routing.

Route groups are used minimally in this project. A single route group, (home), is used to organize the landing page without affecting the URL structure.


The (home) directory contains multiple section-based components (such as hero sections and service overviews) that together compose the main landing page.

This approach keeps the root route clean while allowing the homepage to be structured into smaller, maintainable pieces.

All other routes (consulting, recruiting, automation_materials, contact) follow standard file-based routing using page.tsx.


## Component Architecture

Pages are intentionally kept lightweight and act primarily as composition layers.

Each page imports and assembles smaller, focused components rather than containing large amounts of logic directly.

This approach provides:

- improved readability
- easier testing and reuse
- better scalability as features grow

Reusable components are stored in the components/ directory, while page-specific sections remain close to their respective routes.

## API Layer

Server-side logic is handled through Next.js API routes located in app/api/.

For example:

- /api/submit handles form submissions

This keeps backend logic colocated with the frontend while maintaining a clear separation between UI and server-side processing.
