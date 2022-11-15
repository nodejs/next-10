## Technology trends

|  2021         | 2022          | Change    |
|---            |---            |---        |
| TypeScript / Types                                        | ESM support                                                           | new  |
| Serverless                                                | Types in JavaScript (TaC or TS) / Types / Server-Side TypeScript      | -1  |
| Web Assembly                                              | Serverless / Seemless hosting of Node.js server. Support latest version serverless hosting by major cloud providers / Node.js as a cloud function runtime / Cloud deployment                                | -1  |
| Transaction tracing (ex. Open Telemetry) / Tracing        | Small footprint JavaScript runtimes                                   | new  |
| Single Binary                                             | Observability (Otel, prometheus, etc.)                                | -1  |
| CI/CD Automation                                          | Developers-first DX                                                   | new  |
| Permissions / Policies                                    | WinterCG                                                              | +9  (ecosystem ?)  |
| GraphQL / gRPC                                            | http 3                                                                | new  |
| Prometheus style metrics                                  | WASM                                                                  | -6  |
| Secure Software bill of material                          | Supply chain security                                                 | =  |
| Pre-compilation                                           | eBPF                                                                  | new  |
| Cryptocurrency                                            | Multi-pages Apps (MPAs) / Full-stack JavaScript                       | new  |
| IoT                                                       | Edge / Can we lift something from workerd? Are there any approches or features?  | new  |
| Zero knowledge                                            | GraphQL / gRPC                                                        | -5  |
| Object capability (OCAP)                                  | Kubernetes / Containerization                                         | new  |
| Ecosystem Comparability & Maintenance                     |                                                                       |   |

>  Types / TS need to be a core subject (linked to the new tc39 type proposal - also PR and discussion about linking TS)

> Serverless still a key priority (WinterCG group ?)

> Security still on the list, how to improve what should we change ? (ecosystem wide maybe)

> Some stuff are in progress: `binary` and `diagnostic (tracing, prometheus metrics?)`

## Node.js features

|  2021                                                                                 | 2022          | Change    |
|---                                                                                    |---            |---        |
| Modern HTTP request tooling (undici)                                                  | Docs: production ready recommendations / Rustdoc but make it Node.js / Documentation (better documentation for new people) / Docs best practice for module authors / Docs: official tutorials | +1  |
| Documentation                                                                         | Stable fetch()  | new  |
| ESM                                                                                   | Undici / undici in core  | -2  |
| Up to date ES version JavaScript support                                              | ESM import mocking  | -1  |
| Diagnostic tools (log, debugging etc.)                                                | Hot reload / dev server  | new  |
| Quic                                                                                  | More complet ESM/CJS interop  | -2  |
| Worker Thread support                                                                 | More assertion for test runners /  | new  |
| fs hooks                                                                              | python -m SimpleHTTPServer <PORT> equivalent  | new  |
| Argument Parser                                                                       | Better support embedding Node.js into other projects (related to build systems support)  | new  |
| Native bundling support (for e.g., to allow for TypeScript files as entry points)     | Improving performance of Web APIm WHATWG streams specifically  | new  |
| FIPs support                                                                          | Expanded use of diagnostic channel  | -6  |
| N-API                                                                                 | WASM / WASI status  | new  |
| Better installers / binary management                                                 | TypeScript integration / TypeScript support  | new  |
| AOT (to v8 snapshot maybe?)                                                           | llhttp and its dependency llparse is mostly a blackbox  | new  |
| Current OpenSSL support                                                               | Disk backed blob object  | new  |
| Iteration on policies and/or exposing sandoboxing primitives to scripts               | Module quality assessment tool: (eg. check if you have dual exports)  | new  |
| Alternative SSL support                                                               | FetchEvent and familly (CloudFlare workers-like server)  | new  |
|                                                                                       | logger    |   new        |
|                                                                                   | build in bundler and transpiler   | new         |

> Documentation is a key point to adress (next-10 initiative on the way)

> ESM seems crucial also (function, doc, recommandation, interop...)

> Diagnostic seems to be a key concept to improve

> Some functionnalityes landed: `Fetch` & `undici` & `argument parser` & `openssl`

## Other

|  2021                                     | 2022                                                              | Change    |
|---                                        |---                                                                |---        |
| Vulnerability management and reporting    | Improving CI reliability                                          |  new         |
| Compatibilities with other environments   | CITGM (smoke test suite) maintenance                              |  new         |
|                                           | Fuzzing                                                           |  new         |
|                                           | Competing with Bun and Deno on performances / keep up with them   |  new         |
|                                           | Vulnerability management                                          |  -4         |

> Vulnerability and security are key

> global maintenance (on multiples topics)