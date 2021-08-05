# Next-10 Summit Aug 5 2021

## Participants

* Michael Dawson (@mhdawson)
* Bradley Farias (@bmeck)
* Matteo Collina (@mcollina)
* Jean Burellier (@sheplu)
* Rick Markins (@rxmarbles)
* Joe Sepi (@joesepi)
* Tierney Cyren (@bnb)
* Parris Lucas (@GrooveCS)
* Chengzhong Wu (@legendecas)
* Beth Griggs (@BethGriggs)

## Agenda

Deck with the agenda is available in:
<https://github.com/nodejs/next-10/blob/main/meetings/summit-aug-2021/agenda.pdf>

## Recording
Recording is available in: <https://youtu.be/4u_cZoOkiyM>

## Constituencies, needs, survey

We went through quick review of work to date:

* https://github.com/nodejs/next-10/blob/main/CONSTITUENCIES.md
* https://github.com/nodejs/next-10/blob/main/CONSTITUENCY-NEEDS.md
* https://github.com/nodejs/next-10/tree/main/surveys/2021-05-03

Some discussion about the survey, would there be future ones. We discussed that
something similarly might make sense to get external validation of what we come
up with for technical priorities.

## Technical Priorities

Full notes are in:
<https://docs.google.com/document/d/1y7op1YiJchpdlk_XmUyGe5y0BLlJekldX8zUb3VoLRk/edit>

We went through the priorities identified in the easy retro we used to get input
from core collaborators:
<https://easyretro.io/publicboard/cLBIBu3wA2Um7qIziXq1zmC4gdi1/1db5ea23-fee3-4da0-bb7b-a5ea49d810e7?sort=votes>

From that and additional discussion we came up with the following priorities in
terms of what is import for the future success of Node.js:

* Key Priorities
  * Modern HTTP 
  * Suitable types for end-users
  * ESM
  * Documentation
  * Web Assembly
  * Up to date ES JavaScript Support
  * Observability
  * Permissions/policies/security model
  * Better multithreaded support
  * Single Binary

We also identified a couple which we did not feel should be on that list but that
we should keep an eye on to see if that change. These we put on a `watch list`

* Watch List
  * QUIC
  * Serverless

## Next 10 years for collaborators

Full notes are in:
<https://docs.google.com/document/d/1P0Pcg-booPxaYRYRluT6wIWyspFV2jMEafO2GfLZp28/edit>

We talked about key issue in terms of the next 10 years for collaborators/contributors
as suggested in <https://github.com/nodejs/next-10/issues/16>. The following were
used to seed the discussion:
* Contribution workflow
* Consensus seeking model
* Leadership Model

From those discussions the following priorities were agreed:
* Maintaining/growing the level of contribution
  * Ways to get funding to collaborators
  * Succession planning
  * Helping people from companies justify/make the case to have time contribute
  * Targeted mentoring
* Easier contribution workflow
  * Local build time is a major blocker
* Consensus seeking model
  * Improve how we handle objections, find “tie-breakers”
* Leadership Model 
  * Should TSC be more active in future vision/direction?


## Next steps

We reviewed the discussion and came up with this next steps:
* PR to Node core with technical priorities (Michael, Joe, Tierney, Jean)
* Plan for external validation (Survey, or what ?) - Michael to open issue to discuss
* Deep dive session in Next-10 meeting for each priority, invite other working groups
  for particular sessions or go to their meetings. (Michael to Schedule)
* Open issue discussing pre-builds/ways we can reduce impact of long build time (Tierney) 
* Plan deep dive on Maintaining/growing the level of contribution in future Next-10 meeting (Michael)
* Open issue in TSC repo for
    * “Should TSC be more active in future vision/direction?”
    * "Should top level priorities be strategic intiatives?"
    * Agreed we should wait to do this until after we have the PR to node core with the
      technical priorities.
