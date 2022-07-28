# Next-10 Types Mini-Summit

# Links

* Recording: <http://www.youtube.com/watch?v=HTbh6o6a-aI>
* Issue: <https://github.com/nodejs/next-10/issues/149>

# Attendees

* Michael Dawson (@mhdawson)
* Stephen Belanger(@qard)
* Richard Lau (@richardlau)
* Ethan Arrowood (@ethan-arrowood)
* Gil Tayar (@giltayar)
* Wesley Wigham (@weswigham)
* Jacob Smith (@JakobJingleheimer)
* OJ Kwon (@kwonoj)
* Andrew Bradley (@cspotcode)
* Guy Bedford (@guybedford)
* Zack Schuster (@zackschuster)
* DongYoon Kang (@kdy1)
* Steven (@styfle)
* Jake Bailey (@jakebailey)
* Geoffrey Booth (@GeoffreyBooth)
* Feng Yu (@F3n67u)
* Ruy Adorno (@ruyadorno)
* Fabian Meyer (@meyfa)
* Romulo Cintra (@romulocintra)
* Tierney Cyren (@bnb)
* Matteo Collina (@mcollina)
* Jean Burellier (@sheplu)
* Moshe Atlow (@Molow)
* Rob Palmer (@robpalme)
* and 2-3 others

# Agenda

* Intro
* Requirements/Desired UX Brainstorm
* Document agreed approach
* Implementation brainstorm (if time)
* Document Next Steps (10 mins)

# Requirements/Desired UX Brainstorm

* Jacob
  * Today you can support TS using esloader with command line loader
* Geoffrey shared steps you need to do using ts-node
* Tierney believe goal is to run node test.ts
* Michael, not bundling, but if required pieces already installed, then work, otherwise
  prompt to install pieces.
* Jacob, how?
  * keep list of all options
  * pick one?
  * some config
* Stephen - Suggestion of pushing things into NODE_OPTIONS does not work
* Wesley - built in prompt, but then suggest you install
* Geoffrey, specific design not to bundle TypeScript with Node.js
* Geoffrey, we would have informative error message, go to this link to get info on
  options etc.
* Zack - many different flavors of typescript?
* Wes, check compiler options reference, many different ways to config
* Zack, two core parts,
  * print something when test.ts is run with additional info
  * Lower config than NODE_OPTIONS in terms of what you can do today
* Andrew, comes down to adding more comprehensive customization hooks
* Jake - don’t want to get hung up on global list
* Matteo
  * Current issue with some proposals - requirement for ESM,world is bigger than that, needs to work for both ESM and CJS
  * use of NODE_OPTIONS is not ergonomic
  * loading from package.json might be a good option
* Tierney
  * Configuring through package.json is fine, but would be able to run node script.ts,
    happy to do steps required for project, but not have higher bar.
* Andrew - mention of snippet implying ESM, work through hacks ts-node sample works for CJS
  as well
* Matteo
  * Reason not recommended that can download node and then just run node script.ts. Issue
    is there are lots of different options
* Stephen could we just not do the same as ts-node if we don’t use config file
* Matteo, hook to guide people to setup config file. Deno does not support multiverse of
  TypeScript, we don’t want to do that.
* Daniel, in terms of compatibility across versions, does Types as annotations relate in terms of
  Possibly being defaults?
* Matteo, whatever happens at runtime level, does not relate, what’s being specified in TC39
  proposal  dos not overlay, Types a comments is about TypeChecking, not running
* Tierney, independent.
* Ruy, discussed supporting different versions, maybe vendoring loaders might be a solution.
* Rob, implemented in runtime in a custom runtime, on Matteo’s comment, found you can divide tsconfig into 2 categories
  * type checking - every project wants something different
  * adapting to platform - looking them down the way Deno does is beneficial as they don’t need
    to vary for a given runtime platform. Deno’s layered approach
    * core set you cannot override which are aligned with platform
    * other can be varied
  * Andrew, what do we do if user does not have config, its more just around running, editors
    highlight issues, etc.  If we lock down options, what does the editor do if there is no config
    file for example?
* Wes fundamentally all we want is ability to install something that has the ability to override
  Node.js execution start.
* Tierney, don’t want to do it for anything, ok to limit it down to a limited subset, for now TypeScript
* Jacob, don’t necessarily to need to limit subset, only if we can define a method that is agnostic
* Geoffrey, perspective of maintainers, there are lots of decisions so choosing config etc. as  
  Node.js maintainer, don’t have Node.js make decisions. Just enable people to load easily.
  This is first decision to make.
* Andrew
  * Loaders to expand to be customization hooks
  * Option in on project local basis through package.json
  * Opt in on a global basis
  * Don’t violate security expectations
* Geoffrey, loaders roadmap has a number of those on the roadmap, PR already open #43973
* Tieney, +1 being totally configurable, as long as it does not take a lot of energy to
  support that and DX is not awful, DX needs to be primary result. Could loader just not provide
  the configuration.
* Jake, busy looking at snippet, talking about putting things in package.json.  Do we not care
  about case where you don’t need a package.
* Matteo, will need a config, other files
* Geoffrey, you could run with ts-node as the binary
* Jake, wanted to understand where line is drawn.
* Tierney, concept of node.rc has been raised a number of times, for example saying that node
  will use loader X
* Geoffrey - node just has one, flag, if config in package.json, should be able to put as much
  configuration into it. - often different configurations for different environments.
* Wes, expectations that package.json is scoped, maybe you just want a rc file instead.
* Geoffrey, if file is in scope of package.json, that package.json is used to start/run config,
  No other package.json take place.
* Andrew, affects package typically, were most rc files, they are hierarchical, and combined
* Stephen, tsconfig is not necessary related, defer that to whatever is configured
* Matteo, we could consider that tsconfig is needed since without that it is sub-par experience
* Andrew, some talk of mapping from file extensions, some cases where that might not work
* Michael, more generally or for TypeScript, imports may not have a specifier at all, or
  package.json
* Jake, other tools already do the prompt in terms of asking people to install required components.
* Geoffrey if have example of doing the same prompts that would be useful. Please add to the issue.
* Rob beneficial, for it to just work, not many people wanting to reconfigure loaders, if we
  can be opinionated, important for ecosystem coherence.

# Agreement on DX 
1.start file with node (ex ndoe script.ts), look for config, not found echo message
  * generic
  * specific one for .ts
  * point to page on Node.js project with the instructions.

2.start a file with node (ex node script.ts), find config file in scope, apply Node.js
  options specified before trying to run file
  * options will configure support for execution of file of that type (for example
    through loaders or some other mechanism)
  * package.json as config file is a good choice as we already look for it.
  * Need to support handling different environments/conditions like prod,dev, etc.

Future/follow on discussion:

* Can we provide more opinionated solutions in future. Some views that this adds more value.
* When we support this how can we discourage people from shipping libraries that only contain
  TypeScript code, encourage pre-compilation. Feature may lead people into thinking just
  shipping TypeScript makes sense. Loaders can choose to not do node_modules. Can plan for
  users flow for pre-compiling.

Next Steps

1. PR in minutes for summit (Michael)
1. PR in agreement somewhere, to get broader collaborator input (Michael)
1. PR in page with instructions on Nodejs.org
1. PR in Node.js to return error with link to page
1. Open discussion issue on nodejs/node for designing config approach (Geoffrey)
1. PR to implement config design
1. Update instructions on page from 2) to define config for getting `node script.ts` to run
