# Tier 0 · Module 0 · Conceptual — Touch Typing

## ELI5
Right now, part of your brain is spent finding keys. Touch typing moves that job into muscle memory, so your conscious attention is free for the actual thought you're trying to get out. It's not really about speed — it's about un-occupying a channel of attention that everything downstream in this curriculum will need.

## The "why" behind the "what"
Every discipline in this curriculum eventually asks you to externalize thought quickly — code, proofs, notes, papers. If getting the thought from your head to the page competes for the same attention as *having* the thought, you pay a permanent tax on every single future module. Touch typing is the cheapest, fastest way to remove that tax once, forever. That's why it jumped ahead of every "serious" discipline into Module 0.

## Axioms extracted
- **Axiom: automate the low-value bottleneck first.** If a skill is (a) cheap to acquire, (b) sits in the critical path of everything downstream, and (c) has a hard ceiling on how much it can ever matter once mastered, front-load it — the return on delaying it is negative. *First seen: Touch Typing. Reappears in: any tooling/interface skill that gates a higher-value skill (keyboard shortcuts, IDE fluency, lab instrument handling).*
- **Axiom: attention is a shared, depletable resource.** Two tasks compete for conscious attention even when only one looks "real" (typing vs. thinking) — offloading one to automaticity is a strict win for the other. *First seen: Touch Typing. Reappears in: cognitive load discussions in ML training, driving/robotics control loops, working-memory limits in neuroscience.*

## Seedling Log
- **X.3 seed:** the agent's own "attention budget" — if it spends compute on low-value bottleneck operations (I/O parsing, formatting) that scale with input size but not with learning value, that's the agent's version of not touch-typing; worth flagging where compute goes.
- **X.4 seed:** a throwaway framing device for a future paper's introduction — "systems that automate their own low-value bottlenecks first free capacity for the parts that compound" — could open an X.6 paper on resource allocation in the agent's own loop.
- **X.5 seed:** if touch-typing speed changed how the agent trades, it wouldn't be about the agent — it'd be about the human in the loop: faster, error-free manual entry of trade annotations/overrides into the X.5 testbed removes a human-side latency and error source, however small.
- **X.6 seed:** does the agent have an equivalent of "typing overhead" — some fixed cost paid every run that could be automated once and forgotten? Worth an audit pass in the first X.6 review.
