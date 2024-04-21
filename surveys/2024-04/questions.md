# Survey April 2024

## Demographics

- Where are you from? (countries list if possible - or open question)
  - Country

- How long have you been working with Node.js? (numbers list from 0 to 10+)

- In what kind of organizations are you working in?
  - big tech
  - company
  - startup
  - university
  - individual
  - other

- If working in a company, in which sector does your company operate? (single choice - Other should give an input)
  - Energy
  - Materials
  - Industrials
  - Health Care
  - Financials
  - Information Technology
  - Communication Services
  - Utilities
  - Real Estate
  - Other?

## Node.js Usage

- Which groups do you identify with? (multiple choice)
  - Direct end users: Users who run tools themselves
  - Application operators: Service and infrastructure providers
  - Application developers: Frontend tools consumers, backend server authors, tools authors
  - Library & package authors: Users who write libraries and packages to be included on other applications
  - Node.js core maintainers: Developers working directly on Node.js, individuals participating in Working Groups
  - Organization with investments in Node.js (eg: Enterprises, Gouvernement bodies, Startups, Non-profit, Education, Security)

- Are you part of a group not covered ? If yes which one ? (open question)

- What is your use cases of Node.js ? (multiple choice) (open question - Other should give an input)
  - Cli tools
  - Testing
  - Development of APIs with Microservices
  - Development of APIs with Serverless
  - Development of APIs with Other
  - Building static front end applications
  - Deploying front end applications (Next.js, Remix, etc...)
  - Script and automation (bots, scrapers)
  - Proxy
  - other

## What Node.js binaries do you use

- What is your Operating System for your local development environment ? (single choice - Other should give an input)
  - Linux
  - Windows
  - macOS
  - Linux with Docker
  - Windows with Docker
  - macOS with Docker
  - Windows with WSL
  - Other?

- What is your Operating System in which you are running Node.js in production ? (multiple choice - Other should give an input)
  - Linux/Unix
  - Windows
  - macOS
  - Linux with Docker
  - Windows with Docker
  - macOS with Docker
  - Other?

- What architecture is the machine you are running Node.js in production? (multiple choice - Other should give an input)
  - x64
  - x32
  - arm
  - ppc
  - s390
  - Don't know
  - Other?

- How do you get your `node` executables? (multiple choice – Other should give an input)
  - With a Node.js version manager: nvm, n, nave, nvs, volta, etc.
  - Using the official installer
  - Using package managers like npm or yarn and install Node.js as a package
  - Using a system package manager: apt-get, brew, dnf, yum …
  - Downloading binaries directly from Nodejs.org
  - Building Node.js from Source
  - Other

- What package manager do you use ? (multiple choice - Other should give an input)
  - npm
  - yarn v1
  - yarn modern (2+)
  - cnpm
  - pnpm
  - Other?

- Which version manager do you use (multiple choice - Other should give an input)
  - none
  - nvm
  - n
  - asdf
  - fnm
  - nodenv
  - nvs
  - volta
  - Other?

- How do you manage the package manager for your project? (multiple choice – Other should give an input)
  - I use one version installed globally for all my projects.
  - I use a tool to pick a specific version per project (e.g. Corepack, asdf, …).
  - I use containers.
  - Other?

## Project Priorities and Direction

- Which of the current [Technical Priorities](https://github.com/nodejs/node/blob/main/doc/contributing/technical-priorities.md) are important to you ? (multiple choice)
  - Modern HTTP
  - Suitable types for end-users
  - Documentation
  - WebAssembly
  - ESM
  - Support for features from the latest ECMAScript spec
  - Observability
  - Permissions/policies/security model
  - Better multithreaded support
  - Single Executable Applications
  - TypeScript Support

- Are there technical priorities that you believe are missing (open question)

- What is important to you ? (multiple choice)
  - Good understanding of the direction of the project
  - Ability to affect the direction of the project
  - Consumable APIs and docs
  - Predictable and stable releases
  - Innovation at a consumable pace
  - Easy Installation
  - Easy issue reporting, resolution and collaboration
  - Broad deployment platform support
  - Broad development platform support
  - Consistent and intuitive error handling
  - Runtime diagnostic tooling
  - Development time diagnostic tooling
  - Relevant APIs in core
  - Module/dependency info and management
  - Ways to fund their work
  - Reasonable resource usage/performance
  - Good security and CVE practices
  - Good CI infrastructure and experience in the project
  - Supportive Collaborators and Environment in the project
  - Better ways to build consensus in the project
  - Easy contribution workflow
  - Ability to embed and bundle the Node.js runtime
  - A well maintained and secure standard library
  - Assets that show Node.js is a good choice

- What is important to you that is not in this list? (open question)

## Technical Questions

- Regardless of how your code is written in its original form, when it runs in production, does it contain ES module syntax (`import`/`export`)?
  - Yes
  - No

- For those of you wishing to use ESM in an existing application, what have been the pain points or blockers preventing you from doing so (if any)? (open question)

- Are you using the following experimental features of Node.js (multiple choice)?
  - Corepack
  - Async Hooks
  - Permission model / Policies
  - Single Executable Application
  - Startup Snapshot
  - Loader hooks (`--loader` or `module.register()`)
  - Network import (`import 'http://...'`)
  - WASI
  - VM Modules (`--experimental-vm-modules`)
  - Watch mode (`--watch`)
  - WebSocket client
  - Trace events (`--trace-event-categories` or `node:trace_events`)
  - Dotenv (`--env-file`)
  - Import attributes

- Are you using the following new stable features (multiple choice):
- Test runner (`node:test`)
- Web Crypto (`globalThis.crypto` or `crypto.webcrypto`)
- Web Streams (`node:stream/web`)
- Fetch

- Do you encounter any recurring issues when using Node.js that you would like to share with us ? (open question)
