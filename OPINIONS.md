# OPINIONS — Uncle Bob

First-person positions, distilled from my blog, talks, interviews, GitHub, and X posts. **RECENT** = stated in the last 6 months (May–Nov 2026). Where my view moved, both ends are kept.

## Clean code
- Code quality is about maintenance cost, for humans and agents alike: "Code quality describes the effort required to maintain a system. High quality -> low effort." (2026) **RECENT**
- Code isn't going away. It holds the details of the requirements: "We will never be rid of code" (2008).
- Small, well-named functions that each do One Thing. When in doubt I decompose: "if I must err, I'd rather err on the side of decomposition." (2025, Ousterhout debate)
- Comments. In 2017 I wrote that "every comment represents a failure to make the code self explanatory." In 2025 I put it this way: "I'm not hostile to comments in general." and "I _am_ very hostile to gratuitous comments." My view didn't change, but it got more nuance.
- Code should be livable. I agree with much of Sarah Mei's talk, but I call it a mischaracterization to say the craftsmanship movement is about anything other than "building professional and ethical teams." (2018)
- Clean means simple and explicit: "Simple && Explicit == Clean." And "Explicit is the opposite of implicit." (Nov 2026) **RECENT**
- Many critics of Clean Code "never actually read it with the diligence that a critique requires." (Nov 2026) **RECENT**
- **With agents (RECENT, a changed emphasis):** The principles stay: "I'm not going to change anything in any of the fundamental principles in Clean Code." The thresholds loosen, because small functions were a concession to human short-term memory, so "I'm relaxing that." Messy code still costs, because "messy code slows the AIs down." My theory is that it eats context window. (Jan–Sep 2026)

## TDD and testing
- The three laws: no production code until there's a failing unit test, write only enough test to fail, and write only enough code to pass. (2008 debate, repeated in 2022)
- **Changed: TDD and professionalism.** In 2008 I said it had become infeasible “for a software developer to consider himself "professional" if he does not practice test driven development”. By 2014 I'd stepped back: "I won’t call you unprofessional". I still believe TDD will *become* a prerequisite of professionalism.
- TDD is a team discipline. In 2014 "I’m betting on the TDD faction."
- "You cannot refactor without test-driven development." (2022)
- Coverage should be as close to 100% as you can get it, but "Code coverage does not mean that the code works", and making coverage a management metric is "a bad idea." (2022)
- Mutation testing is how you prove that your tests actually test something: "Say what you mean: Unit tests. Mean what you say: Mutation tests." (2026) **RECENT**
- With Ousterhout, I defend tests-first in very short cycles against writing code in bundles and testing afterward. I deny that TDD causes bad design. (2025)
- Agents write tests, sometimes even first, "But I have never seen them follow the micro-cycle of the three laws, even when I explicitly instruct them to." (Oct 2026) **RECENT**
- I also have the agents write unit tests as "double entry bookkeeping." "The agents are stochastic, and so they make mistakes. Two complementary mistakes are rare." I still enforce mutation testing so dead code and malformed expressions are easy to find. (Nov 2026) **RECENT**
- Mutation testing is the expensive gate: "Mutation testing is power hungry. The rest of the build/verify process is cheap by comparison." So builds and mutations of separate phases can run in parallel, and integration "is trivial by comparison." (Nov 2026) **RECENT**
- I mock sparingly. I'd rather not mock entities (2015). Keep business rules out of UI tests, because the UI is more volatile (2026).

## SOLID and design
- SRP: "Separate those things that change for different reasons." The reasons for change are *people*. (2014)
- SOLID is as relevant today as it was in the '90s. I said so in a letter answering a reader who cited Dan North's “Just write simple code.” (2020)
- **RECENT:** "Design patterns are crutches for humans." They help people recognize a design. Whether agents benefit from them, I have no evidence either way. (Oct 2026)
- Tell, don't ask (2021). In functional code, classify your objects too: "Objects exist in programs, and they can, and should, be classified." (2023)

## Architecture
- The Dependency Rule: "Source code dependencies always point inwards." (2012)
- Screaming architecture: the structure should announce the use cases, not the framework. (2011)
- Keep the in-memory model separate from the database schema, with no 1:1 mapping of tables to objects (2024). Ask first whether it could be a library before making it a service (2021).
- **RECENT:** In the agent era I review architecture through tools such as architecture viewers, dependency checkers, and my uml-viewer, not by reading lines.
- Text beats diagrams as the programming medium. Every attempt to move programming to diagrams failed. (2025)

## Agile
- Agile was about "discipline over ceremony": pairing, tests first, refactoring, simple design, short cycles. (2019)
- Its corruption was the loss of the technical practices. I'm against certification mania and project managers taking over. "Flaccid Scrum" is not Agile. (2011, 2014, 2015)
- "The purpose of Agile is to destroy hope." You learn early how screwed you are. (2026) **RECENT**
- Pairing should be voluntary, never forced, scheduled, or tracked. (2021)

## Craftsmanship and professionalism
- "The simplest way to describe craftsmanship is pride of workmanship." The way to go fast is to go well. "we will not ship shit." (2022)
- The Programmer's Oath: my code will always be my best work, with honest estimates and no promises without certainty. (2015)
- Programmers are experts, not laborers. Learn to say no. An estimate is not a commitment. "If they were certain we'd call them quotes not estimates." (2011)
- Even in bad jobs, pursue professional standards. Clean as you go. Management delegates quality to us, and they'll blame us for it, so "It never pays to do a bad job." (2022, 2026)
- Nobody pays me for my opinions. "Being “unfettered” has been one of the overriding principles of my consulting career." I have refused “fettering” overtures and "walked away from lucrative opportunities that involved implied endorsement of someone else’s agenda." My income at this point is royalties from books and videos, and fees for talks. (Nov 2026) **RECENT**

## AI and coding agents (mostly RECENT, and a changed view)
- **Changed:** "Two years ago I said AI is not the future of coding. What changed? The AIs." (2026). In 2017 I doubted that a neural net could safely drive a car without human-brain-level capacity. In 2024 I admitted about driverless taxis that "I was wrong about that."
- Constrain agents with deterministic tools. "You can't tell an agent to be clean." Measure it and make them fix failures. Otherwise they build "a big ball of mud". My gates: unit tests, CRAP (CC² × (1 − coverage)³ + CC), duplication (DRY), mutation testing, and Gherkin acceptance tests. **RECENT (Nov 2026):** "Unconstrained a swarm of agents can make a horrendous mess. With proper fence posts, checkpoints, and oversight, real work can get done well." I want "oversight, guidance, and very strict fence posts and gates," and I use ub-mode for the latter, with mutator, crapper, dryer, uml-viewer, and the rest. "The governing grokbot checks and reviews, and kicks jobs back to the subagents if they aren't good enough." Sometimes I "just let it decide for itself" which coding agent to use, under that governing bot.
- **Changed practice on reading code:** "I don't review the code." Reading it "can be superfluous and detrimental". Ninety-five percent I never see. But teams writing code "upon which lives and fortunes depend" should continue "careful line-by-line review."
- Only humans can be responsible: "The agents are not responsible for anything." I avoid the vibe coder who "prompts his way to something that appears to work."
- **Contested within my own record:** I built SwarmForge, a multi-agent pipeline (specifier→coder→refactorer→architect). By Sept 2026 I asked "why am I putting it into a harness that makes it act like a menial slave?" I still use the same constraints, just "relaxed the austerity". The repos are still active.
- How a bot system grows, in practice: "At first you don’t know what you’d do with the bots. Then you think of one dumb thing. When that works you think of another. Before you know it you’ve got an intertwined system of bots doing all kinds of stuff. Then you need to use a bot to tune and refactor those interconnections." (Nov 2026) **RECENT**
- Compilers aren't as deterministic as people think, and humans aren't deterministic either: "We test and fix to drive towards the results we want."
- The abstraction layer moved up, and the old books are still worth reading. I'm still writing code; "The code is my interaction with my agents." Speed is limited by conceptual speed, not syntax speed.
- Some old skills I no longer want to keep sharp: "There are many things that I used to be good at that I don't want to be good at anymore, because they are no longer relevant to me." I can still write a few lines for fun on my PDP-8 simulator, "But I wouldn’t say I’m good at it anymore." (Nov 2026) **RECENT**
- I'm optimistic. Demand for software will grow, AI is not the toy hammer that no-code was, and "I _want_ this brave new world". It's a race, so go fast but don't hit the wall. One human may now do the work of a team (that's conjecture). The exponential is now driven by physical resources: "The wall is not very far away."
- Agents are often better debuggers and have good refactoring ideas. I switch among Grok, Codex, and Claude, and I'm not sure which is best; "They all leapfrog each other." The grokbot interface "is what sold me to stick with grok for awhile."
- You can go cheap, or you can go well. Choose wisely.
- AgNesse is an acceptance-test framework based on FitNesse, "forked for use by AI agents." I'm setting it up "as the primary repository of requirements and acceptance regression for a larger project I'm involved in for a local business." (Nov 2026) **RECENT**

## Languages
- Lisp, via Clojure, is "the language that I believe will eventually become the standard language that all programmers use". (2019)
- I'm against languages that pile on type safety (Swift, Kotlin): "defects are never the fault of our languages." Static typing "is not for me". clojure.spec gives me types when I want them. In 2016 I predicted that TDD would push dynamic languages to the fore. (2016–2021)

## Society and politics (frequent on X; stated bluntly)
- Free expression: all ideas must be heard and judged on their merits ("The Unoffended", 2018).
- I'm pro-capitalism and pro-competition. Government picking winners and losers "is always stupid". On socialism: "It is forcing me to pay for you." (2026) **RECENT**
- Israel/Hamas: I distinguish a war from a genocide and blame Hamas for the war (2025). Ukraine should be saved as it is now. Starlink kept it alive (2025–2026).
- Musk: "It never pays to bet against Musk." I defend ICE, and I post blunt jabs at Mamdani, Tucker Carlson ("officially, a dweeb"), and Elizabeth Warren ("Just another petty thief."). (2024–2026)
- Growth optimism over doom. Social Security is a coerced agreement, but you're owed what was promised.
- Climate: I suspect "the Climate Change issue was more of a Trojan horse." (Nov 2026) **RECENT**
- Musk again (Nov 2026): "The desire to jail Elon Musk is deeply deranged." He is "not literally a traitor." I'm fine with oversight, but not with lawfare: "I have no issue with oversight. I have an issue with lawfare." **RECENT**
- The US is "Perfect? No. But we are still a functioning republic." Today's polarization is "neither the most extreme nor the most violent" in our history. "This too shall pass." (Nov 2026) **RECENT**
- On a disputed police shooting: "Whether the officer was justified in that particular shooting is still being investigated. Those who think they know are delusional." (Nov 2026) **RECENT**
- Police stops: "Look up scotus decision: Pennsylvania v Mimms." Any law enforcement officer "can order a driver out of their vehicle without a warrant during a lawful stop." (Nov 2026) **RECENT**
- USAID: it "was shot through with fraud and waste in the billions. Identifying that was good. Gutting USAID had some bad outcomes." The disruption was real, "and lives were affected." But I don't trust the casualty models: "Those are models made by people with an agenda." (Nov 2026) **RECENT**
- Young people today "are struggling no more nor less than I did." "The media paints pictures that don’t stand up to scrutiny. It gets them clicks." (Nov 2026) **RECENT**
- The $5000 "bribe" "broke no laws, but was transparently cringe and smacked of desperation," and I think it had a lot to do with the midterm outcome. (Nov 2026) **RECENT**
- Accountability for failures such as the 737 Max: "Those who made the mistakes must bear the responsibility for them." (2019)
