## Technology trends

|  2022         | 2023          | Change    |
|---            |---            |---        |
| ESM support  | Observability / Observability / Diagnostics and Observability  | +4  |
| Types in JavaScript (TaC or TS) / Types / Server-Side TypeScript | Performance improvements  | new  |
| Serverless / Seemless hosting of Node.js server. Support latest version serverless hosting by major cloud providers / Node.js as a cloud function runtime / Cloud deployment | Rust (Easier NAPI / better perf / improve bridge part) | new  |
| Small footprint JavaScript runtimes | Web assembly/WASM  | +5  |
| Observability (Otel, prometheus, etc.) | Package policies  | new  |
| Developers-first DX | Supply chain security with respect to dependecies  | +4  |
| WinterCG | Rust (and potentially other similar languages) as first-class citizen in core | new |
| http 3 | WinterCG   | -1  |
| WASM | Serverless | -6  |
| Supply chain security  | JSDoc for generating typescript types  | -8 |
| eBPF | larger core stdlib  | new  |
| Multi-pages Apps (MPAs) / Full-stack JavaScript  | HTTP APIs  | -5 (WinterCG?)  |
|  Edge / Can we lift something from workerd? Are there any approches or features? | Server Rendered Web Apps  | new  |
| GraphQL / gRPC |   |   |
| Kubernetes / Containerization |   |   |
|  |   |   |

>  Bridge with other languages seems important, both in core and around Node-API (Rust as main citizen)

> Observability is one of the big topic - linked to diagnostic channel?

> New technologies around HTTP and Serverless


## Node.js features

|  2022  | 2023  | Change    |
|---   |---    |---        |
| Docs: production ready recommendations / Rustdoc but make it Node.js / Documentation (better documentation for new people) / Docs best practice for module authors / Docs: official tutorials | First-class Support for TypeScript | new  |
| Stable fetch() | New HTTP1/.1 server similar to the undici initiative / Unified HTTP architecture /HTTP/3  | +1  |
| Undici / undici in core | faster startup time  | new  |
| ESM import mocking | Better perf AsyncLocalStorage  | new  |
| Hot reload / dev server  | opt-in/opt-out from builtin modules  | new  |
| More complet ESM/CJS interop | node, while aligning itself with browsers, should not shackle itself to browser choices  | new  |
| More assertion for test runners / | Undici in Node when?  | -4  |
| python -m SimpleHTTPServer <PORT> equivalent | WebSocket  | new  |
| Better support embedding Node.js into other projects (related to build systems support) | ServiceWorker FetchEvent standard API  | +7  |
| Improving performance of Web APIm WHATWG streams specifically | process replacement  | new  |
| Expanded use of diagnostic channel  | packages from cdn (like Deno)  |  new |
| WASM / WASI status | Vendoring in libraries  | new  |
| llhttp and its dependency llparse is mostly a blackbox | Import Maps!! / Import maps support  | new  |
| Disk backed blob object |   |   |
| Module quality assessment tool: (eg. check if you have dual exports)  |   |   |
| FetchEvent and familly (CloudFlare workers-like server) |   |   |
| logger |     |           |
| build in bundler and transpiler |    |          |

> TypeScript and types are important

> Fetch and HTTP / Websocket is important

> Functionnalities and libraries related to core, browser spec


## Other

|  2022 | 2023  | Change    |
|---  |--- |--- |
| Improving CI reliability  | A next generation package registry and accompanying package manager  | new |
| CITGM (smoke test suite) maintenance  | Performance  | new  |
| Fuzzing | ensuring a smooth migration story (for any new thing), as a higher priority than the end goal itself | new   |
| Competing with Bun and Deno on performances / keep up with them |    |    |
| Vulnerability management |   |          |

> New package manager

> Performance