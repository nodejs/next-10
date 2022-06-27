## Links

* recording:
* issue: <https://github.com/nodejs/next-10/issues/112>

## Attendees

* Michael Dawson (@mhdawson)
* Geoffrey Booth
* Glenn Hinks
* Jacob Smith (@JakobJingleheimer)
* Richard Krasso
* Mark McHenry
* Trivikram Kamat (@trivikr)
* Jean Burellier (@sheplu)
* Eemeli Aro (@eemeli)
* Lucas Holmquist
* Waleed Asraf (@waleedashraf)
* Stephen Belanger
* James Snell
* Trevor Norris
* Wes
* Nick
* Beth Griggs
* Ethan
* Luke Holmquist
* Tierney
* Ruben Bridgewater
  * + many more, about 40 I think total

## Agenda

* 13:00 Central/18:00 GMT - ESM (80 mins)
* 14:20 Central/19:20 GMT - Break (10 mins)
* 14:30 Central/19:30 GMT - Observability (80 mins)
* 15:50 Central/20:50 GMT - Wrap up (10 mins)

For each topic answer these questions:

* Is the current state good enough to ensure future success or are there
  things the project should be doing to improve them?
* If the answer to the first question is that significant improvements are needed,
  document specific things that we work on/prioritize

## Minutes

### ESM

* What are key remaining key issues
  * Observability and testing are the 2 main issues remaining

* Discussion that ESM does not support everything you can do in CommonJS
  * Trevor - you can’t do all of the same things you can do in CommonJS in ES, some apps will never be able to move over.
  * Can use async
  * Eemii, there is a use case for a synchronous dynamic import, but that is a spec issue
  * James, host specific behavior. Spec allows instantiation steps to be in parallel
  * Could not commit to keeping the order?
  * Geoffrey defines, create tree, then gets everything
  * Geoffrey: need to define dynamic imports for the things you need order, and then import rest of the stuff.
  * James, developers can stick to CommonJS, or will tool vendors have to have 2 implementations
  * Bradley use loader hooks to be able to redirect and intercept some things
  * Bradley have also ported a lot to diagnostic channel
  * Stephen diagnostic channel is where we want things to go, as more goes to diagnostic channel order will matter less.
  * Stephen good to add things to Node.js versus the hacking into Node.js

* Discussion around import maps
  * Geoffrey
    * Import maps, possible to do with loaders
    * Have one that has been working but need to publish
  * Chrome + Deno support import maps, good to do without loaders
  * Native import maps support would be good, but lower priority than loaders and vm support for ESM

* Discussion on challenges around adopting ESM
  * Glen Difficult to move to ESM  
  * Blocker -> Typescript
    * Lack of support for ESM (Glenn)
    * Compiled down to ESM
    * TypeScript 4.7 released on May 24th, 2022 added support to compile to ESM
  * Brian clarified that it was possible before but not complete
  * Jacob: TS rolled their own for a lot of issues that the ecosystem has now solved, and they're playing catch-up (or ignoring things where they prefer their own)
  * Some modules have just converted to ESM, if you want to use one of those pushes you towards full ESM support.
  * FAQ on How to do x, y, or find/point to links for best blogs on that topic would be helpful

* Discussion around import.meta
  * Having to inject things via the command line arguments, cannot provide a reflective API.  Import.meta,
    host defined container of anything. If every host has a different implementation it will be an issue.
  * One example of meta.resolve.  Node.js returns a promise, in WHATWG going to return a string with a different implementation.
  * Constant risk of conflicting with what others use for import.meta. In many cases only option to inject things early enough.

* Discussion around linking step in ESM
  * Linking step in ESM, only way to inject early enough, is command line arguments. Geoffrey in terms of loaders,
    have talked about way to use loaders with –loaders, possibly something like package.json.  

* Discussion around testing
  * Unit tests, problem with ecosystem in terms of being able to do testing, no solutions that work as seamlessly as with CommonJS.
  * Geoffrey, the one I hear the most about is JEST.  Yes you can do mocks but only at loading, not at runtime. Much tricker using loaders.
  * Geoffrey, another core module vm, has experimental support for ES modules, but is only partial.
    It provides a sandboxed env, which is used by things like JEST, much more complicated to support for ESM and is not complete yet.
  * ok use of vm

* Discussion around lazy loading
  * Eemili, another problem is how to lazy load stuff (can do with dynamic imports but not synchronous code).
  * Jacob → is more lack of knowledge, you need to know that you have to use dynamic imports (it often doesn't require changes
    to implementation, just the test or test-setup itself, and isn't difficult, just very specific).

* Discussion on seeing what was loaded
  * Trevor standard way of seeing what was loaded?
  * Would need use loader to record on each load
  * Node.js internals has that
  * Geoffrey, the problem is that "import" is at V8 level.  Node.js could provide.  
  * Because you can’t tell V8 to unload/replace a module. Work around have been to modify url for module
   (for example with timestamp). But effective memory leak since never gets unloaded.
  * James, import.meta we can add stuff there but question is if we should/is if safe, performance
  * Unloading of modules, not needed in browsers, might be possible to PR into V8 if not too hard to maintain they might accept it.

* Misc
  * Experimental node specifier flag, planning to retire once you can via loaders
  * Will likely be experimental for a long time Import from an https url, shipped experimental support for that.  Unliked to be turned on by default.

* Geoffrey - Who is using ESM in a real production app where ESM is the entry point
  * Only James/Geoffrey
  * Datadog only has 2 out of 10ths of thousands use it, import in the middle satisfied those 2.
  * Anybody using instrumentation with it?
  * Vercel supports ESM but converts to CJS
  * Those who write ESM are larger than CJS.
  * LJHarb: no added value to run ESM in production versus CJS over authoring in ESM which is already possible/being done, even when deployment is then CJS.
  * Cloudflare is switching over to ESM for entrypoint as another datapoint
  * Matteo, one use case that was good for ESM, lambda with top level await, with reserved capacity, can move pre-loading
    in application before resources are reserved. Significantly improved cold start.

#### Summary of what we agreed

* Priorities for Node.js ESM implementation
  * Loaders (monkey patching replacement)
  * Diagnostic Channel (avoid needs to monkey patch in the first place)
  * Full ESM support in vm module (in support of testing -ex JEST)
  * Common problem FAQ/Guide - FAQ on common things people need to do/figure out when transitioning to ESM
  * Native import maps support would be good after that

* Actions/next steps
  * Continue work on loaders.
    * Jacob is progressing and moving forward, will get completed but could be completed a
      lot sooner if there was more help
    * Should we make this a strategic initiative to increase visibility/support at TSC level?
    * Goal is to get loaders to non-experimental this year
  * Continue to work on Diagnostic Channel
    * Stephen continues to work on this, but could use help adding points were we inject data
    * Create doc that lists where we think data should be sent to diagnostic channel so that others
      can help add generation of data at those points.
    * Trevor is going to PR in additional to Diagnostic Channel for a number of places NodeSource is already
      capturing data.
  * Create common problems/FAQ guide
  * Try to encourage/get work started on support for ESM in the vm module.

### Observability

* Stephen - some needs from an APM perspective
  * Need better way to be able to run code before application starts
    * -r /loaders
    * Geoffrey, –import command line as well
    * Ordering with loaders is an issue (loaders already work with both ESM and CommonJS)
    * Issues with serverless, need co-operation with serverless vendors
    * Node clinic, need to load before event loop starts, if start later then miss some objects
    * In serverless challenge getting loaded early enough.  In  AWS can monkey patch later on, but works
    * Need standardized way to have initial instrumentation loaded
      * James, do we need an entry point hook
    * –required is half way there. Geoffrey would it be possible to try –import to see if there
      are shortcomings (James will be the case if there is anything async)
    * Next, mocha, have their own binary. Use Node.js but hard to have all the existing niceties available
      on the Node.js command line.
    * Startup lifecycle for cases where third party starts things up. Environment variables can often be set. But -r for example the
      problem is waiting for async stuff to finish before the actual program starts to run.

* For ESM need to replace monkey patching, this needs non-experimental loaders

* Stephen - Diagnostics Channel
  * Hook into query libraries
  * Rendering libraries
  * Get to the point where you don’t need to monkey patch node core modules
    * DataDog don’t patch http, fastify

* Discussion on Async Hooks and replacing common use cases with an API that can be stable
  * Michael, Stephen has issue to capture additional common use cases
    * similar to AsyncLocalStorage want to provide stable APIs for common use cases
  * Node clinic, uses to track the lifecycle, to track async context flow
  * Long stack traces
  * Trevor/James - need to document that there are one-off specific use cases
    for Async Hooks so we need to keep them.

* Michael - Otel instrumentation currently uses monkey patching, should move towards loaders.

* Diagnostic channel
  * Some earlier discussion in ESM part, see above.
  * Michael, if we documented List of places we need to be instrumented we might get more help from
    across community.
  * Trevor mentions that key piece of info is when module is required.
  * Need module owners to leverage Diagnostic channel as well. We need  better doc/advocacy to module
    owners on what they should to support observability, prime projects for PRs from APMs etc.
    Communicating best practices.  There was support for Node debug, maybe we can repeat that.

* Trace events
  * James there is something better, have been attempts to replace with perfetto.
    Key that we make the switch since what we have is not stable enough

* Long stack trace support
  * Asking V8 for long stack trace support that is not connected to async await (for libuv continuations).
    Stephen has been asking for a clearly defined task object and track their stuff and our stuff,
    and passed back on async resume.

#### Summary of what we agreed

* Priorities for Observability
  * Diagnostic Channel (common with ESM)
  * Better advocacy to module owners, primining them for PRs from APMs etc and communicating best pratices
  * Better defined Node.js startup lifecycle so that Observability tools can ensure they get loaded
    early enough (common priority with another collab subbmit discussion on Typescript)
  * Replacing trace events implementation with Perfetto

* Actions/next steps
  * Continue to work on Diagnostic Channel (common with ESM)
    * Stephen continues to work on this, but could use help adding points were we inject data
    * Create doc that lists where we think data should be sent to diagnostic channel so that others
      can help add generation of data at those points.
    * Trevor is going to PR in additional to Diagnostic Channel for a number of places NodeSource is already
      capturing data.
  * Continue work on loaders (common with ESM)
    * Jacob is progressing and moving forward, will get completed but could be completed a
      lot sooner if there was more help
    * Should we make this a strategic initiative to increase visibility/support at TSC level?
    * Goal is to get loaders to non-experimental this year
  * Initiate work on enhanded startup lifecycle than can be used to ensure Observability tools are loaded
    first. James volunteered to open issue to kick off discussion.
  * Start documentation/advocacy initiative to modules owners, Michael to open issue in Diagnostics WG around
    this.
  * Look for volunteers to bring perfetto in to replace existing trace events implementation.
