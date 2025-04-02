# Survey April 2025

## Demographics

- Where do you currently live? (countries list)
  - Country

- How long have you been working with Node.js? (numbers list from 0 to 15+)

- In what kind of organizations are you working in?
  - Big tech
  - Company
  - Startup
  - Academia (school, university..)
  - Government
  - NGO (no profit)
  - Individual/Freelance
  - Other

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

- Which of the following best reflects your role regarding Node.js? (multiple choice)
  - Node.js core maintainers: Developers working directly on Node.js, individuals participating in Working Groups
  - Library & package authors: Users who write libraries and packages to be included on other applications
  - Application developers: Frontend
  - Application developers: backend server authors
  - Application developers: fullstack (front end and back end)
  - Application developers: tools authors
  - Direct end users: Users who run tools themselves
  - Application operators: Service and infrastructure providers
  
- How does your organization invest in JavaScript related projects ?
  - sponsors your time to work in the Node.js project
  - sponsors your time to work in JavaScript projects other than Node.js
  - sponsors Node.js directly through crowdfunding (for example, GitHub sponsors or Open Collective)
  - sponsors JavaScript packages in the ecosystem through crowdfunding (for example, GitHub sponsors or Open Collective)
  - through membership in the OpenJS foundation
  - other
  - none

- What is your use cases of Node.js ? (multiple choice) (open question - Other should give an input)
  - Cli tools
  - Testing
  - Development of APIs with Microservices
  - Development of APIs with Serverless
  - Development of APIs with Other
  - Tooling used to build front end applications
  - Full stack development (Next.js, Remix, etc...)
  - Implementing desktop applications (ex electron based applications)
  - Mobile applications 
  - Script and automation (bots, scrapers)
  - Http proxy
  - IoT/Edge devices
  - other

## What Node.js binaries do you use

- What is your Operating System for your local development environment ? (multiple choice - Other should give an input)
  - Linux
  - Windows
  - macOS
  - Linux with Docker
  - Windows with Docker
  - macOS with Docker
  - Windows with WSL
  - Android
  - Other?

- What is your Operating System in which you are running Node.js in production ? (multiple choice - Other should give an input)
  - Linux/Unix
  - Windows
  - macOS
  - Linux with Docker
  - Windows with Docker
  - macOS with Docker
  - Android
  - Serveless
  - Unknown
  - Other?

- What architecture is the machine you are running Node.js in production? (multiple choice - Other should give an input)
  - x64
  - x32
  - arm
  - Don't know
  - Other?

- How do you get your `node` executables? (multiple choice – Other should give an input)
  - With a Node.js version manager: nvm, n, nave, nvs, volta, mise, asdf, etc.
  - Using the official installer
  - Using package managers like npm or yarn and install Node.js as a package
  - Using a system package manager: apt-get, brew, dnf, yum …
  - Downloading binaries directly from Nodejs.org
  - Building Node.js from Source
  - Docker Image
  - Other

- What package manager do you use ? (multiple choice - Other should give an input)
  - npm
  - yarn v1
  - yarn modern (2+)
  - pnpm
  - bun
  - Other?

- Which version manager do you use (multiple choice - Other should give an input)
  - none
  - nvm
  - n
  - asdf
  - fnm
  - nodenv
  - volta
  - pnpm
  - Other?

- How do you manage the package manager for your project? (multiple choice – Other should give an input)
  - I use one version installed globally for all my projects.
  - I use a tool to pick a specific version per project (e.g. Corepack, asdf, …).
  - I use containers.
  - Other?

## Project Priorities and Direction

- Which of the current [Technical Priorities](https://github.com/nodejs/node/blob/main/doc/contributing/technical-priorities.md) are important to you ? (multiple choice)
  - Modern HTTP (HTTP3, quic)
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
  - Native Addons
  - Performance

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

- Are you using the following experimental features of Node.js (multiple choice)?
  - Corepack
  - Async Hooks Module (`node:async_hooks`)
  - Single Executable Application
  - Startup Snapshot
  - Loader hooks
  - WASI
  - VM Modules
  - Dotenv (`--env-file`)
  - TypeScript support
  - Shadow Realm
  - Test Coverage
  - Module Mocking
  - Web Storage
  - SQLite
  - Require(ESM)
  - Config File (`node.config.json`)
  - Glob
  - zstd

- Are you using the following new stable features (multiple choice):
  - Import attributes
  - WebSocket client
  - Watch mode (`--watch`)
  - Permission model
  - Test runner (`node:test`)
  - Test Snapshot
  - Task runner (`--run`)
  - Diagnostic APIs (`--cpu-prof`, `--heap-prof`, etc...)

- Do you encounter any recurring issues when using Node.js that you would like to share with us ? (open question)
