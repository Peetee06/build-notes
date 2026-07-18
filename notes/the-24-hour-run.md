# The 24-hour run
The project was set up to run autonomously. The pull request checks ran formatters, linters, tests, and even AI reviews. Auto-merge on green enabled.  

After having brainstormed the main feature of the mobile app for a few hours and written a comprehensive implementation specification, I handed it off to an agent for implementation.  

It dispatched subagents for different tasks and orchestrated the whole implementation.  

About a day and ~15 merged pull requests later it was finished, all pull request checks were green, and the full feature landed on main.  
 
I started the app and realized that the feature wasn't working.


## The realization
I was excited. It was the first time an agent ran autonomously for so long and all automated checks I built before were passing.  

But the feature didn't work. Tapping the primary button didn't do anything.  


## The root cause
Each subagent built its own part of the feature. But no one wrote integration tests.  

The AGENTS.md and agent skills described how to build a feature using test-driven development (TDD) and the pull request checks verified it. But they didn't mention integration tests or end-to-end tests at all.  

That led to the feature seemingly being fully built, while it was really a set of working but disconnected pieces.


## What I changed
I fixed this in multiple ways.
- Built a `/verify` skill that enables agents to launch and drive the app to do manual testing
- Extended the AGENTS.md to prompt agents to write integration and end-to-end tests when implementing features
- Added pull request checks to ensure every feature has specified acceptance criteria with corresponding and passing tests


## The takeaway
Agents need specific context on what success looks like. Otherwise, they'll follow the given process and claim "Done — the full specification is implemented," without verifying the output. This may sound obvious on the surface, but this experience made me realize just *how* specific the context needs to be.
