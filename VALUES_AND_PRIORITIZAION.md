# Values and Priorities

> Document Status: Proposal, Work In Progress

## Context

Define the `Technical` values shared by the project and their relatively priority
that are applied when making tradeoffs.


## Values and priority level

This is only a subset of the overall prioties, listing only those which are at the
top of the priority list. Anything on this list is very important for the project
despite the relative priorities shown.

- Prio 1 - Developer experience
- Prio 2 - Stability
- Prio 3 - Operational qualities
- Prio 4 - Node.js maintainer experience
- Prio 5 - Technology and API Currency

## Value descriptions

### Developer Experience
We value ensuring that developers are productive and enjoy developing with Node.js. Some key elements of this include:
  - Approach-ability (both technical and community)
  - Great Documentation 
  - Bundling API/components which reduce the friction of using them, even though they could be external
  - Enabling/supporting external packages to ensure overall developer experience

### Stability
We value keeping Node.js stable and consistent across releases versus introducing breaking changes that require churn in the ecosystem. Some key elements of this include:
  - Backwards compatibility
  - Predictable and stable releases
  - A strong safety net (testing etc.) 
  - Careful consideration of what goes into LTS releases 

### Operational Qualities
We value keeping Node.js safe, performant and light weight as well as the ability to investigate and debug problems in development and production. Some key elements of this include: 
 - throughput(speed)
 - startup time
 - binary size
 - memory footprint
 - Debug tooling (debugger)
 - Diagnostic tooling (profilers, heapdumps, coredumps, etc.)

### Technology and API currency
We value providing developers with modern APIs and technologies following existing standards whenever possible.  Some key elements of this include:
  - participating in standards work and organizations
  - web API compatibility
  - supporting new technologies and standards and exposing them early in their life-cycle 

## References

[First pass at list of values](https://github.com/nodejs/next-10/issues/5)
[Original priorities brainstorm document](https://docs.google.com/document/d/1sbO_zCn9n_JH2zuGtqNAahUhA_mGFA89DdAme8nEdsw)
