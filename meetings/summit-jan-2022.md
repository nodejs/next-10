# Next-10 Mini Summit 27 Jan 2022

## Links

* zoom: <https://zoom.us/j/99950131676>
* stream: <http://www.youtube.com/watch?v=8t6HZfBZck0>
* issue: <https://github.com/nodejs/next-10/issues/108>

## Attendees

* Michael Dawson (@mhdawson)
* Robert Nagy (@ronagy)
* Christophe El-Khoury (@christopheEK)
* Michael Zasso (@targos)
* Manish Kumar (@manishprivet)
* Joe Sepi (@joesepi)
* Wes Todd (@wesleytodd)
* Jean Burellier (@sheplu)
* Beth Griggs (@BethGriggs)
* Ruy Adorno (@ruyadorno)
* Tierney
* Richard Lau (@richardlau)
* Matteo Collina (@mcollina)
* James
* Ethan
* Bradley Farias

## Agenda

* Intros
* Modern HTTP - 90 mins
* Break 15 mins
* Documentation - 90 mins
* Break 15 mins
* Wrap up and capture next actions

## Minutes

### Modern HTTP

#### Key questions to answer

1. Is the state of our http implementations good enough to ensure future success or are there things the project should be doing to improve them
2. If the answer to 1) is that significant improvements are needed, document specific things that we should do to improve the current state.

#### Discussion

* Matteo
  * HTTP 1 and HTTP 2
  * HTTP 1 API - has new http parser which is better than what we had (llhttp), challenges is that
    previous design decisions hold it back
  * HTTP 2 API a bit more modern but don’t have many people maintaining it, and has a number
    of issues, but they don’t seem to be being progressed.
  * On client side, one of the major issues is performance. Old request module to Undici, 50%
    reduction in latency. 750k weekly downloads.
* Ronag
  * quite wide HTTP1, HTTP2, HTTP3, client server side, good to break up discussion

* HTTP 1/2/3
  * We need http1 and probably do for a while
  * Do we need http2 or should we just focus on http3?
  * Wes express still does not support it, not enough interest from user, maintainers.  At netflix
    as a user don’t care, don’t think we really use it and abstracted away.  My take is
  * Matteo -> GRPC stack uses it to avoid binary addon.
  * Wes, not sure GRPC is enough to prioritize unless GRPC team gets more engaged and
    drives specific needs.
  * HTTP 2 - no major features, but bug fixing is important
  * HTTP 1 - Foundation for future application development (ex GraphQL)
  * Ronag, any plans to move GRPC over to HTTP2, James may happen but cannot count
    on that. Wes also depends on other platforms having HTTP3 support.
  * Ronag make HTTP 1 and HTTP 3 to be primary focus. ?
  * James, agree making HTTP 2 stable, HTTP 1 features stable as well, but APIs for using
  * Michael, different aspects protocols (1,2,3) and then the APIs that we use to support them
  * James, We had to change for HTTP2, but unfortunately HTTP3 changed things all over again.
    * have taken a step back socket api, looking to see if we can unify under one API.
  * Matteo, with respect to unified API we need to look at our users. Client/Server. Client typically modules authors who build on top of API. Server side target users are module users as well that build on top of API. On client, main request is put fetch in core which should be agnostic in protocol.
  * HTTP 2 in “maintenance mode” both protocol and API
  * HTTP 1 stable protocol, but innovation in API
  * HTTP 3 is the future need to plan in support
  * Client - Should Fetch be our focus?
    * Don’t want to think about protocols (1/2/3) etc.
    * They want good defaults that would perform well
    * James either want fetch or really low level API. Wes don’t want just fetch, may want something in the middle. Have looked at moving onto Got but could not due to perf issues. From Netflix would be using library interface on top of Fetch, unfortunately promise based APIs adds performance concerns. Ideally would not want to have to use low level APIs, instead the APIs provided by undici would be a better level.
  * Michael -> undici level, low level possible to be agnostic to HTTP 1/2/3. Matteo not an issue for undici.
  * James there are some complications like being able to survive switch of network
  * Wes, if interest is the problem, then driving from end-user perspective is the right way to go. Where we went wrong with HTTP is that there was nobody interested, so nobody interested in maintaining it.
  * James, disagree a bit, the reason it never really picked up due to IETF and the way browsers handled it. Browsers wanted it to be hidden so users would not have to  know about it and IETF immediately moved on to talking about HTTP3 and then benefits from HTTP2 never materialized.
  * Michael, strategic to move to APIs where you don’t need to know what protocol is being used.
  * Wes, earlier comments were about having user focus versus protocol focus
  * James fact that people have to think about APIs is what has held people back.
  * Ronag, part of HTTP2 is that lots of people are on HTTP1 and have to use both.
  * Would like to have APIs that are similar on the server/client side

  * Perfect world
    * Fetch
    * intermediate level
    * socket

  * Matteo - undici
    * Client which can do request on single socket
    * Pool, same API as client (low level API) allows you to manage multiple sockets with some dispatching
    * Agent, same API as other 2 that supports more than one target destination, adds routing to the right pool
    * Need at least 2 of those if you want to generalize across protocols
    * API surface is very nimble, developer experience is layered on top of this
  * Ronag, would make sense to have undici as low level then ship Fetch on top
  * James he would look for socket API and then toolkit to build on top off
    * would like to see innovation on top of outside of Node.js ?
  * Ronag it comes back to the to be or not to be in core
    * does not matter so much where the work is done
    * Matteo, but does matter to state what we would support
  * James developer outside of Node core lets us develop faster, and then later we can pull them
   in once more stable.
  * Wes, the outside core then pull in later is being pursued in a few places, that is great. Maybe part of 10 year plan is to go from experiment to being part of core. Should invest in that process. Not a problem to be in a vendored in state for a long time. Is important that the project provide code of conduct support, etc. from Node.js project while letting projects innovate quickly. Path for external library to getting bundle with core path/
  * Michael Z - could include undici without exposing in core to support a fetch implementation
  * Bradley, need to be careful. If exposed in node core then automatically forces stability on API.

  * Michael key goal, APIs that end users don’t need to know about HTTP protocol.
  * only introduce new APIs that can support all HTTP protocols
  * be able to surface low level details, need to ship safe defaults but allow configuration
  * Wes, providing some options that configure the high level API, is a good API/layering choice
    * Fetch + some little tweakables would hit the 99% case
  * James for QUIC/http there will always be need for QUIC specific api, other protocols build
   on top of QUIC in addition to HTTP 3
  * Tierney -> path forward for undici to consume it, if not QUIC 3 is not exposed. If external then
   no, but more flexibility if we
  * Bradley, like idea of being able to pull in without exposing for internal use. Has been used to
  slow things down. James if no immediate use then people have resisted.
  * Bradley we have talked about modules that have extra privileges.
  * Matteo, wanted to say if we want to use undici to validate apis but then we need to expose
  some way to validate.

  * Wes
    * most people will likely use node-fetch etc. as they would likely never use fetch.
    * should focus on APIs that library authors can use to build fetch compatible APIs
Bradley
    * For many apps, for requests don’t need more than fetch. For servers yes. Main reason people want fetch is that usability is much more difficult to learn to use properly. For example undici is much harder to use even though it’s a great improvement
  * Ethan agree that there is a need for fetch base on what he’s seen people struggling with
  * James agrees we need fetch in core.
  * Matteo, from marketing/position we have to have fetch in.
Bradley
    * least common denominator API works the same even if less features
    * more specific features are exposed in intermediate (variants for protocols).
      * Michael undici approach is single API, that tries to cover/support all protocols.
      * James at intermediate level can result in surprises if support is not there.

  * socket (likely to be very protocol dependent, tcp, quic)  (this might be separate from HTTP priority)

  * Matteo, on server side existing APIs have not been as big an issue

  * socket (likely to be very protocol dependent, tcp, quic)  (this might be separate from HTTP priority)
Client
  * Here is some previous discussion on the server apis: <https://github.com/nodejs/web-server-frameworks/issues/60>

#### Summary of what we agreed

  * Longer term goal
    * http protocol independent (support http1,2,3)
    * client/server APIs should be consistent and allow easy integration
    * Things like piping out from client API to server APIs should be easy
    * Client - need two levels
      * Fetch  level (and should be Fetch)
      * intermediate level (undici) - client only
    * Server - need
      * integration with client APIs is important
      * high level, here is request give me response
  * Specific goals
    * Ship Fetch implementation as experimental in 18
      * built on top of undici without exposing undici

  * Robert, we may have too many APIs in undici, may want to filter down. Goal is to have something like undici on both server/client.

### Documentation

#### Key questions to answer
1)Is the state of the current documentation good enough to ensure future success or are there things the project should be doing to improve them
2) If the answer to 1) is that significant improvements are needed, document specific things that we should do to improve the documentation.

#### Discussion

* Joe
  * Rich left a good set of things for us to discuss
  * Other aspect is integration of to website docs

* Some notes from Rich to start:
  * Search functionality (or is Google/Bing/Yandex/etc. sufficient?)
  * Automated generation from JSDoc in a consistent format (or is JSDoc not something that provides all the information we need?)
  * Separation of "here's the API reference" and "here's a breezy explanation of how to use the thing" (or maybe it's good that they appear in the same place?)
  * More consistent layout/organization and editorial voice
  * Is the one-page-per-module approach working? Or should we adopt something more like an MDN approach where it's one-page-per-function? (I like our current approach but I find it hard to imagine the alternative so I might not be comparing it against anything.)
  * Stuff is in surprising places if you don't know where to look. If I see `process.stdin.unref()` in code, I'm going to look in the `process` doc. It won't be there. If I know a thing or two about how Node.js works under the hood (which I shouldn't have to in order to use the docs), I might look in `streams` where I will also have no luck. Maybe I'd eventually find it in `net` and wonder why I had to go on the wild goose chase.
  * Let us please get rid of the knowledge base. Leave tutorials to the community. There are some things in the knowledge base that should be preserved on the site. Let's move them to the docs.
  * The team splintering of nodejs.org (website team), docs in core (core team), and nodejs.dev (website redesign team) is a problem. (And yet, is it?)

* Bradley
  * Right now feel page per module is getting unwieldy. Especially since we have pages which
  are not related to modules.
  * If you have single pages per API, it also lets you link from many places

* Richard has different scopes
  * API documentation - part of core repo
  * Knowledge base is part of website
  * As part of builds we have json doc,
  * End user formatting, stuff on top, should be it be layered differently

* Documentation Categories
  * API Documentation
  * Guides (knowledge base), getting started, debugging, profiling etc.
    * <https://nodejs.org/en/docs/guides/>
  * Learning path
    * Learn (nodejs.dev) - <https://nodejs.dev/learn>
  * Release Notes/Change logs <https://github.com/nodejs/node/tree/main/doc/changelogs>
  * Internal documentation (contributing, etc) <https://github.com/nodejs/node/tree/main/doc>
  * Roadmaps/efforts
  * Security model, processes etc.
  * Operations - Observability/tracing/monitoring
  * Deployment in production
  * How to upgrade between versions
  * How to install Node.js

* Existing docs, style guide

* How are they built/delivered
* Consistency across packages
* Separating content from presentation would allow different presentations, help make them
    Consistent. Writing in something like JSON would not be manageable.
* What is out scope
  * JavaScript standard itself

* Prioritization
  * Priority 1
    * API Documentation
    * Release Notes/Change logs <https://github.com/nodejs/node/tree/main/doc/changelogs>

  * Priority N
    * Guides (knowledge base), getting started, debugging, profiling etc.
    * <https://nodejs.org/en/docs/guides/>
  * Learning path
    * Learn (nodejs.dev) - <https://nodejs.dev/learn>
  * Release Notes/Change logs <https://github.com/nodejs/node/tree/main/doc/changelogs>
  * Internal documentation (contributing, etc) <https://github.com/nodejs/node/tree/main/doc>
  * Roadmaps/efforts
  * Security model, processes etc.
  * Operations - Observability/tracing/monitoring
  * Deployment in production
  * How to upgrade between versions
  * How to install Node.js

* Tierney have not been able to maintain guides over time
  * would be good to focus on APIs for now
  * we should keep learn
  * syndicate guides from community

#### Summary of what we agreed

* Focus on
  * API documentation
  * Release documentation
* Syndicate everything else guides, etc.
  * lower priority than improving in focus area
  * grandfather some good content

* APIs docs
  * What is in scope
    * Node.js additions on top of JavaScript
    * API specs

* Key things to work on
  * Documentation documentation strategy
    * Document metadata and what it supports
  * Consistency across packages
    * Document metadata and what it supports
  * Add examples
    * Every method has example
    * Example is in-line
  * More complete explanation for methods
  * Better links between different concepts

* Next actions
  * Document documentation strategy/get consensus
    * Document metadata and what it supports
    * Add examples
    * Every method has example
    * Example is in-line
    * Explore how we would validate that examples exist
