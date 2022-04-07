## Links

* recording: <https://youtu.be/MqOdY58EW7M>
* issue: <https://github.com/nodejs/next-10/issues/124>

## Attendees

* Michael Dawson (@mhdawson)
* Gireesh Punathil (@gireeshpunathil)
* Ulises Gascon (@ulisesGascon)
* Luke Wagner (@lukewagner)
* Thomas GENTILHOMME (@fraxken)
* Richard Lau (@richardlau)
* Rodney Russ (@rdruss)
* Jean Burellier (@sheplu)
* Tobias Nießen (@tniessen)
* Beth Griggs (@BethGriggs)
* Chengzhong Wu (@legendecas)
* Vladimir de Turckheim (@vdeturckheim)
* Debdut Chakraborty (@debdut)
* Colin Ihrig (@cjihrig)

## Agenda

* Intros - 5 mins
* WASM - 90 mins
* Break 15 mins
* Permissions/policies/security model - 90 mins
* Break 15 mins
* Wrap up and capture next actions

## Minutes

Started off with quick intros for who we are/interested.

### WASM

* Built in WASM within Node.js
  * What are the capabilities, how can the process be as smooth as possible.
* Discussion 
  * Luke - WASM gives tools, to build up your own thread support
    * know that there should be work in spec to make spawning threads easier, nobody
      has volunteered yet
  * Tobias
    * webassembly per thread, asyncify, challenges, stack unwinding/switching in a more usable
    * synchronous calls versus async calls, instead of asyncify, work to to stack switching, would be helpful if we said we really wanted this.
  * stack switch especially useful in Node.js were we need async
  * more apis to convert between WASM memory and Node.js memory
    * Luke is streaming in/out of Web assembly memory a use case for this
    * Tobias, have not seen those use cases, but avoiding copies would be valuable
    * BYOB - bring your own buffer, not great for Web Assembly.  But taking
      Shared view is a use case where it could make sense. - whatwg/streams/757
    * Today if you change size of memory in WASM, it’s detached and all pointers
      become invalid. This would need to be addressed on the WASM front.
    * Challenge is APIs that can write into WASM memory.  
      * Luke making memory shared, but don’t really share it, it uses virtual memory
        so views on shared memory are stable
    * challenge between memory allocation in JavaScript and in WASM as 2 different
      memory spaces, some proposals around garbage collectors
    * Luke in v8 finalizers can be created for views, and there are some tricky edges,
      but is an approach. FinalizationRegistry
    * Important that Node.js support WASM
      * WASI - another important front (should try to actively be involved in this to make sure we can support it)
      * Luke - cluster of standards interface types and module linking, fused into component model which layers
        on top of WASM to try to give more complex types.
      * Idea is that platforms can provide implementation, but initial implementations would be polyfills with glue code.
        Actively being prototyped in Wasmtime.  
      * Michael, does this help on the addon front?
      * Luke, yes, would also the module to be imported, allows you to import function from JavaScript as well.
      * Tobias, different use cases
        * Want to re-use existing code
        * Performance
        * Hardware features
      * Today, WASM has mostly been the performance use case to avoid call across the boundary
      * Advantage of compiling WASM once, versus having to compile on local machine
    * Node.js could look at how we support WASM compilation step easier
      * It would make sense for us to have some good documentation for that
    * Luke what is the state of the art for getting WASM
      * In Node.js you can read in a separate file, online resource and then compile/run. Does depend on WASI
      * Base 64 encoding is mostly in browsers
    * streaming web assembly APIs
    * ESM, how imports get satisfied is tricky, need to inject wrapper with glue around module, there is variation on
      original ESM integration, what you import is uninstantiated code, then you get to instantiate within your own module.
      * use fetch to get/compile but then allow instantiation
      * new proposal - <https://github.com/tc39/proposal-import-reflection>, can opt into new behavior
    * Key APIs
      * WASI
      * Component API Model: <https://github.com/WebAssembly/component-model/>
      * Streaming APIs (mostly provided by V8, need to enable embedder)

#### Summary of what we agreed
* WASM strategy
  * Base WASM functionality through V8
  * Key API support - Enable key complimenting APIs
    * WASI
    * Component API Model: <https://github.com/WebAssembly/component-model/>
    * Streaming APIs (mostly provided by V8, need to enable embedder)
  * Make it as easy as possible to load WASM
    * ES modules integration - will need to implement/not design
    * May want an equivalent for require/commonJS, but not as important
    * Loading times may be an issue for environments like serverless, streaming compilation may help with that.
      Compilation time mostly depends on tiering, synchronous compilation may (Interesting but complicated and not
      key to success of Node.js at this time).
    * Getting started page for WASM - <https://nodejs.dev/learn/nodejs-with-webassembly> (existing link)
    * Tutorial/pointers on how to compile your WASM (outside of Node.js) and how to integrate into an
      npm workflow. Package.json, how do you integrate WASM build steps into that.
    * Michael issue related to bundling? Tobias not necessarily related to WASM. 
  * Making sure our own APIs are compatible with WebAssembly and can be called efficient to avoid data copies.
    * Review APIs, identify key APIs
    * Additions to allow a pre-existing buffer to be passed

* Actions/next steps
  * Document strategy - Michael will PR what we discussed
  * Encourage implementation of Streaming APIs
  * Put Component model/addon opportunities on agenda for discussion by node-addon-api team
  * Document list of documentation that would be good have and make call for volunteers to find existing
    articles to cover it or write new doc we can host.

### Permissions/policies/security model

* Ulises
  * past meeting, deploy some kind of policies, but what it might look like, etc.
    concerns about how it might affect distributions
  * Deno might be an example, file system, environment model, network access
  * Related, Anna’s pull request a while ago with proposal, blog post by James
  * docker often provides a lot of control but does not apply to use cases like
    electron
  * how do you deal with granularity etc.
  * architectural approach/strategy
  * In the mean time could provide advice how to address in environment like docker
    etc.
  * Useful resources about this (context)
    *process: initial impl of feature access control by Anna Henningsen
    * [WIP] src,lib: policy permissions by James M Snell
  * Permission flags were explained by Ryan Dahl in his 2020 talk about the Deno security model at Speakeasy JS
    * Adding a permission system to Node.js
  * Vladimir, we could not agree on the threat model (attacker, what are we trying to prevent, as most measures come along with costs/overhead)
    * Comment on article in Deno, that they needed to have all permissions enable.
  * Tobias, you can already create policies, but not a lot of tooling around it
  * Guy, one thing that is tricky, is that there are so many different approaches to it.
    Because it’s all or nothing, it is difficult to define next steps. How do we
    research where there are a lot of interesting things.  different directions even if they are not comprehensive.
    Many different use cases, and strategy for each.

* Security Model
  * What would we use it for
    * Filter for vulnerability reports
    * Penetration testing?
  * Vladimir, capture those that we believe are in scope, and those out of scope based on past history.

* Guy interesting areas we should explore
  * Stronger sandboxes, shadow realm
  * WASI virtualization
  * Policies do control dependency locking
  * Does each dependency gets different versions of fs
  * Depend on frozen intrinsics
  * Deprecated process.dlopen

* Vladimir - Node.js certification curriculum?  2-3 questions?

* Can we make it so native modules need to be declared as CLI flags when starting?
  * `--no-addons` exists today already exists but does not let specific addons to be selected

* Vladimir - Isolating modules
  * Can we prevent npm module from accessing other system primitives
  * Only way of doing it are performance killers + lots of complexity

#### Summary of what we agreed
* Strategy
  * Document security model, accept/handle security vulnerabilities in line with Model
    * is not a sandbox, we assume user trusts the code that is running
      * includes JS and native code
    * must be able to manifested with just Node.js APIs (ie just be because you can build something
      vulnerable with the APIs does not mean there is a vulnerability in Node.js itself)
  * Look to help code on top avoid making mistakes, but not doing so is not considered a
    vulnerability in Node.
  * Not currently planning to provide supported sandbox functionality, but want to allow
    Experimentation
    * Today, any additional functionality would be opt-in, and default behavior must be low overhead.
    * Try to limit change in core to just what is needed to enable experimentation
    * Experimental low overhead additions are good
  * Documenting threat models and current state of the art
        Server
        Desktop application
        Cli
        Single executable application
        CI/CD pipeline components
  * Add security component in Node.js certification covering Node.js security model
  * Observability, providing diagnostic info is important to support live monitoring/security
    post-mortem, but should be covered under Diagnostics strategy.  

* Actions/Priorities
  * Document strategy - Michael volunteered to PR this in.
  * Document security model
  * Documenting threat models and current state of art
