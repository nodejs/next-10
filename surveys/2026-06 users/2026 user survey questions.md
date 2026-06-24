# Next-10 2026 User Survey Questions

## About you

1. Where do you currently live? (drop-down list of countries)
1. What is your primary language? (drop-down list)
1. In what type of organization is your primary occupation? (drop-down list)
    * Academia (school, university..)
    * B-Corporation
    * Charity or Non-profit
    * Company (For-profit)
    * Government
    * Non-Governmental Organization (NGO)
    * Self-employed (Freelance, Sole Propritorship, etc)
    * Unemployed
    * Other
1. If working in a company, in which sector does your company operate? (drop-down list)
    * Agricultural tech
    * Communication Services
    * Energy
    * Financials
    * Health Care
    * Industrials
    * Information Technology
    * Materials
    * Real Estate
    * Utilities
    * Other

    If answered org type (and not "Unemployed") or answered company sector:
    1. What is the number of employees/member of the organization you are part of? (drop-down list)
      * 1 to 9
      * 10 to 99
      * 100 to 499
      * 500 to 999
      * 1000+

## Node.js features

1. Which of the following new stable features? (select all that apply)
    - [ ] Diagnostic APIs (`--cpu-prof`, `--heap-prof`, etc…)
    - [ ] Dotenv (`--env-file`)
    - [ ] Import attributes
    - [ ] Permission model
    - [ ] Task runner (--run)
    - [ ] Test runner (node:test)
    - [ ] Test Snapshot
    - [ ] TypeScript support
    - [ ] Watch mode (--watch)
    - [ ] WebSocket client
1. Are you using the following unstable (experimental or active development) features of Node.js? (select all that apply)
    - [ ] Async Hooks module (`node:async_hooks`)
    - [ ] Config File (`node.config.json`)
    - [ ] Foreign Function Interface (`node:ffi`)
    - [ ] FS FileHandle Pull
    - [ ] FS FileHandle Writer
    - [ ] FS Utf8Stream (`node:fs.Utf8Stream`)
    - [ ] Glob (`fs.glob`)
    - [ ] Module findPackageJSON
    - [ ] Module Loader / Customization hooks - async (`module.register`)
    - [ ] Module Loader / Customization hooks - sync (`module.registerHooks`)
    - [ ] Iterable Streams (`node:stream/iter`)
    - [ ] QUIC/HTTP3
    - [ ] Require(ESM)
    - [ ] Shadow Realm
    - [ ] Single Executable Application
    - [ ] Startup Snapshot
    - [ ] SQLite
    - [ ] Test Coverage
    - [ ] Test Module Mocking
    - [ ] Test Watch Mode
    - [ ] V8 SyncHeapProfileHandle
    - [ ] VM Modules
    - [ ] WASI
    - [ ] WorkerThread locks
    - [ ] Web Storage
    - [ ] Zstd
1. Which of the current Technical Priorities are important to you? (select all that apply)
1. Do you use Alpine builds?
    * Yes
    * No

    1. Should Alpine support be official?
        * Yes
        * No
1. What capabilities do you feel Node.js is lacking? (free response)
1. Are there any key features that you think should be added to Node.js? (free response)
1. Do you encounter any recurring issues when using Node.js that you would like to share with us? (free response)

## Dev environment

1. With what regularity do you/your company update Node.js versions? (drop-down list)
    * Evergreen (as soon as a new version is available)
    * Evergreen (delayed to await patches, etc)
    * Monthly
    * Quarterly
    * Semi-annually
    * Annually
    * Longer
    * When forced (e.g. AWS stops supporting your ancient version)
1. How long have you been using Node.js? (drop-down list)
    * <1 year
    * 1–4 years
    * 5–10 years
    * >10 years
1. How do you get your Node executables? (select all that apply)
    - [ ] Building Node.js from Source
    - [ ] Docker Image
    - [ ] Downloading binaries directly from Nodejs.org
    - [ ] Using a system package manager: apt-get, brew, dnf, yum …
    - [ ] Using package managers like npm or yarn and install Node.js as a package
    - [ ] Using the official installer
    - [ ] With a Node.js version manager: nvm, n, nave, nvs, volta, mise, asdf, etc.
    - [ ] Other

    If selected "With a Node.js version manager":

    1. Which node version manager do you use? (drop-down list)
1. Which package manager do you use? (drop-down list)
    * bun
    * npm
    * pnpm
    * volta
    * yarn v1
    * yarn v2+
1. How do you manage the package manager for your project? (drop-down list)
    * Containers
    * One version installed globally for all projects
    * A tool to pick a specific version per project (e.g. asdf, Corepack, …).
    * Other: (free response)
1. Which of the following best reflects your role regarding Node.js? (drop-down list)
    * Application developer (backend server authors)
    * Application developer (Frontend)
    * Application developer (fullstack (front end and back end))
    * Application developer (tools authors)
    * Application operator (Service and infrastructure providers)
    * Direct end-user (Users who run tools themselves)
    * Library & package authors (Users who write libraries and packages to be included on other applications)
    * Node.js core maintainers (Developers working directly on Node.js, individuals participating in Working Groups)
1. What operating system is your **local** development environment? (drop-down list)
    * Android
    * Linux with Docker
    * Linux/Unix
    * macOS
    * macOS with Docker
    * Serverless
    * Windows
    * Windows with Docker
    * Windows with WSL
    * Other
1. What is your Operating System in which you are running Node.js in **production**? (drop-down list)
    * Android
    * Linux with Docker
    * Linux/Unix
    * macOS
    * macOS with Docker
    * Serverless
    * Windows
    * Windows with Docker
    * Windows with WSL
    
    * Don't know
    * Other
1. What is your architecture in which you are running Node.js in **production**? (drop-down list)
    * Arm
    * x64
    * Don't know
    * Other
1. What is your primary use case for Node.js? (drop-down list)
    * Application server
    * Endpoint server
1. Do you write and test your code to run on other server side runtimes in addition to Node.js? (drop-down list)
    * Yes
    * No
1. Which frameworks/ecosystems do you use?
    - [ ] Adonis (various)
    - [ ] Blitz.js (React)
    - [ ] Meteor (various)
    - [ ] Next.js (React)
    - [ ] Nuxt (Vue)
    - [ ] Remix (React)
    - [ ] SolidStart (SolidJS)
    - [ ] SvelteKit (Svelte)
    - [ ] TanStack Start (React)
    - [ ] Something else: (free response)

## Node.js maintenance

> Node.js is maintained by volunteers, mostly in their free time.

1. How does your organization invest in Node.js ? (select all that apply)
    - [ ] Sponsors time to work on open-source
    - [ ] Donates (financially) to Node.js or OpenJS (the parent charity of Node.js)
