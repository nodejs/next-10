# Values and Priorities

> Document Status: Proposal, Work In Progress

## Context

Prioritize the **Technical** values shared by the project and use these to guide us when making tradeoffs.


## Values and priority level

This is only a subset of the overall priorities, listing only those which are at the
top of the priority list. Anything on this list is very important for the project
despite the relative priorities shown.

- Prio 1 - Developer experience
- Prio 2 - Stability
- Prio 3 - Operational qualities
- Prio 4 - Node.js maintainer experience
- Prio 5 - Technology and API currency

## Value descriptions

### Developer Experience
We value ensuring that developers are productive and enjoy developing with Node.js. Some key elements of this include:
  - Approachability (both technical and community)
  - Great Documentation 
  - Bundling friction-reducing APIs and components, even though they could be provided externally
  - Enabling/supporting external packages to ensure overall developer experience

### Stability
To avoid introducing churn into Node.js' ecosystem, we value stability and consistency across releases and avoid breaking changes. Some key elements of this include:
  - Backwards compatibility
  - Predictable and stable releases
  - A strong safety net (testing etc.) 
  - Careful consideration of what goes into LTS releases 

### Operational Qualities
We value keeping Node.js safe, performant and lightweight as well as the ability to investigate and debug problems in development and production. Some key elements of this include:  
 - Throughput (speed)
  - Startup time
  - Binary size
  - Memory footprint
  - Debug tooling (debugger)
  - Diagnostic tooling (profilers, heapdumps, coredumps, etc.)
 - Addressing security vulnerabilities in a responsible manner

### Node.js Maintainer Experience
We value the productivity and happiness of Node.js' maintainers. Some key elements of this include:
- Approachability of the codebase
- Good internal documentation and guides
- Low-friction policies and processes
- Good CI and tooling to make maintainers productive

### Providing modern APIs and Technologies
We value providing developers with modern APIs and technologies following existing standards whenever possible. Some key elements of this include:
  - Participating in standards work and organizations
  - Web API compatibility
  - Supporting and exposing new technologies and standards through early adoption

## References

[First pass at list of values](https://github.com/nodejs/next-10/issues/5)
[Original priorities brainstorm document](https://docs.google.com/document/d/1sbO_zCn9n_JH2zuGtqNAahUhA_mGFA89DdAme8nEdsw)
