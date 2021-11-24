# Next-10 Mini-Summit 18 Nov 2021


- **Mini-summit issue:** https://github.com/nodejs/next-10/issues/99
- **Recording:** http://www.youtube.com/watch?v=TY5uirDq1SI
- **Minutes doc:** https://hackmd.io/mW7rTTYvREOwGRpOYkXc4w


**Attendees**
* Michael Dawson (@mhdawson)
* Tierney Cyren (@bnb)
* Michael Zasso (@targos)
* Orta Therox (@orta)
* Richard Lau (@richardlau)
* Igor (@igorklopov)
* Max Schmitt (@maxibanki)
* Gireesh Punathil (@gireeshpunathil)
* Joyee Cheung (@joyeecheung)
* Joe Sepi (@joesepi)
* Erick Wendel
* Bethany Nicolle Griggs (@BethGriggs)
* Simon Schick (@SimonSchick)
* Ruben Bridgewater (@BridgeAR)
* Steven (@styfle)
* Parris Lucas (@groovecs)
* Jean Burellier (@sheplu)
* Joyee Cheung (@igalia)

**Agenda**
* Quick introductions
* Suitable types for end-users - 90 mins
* Break 15 mins
* Single Executable Applications - 90 mins
* Break 15 mins
* Wrap up and capture next actions


## Suitable types for end-users
* Orta (@orta)
  * From [TypeScript](https://github.com/microsoft/TypeScript) team, advantages to being in 
    [Definitely Typed](https://github.com/DefinitelyTyped)
    * Easier to make minor fixes
    * Changes to node types tested across the vast ecosystems for breaks
    * We can support multiple versions of TS and node in the same place
  * Automation could help improve things
  * Simon has something that extracts docs from Node.js
* Simon (@SimonSchick)
  * A tool that tries to match types with documentation
  * Fairly incomplete
  * Pulls in docs tags, also help identify where types 
    are missing 
* Orta (@orta)
  * Web, all have specs generated from that
  * Reach into Mozilla repos, using [JSON](https://www.json.org/json-en.html) data to extract 
    doc, and append those to types
  * Maybe there is an excellent way to get a JSON dump of 
    functions in Node.js to provide richer types inside 
    the type system
* Tierney (@bnb), the discussion is getting closer to my pref, 
  which is to mirror what electron does. [Electron](https://github.com/electron) structure is
  sort of patterned on Node.js, they have [docparser](https://github.com/Docparser), which
  creates JSON rep, and they can generate types off that.
  Node.js dumps into a text property were as the
  Electron one is more structured.
* Tierney (@bnb) spent some time getting docparser working
  with Node.js, which does not appear due to legacy. Json
  representation of APIs would be good.
* Orta (@orta), one of the parts of the tension is that
  the more profound the integration, the more node maintainers
  need to know about typescript. Advanced TS syntax
  makes it hard, and we want to avoid maintainers having
  to understand how to make it all work in those more
  advanced cases. This work best left for contributors in DT.
* Today's flow
  * API is added/documented in Node.js codebase
  * Node.js publish JSON content on doc site for example
    * [https://nodejs.org/.../console.json](https://nodejs.org/dist/latest-v17.x/docs/api/console.json)
  * Simon runs his tool manually. It tries to match
    documentation in JSON files published on the Node.js 
    the site to the tree that already exists in DT. 
    It checks for missing definitions, mostly output warnings.
    * The tool will actively pull docs for with a match and 
    update the docs.
    * New methods require additional new APIs.
  * Pull Requests(PRs) reviewed and landed.
* Ideal flow
  * API is added/documented in machine-consumable
    way to Node.js codebase.
  * An automated script in DT runs, generates new PR.
  * PRs reviewed and landed
* Challenges with consuming existing data
  * Current JSON data is reasonably inaccurate, words
    are accurate, but struct is not. This function tries
    to match things up - [github.com/SimonSchick/DefinitelyTyped/.../node-doc-processing.ts#L112](https://github.com/SimonSchick/DefinitelyTyped/blob/master/types/node/scripts/generate-docs/node-doc-processing.ts#L112)
  * Often generated JSON docs do not represent actual
    documentation.
  * How do we model complex generics overload?
    * e.g., return types differ depending on argument values 
    currently not modeled at  doc assumes these functions 
    return type unions.
  * Many methods in the child process module take the same types,
    but docs redefine. So we are just documenting function arguments.
* Example of converting Node.js doc to work with
  electron parser
  * [github.com/bnb/node-docs-parser](https://github.com/bnb/node-docs-parser)
  * Info in comments and YAML would need need conversation
    to raw markdown (for example introduced in) style 
    guide - [Electron Documentation Style Guide](https://github.com/electron/electron/blob/main/docs/styleguide.md)
* Possible MVP
  * Discuss if we can use the electron style guide
  * Explore DocsParser, perform multiple exports fix 
    allow generations for "enough stuff."
  * Would need to move metadata into markdown to 
    be visible (type systems require this). 
  * It would require a change to the HTML generator.
  * Actions, validation jobs for docs that
    have generated
  
* Questions
  * Would it change how the existing markdown looks?
  * Do we have any commitments on the structure of that?
  * Is stuff used in comments/YAML used in types?
  * What issues around backporting to earlier versions exist?

## Single Executable Applications

* Current solutions
  * [pkg](https://github.com/vercel/pkg) ![GitHub Repo stars](https://img.shields.io/github/stars/vercel/pkg?style=plastic)
  * [nexe](https://github.com/nexe/nexe) ![GitHub Repo stars](https://img.shields.io/github/stars/nexe/nexe?style=plastic)
  * [NectarJS](https://github.com/NectarJS/nectarjs) ![GitHub Repo stars](https://img.shields.io/github/stars/nectarjs/nectarjs?style=plastic)
  * [node-packer](https://github.com/pmq20/node-packer) ![GitHub Repo stars](https://img.shields.io/github/stars/pmq20/node-packer?style=plastic)
  * [BoxedNode](https://github.com/mongodb-js/boxednode) ![GitHub Repo stars](https://img.shields.io/github/stars/mongodb-js/boxednode?style=plastic)
* Steven (@styfle)
  * 3 different ways of bundling
    * [pkg](https://github.com/vercel/pkg), bundles Node.js executable into a single 
      binary, similar to what Deno does
    * [ncc](https://github.com/vercel/ncc), compiles all JavaScript into single file, 
      distribute single JS filem with exectable 
      directive at the top
    * [nft](https://github.com/vercel/nft), given single input file, find all dependent 
      files which gives the list
  * Benefit is that those who are unfamiliar with 
    Node.js ecosystem can easily run binary. cli is
    a good example
  * Easy to download, easy to run
* Michael (@mhdawson) does size of binary matter?
* Tierney (@bnb) all three might be interesting but for
  what we are discussing here pkg most related
* Steven (@styfle) - [Awesome Desktop JS > Packaging](https://github.com/styfle/awesome-desktop-js#packaging), list of implementations.
* Tierny (@bnb) quite a few shows interest.
* Today common challenges include:
  * Igor
    *  compile time
      * traverse require calls, would be good if nft and 
        pkg combined efforts. 
    *  runtime
      * how do we store the assets needed to run 
      * pkg has its own binary format that indexes them
      * pkg attaches to the Node.js executable
  * Michael (@mhdawson) both pkg and BoxedNode require that you 
    compile Node.js.
    * For pkg, hidden source code requires compilation
    * pkg required patches - [github.com/.../99#issuecomment-970674910](https://github.com/nodejs/next-10/issues/99#issuecomment-970674910)
  * Igor, self-extracting archive
  * Each platform has its own way of
* Issues around adding signatures (macOS) 
* Obfuscation, how important is that?
  * Is one of the reasons people would want single 
    binary verus just using script. 
* Signature issues
  * Executables have their own format on each platform
  * They have sections, one more section added to end
    with signature. 
  * Cannot just blindly buffer contact, need to make
    their payload a proper section of the binary
  * Without signature OS does not care if you have
    added to the binary, signature tools may strip
    out a section if it is a simple concat.
  * Packer would need to
    * Strip signature from Node.js
    * Add the new section in manner that complies with 
      OS exe structure
    * Use signing tools to add new signature
  * Flow that might makes sense is
    * On startup Node.js checks for section in
      exe
    * Load options from known offset in section
    * Load JS file from known offset in section

   * Michael Z, be able to run single file in
     binary format. Then second feature is to 
     bundle single file.
     * Joyee can you not already do that with
       bundlers like Webpack
     * Michael Z, Ideal if Node.js was its own
       bundler.
   * Joyee makes sense for Node.js to be able to patch 
     itself, just the simple case of patching itself
     and staring binary js file.
   * Richard, Issue/PR already to provide framework to
     allow a virutal file system to be provide
   * Joyee, bundlers can generate single file
   * Michael Z, there are limitations, cannot support
     native modules, or include additional files
   * Michael, need to define more than just block of
     JS
   * Joyee, don't want to contrain what we put in
     section
   * Structure needs to have a least 3 sections
     * options (ex allow --js-flags)  
     * arguments for Node.js (-e allows js to be specified)
     * data section to be passed to js file
   * Command line args, additional arg to add options to
     Node.js arguments (--js-flags). Force to be the first
     argument.
   * Still would not support native addons
     * pkg ended up placing native modules as dlls shipped
       along with binary
     * boxednode includes native addons, we should ask Anna
       how you do that.
     * Richard believes boxednode handles native addons by
       including them in like core modules
       
* Approaches
  * Compile with node, into exe (boxnode)
  * Bundled onto exising Node.js exe (pkg approach)

* Richard used to be `third party main`, I think we took that
  out, how do you start something else. Good prior art to consider.
* Joyee we could add into list of conditions checked in startup
  before others. `third_party_main.js` was implemented because it was easy (just checking for the existence of it). The bundling solution would be more sophisticated.
* Michael Z, In which mode (esm or cjs) should we run the next section
  * Michael D, probaly need an option for that  

## Next Steps and actions

### Single Executable Applications
* Ask Anna if there are things still needed in Node.js to support
  "Compile with node" approach
* Write up an overview of what we discussed in terms of potential
  addition to Node.js
* Share what we discussed with @jesec with respect to what we discussed
  to support bundled onto Node.js exe approach
* Reach out to V8 team to see if it's possible to rely on the compilation cache (which includes the bytcode) for compilation and not require sources (Yang had previously said it was doable, prior art: https://chromium-review.googlesource.com/c/v8/v8/+/1462961).

## Suitable types for end-users
* Document target flow for Node.js type generation
* Staring discussion on adopting Electron style guide
* Further explore Electron TypesParser to see if it can be used to generate JSON 
  for Node.js project
* Explore how we'd move metadata from comments/YAML to markdown as they
  are currenlty not rendered and it would also help exposing through TypesParser
* Rethink how doc is structured with respect to API documentation versus other 
  things. Should JavaScript API docs and other topics be more separated?
