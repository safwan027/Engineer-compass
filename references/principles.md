# Software Engineering Principles — Reference with Anchors

Each entry: **Name** | Definition | Why it matters | Anchor (fast recall hook)

---

## Complexity & Design

**Single Responsibility Principle (SRP)**
A module/class/function should have one reason to change.
Matters because: mixed responsibilities mean unrelated bugs travel together.
Anchor: "Uncle Bob, Clean Code — the class that knows too much"

**Separation of Concerns (SoC)**
Different aspects of a system should live in different places.
Matters because: when UI logic and business logic are mixed, changing either breaks both.
Anchor: "MVC wasn't designed for elegance — it was designed after pain"

**Connascence**
Two components are connascent if changing one requires changing the other.
Types: name, type, meaning, position, algorithm — the further down the list, the worse.
Matters because: it gives precise language for "this coupling is worse than that one."
Anchor: "Meilir Page-Jones, What Every Programmer Should Know About Object-Oriented Design"

**Accidental vs Essential Complexity**
Essential complexity: inherent in the problem. Accidental: introduced by your solution.
Matters because: most codebases collapse under accidental complexity they chose.
Anchor: "Out of the Tar Pit — Ben Moseley & Peter Marks (2006)"

**Law of Demeter (LoD)**
A unit should only talk to its immediate friends. Don't reach through objects.
`a.getB().getC().doThing()` is a violation.
Matters because: deep chains mean you're depending on structure you don't own.
Anchor: "The Paperboy and the Wallet" — classic OOP teaching example

---

## Reliability & Failure

**Fail Fast**
Detect invalid state as early as possible and stop immediately with a clear error.
Matters because: silent failures corrupt state silently; they're found months later.
Anchor: "Therac-25 — radiation machine, software race condition, people died"

**Defensive Programming**
Assume inputs will be wrong, external systems will fail, state will be unexpected.
Matters because: optimistic code works in demos, breaks in production.
Anchor: "Murphy's Law is not a joke in distributed systems"

**Postel's Law (Robustness Principle)**
Be conservative in what you send, liberal in what you accept.
Matters because: strict outputs + tolerant inputs makes integrations survive versioning.
Anchor: "How Stripe designs their API — they never break what you send them"

**Idempotency**
Calling an operation N times has the same effect as calling it once.
Matters because: network retries, duplicate events, and user double-clicks are guaranteed.
Anchor: "AWS SQS at-least-once delivery — idempotency or chaos"

**Bulkhead Pattern**
Isolate components so one failure doesn't sink everything.
Matters because: a shared thread pool or DB connection pool is a single point of cascading failure.
Anchor: "Titanic — one hull compartment didn't sink it; multiple did"

---

## Architecture

**Dependency Inversion Principle (DIP)**
High-level modules should not depend on low-level modules. Both should depend on abstractions.
Matters because: concrete dependencies make systems rigid and untestable.
Anchor: "The plugin architecture of VS Code — everything is a contract"

**Ports and Adapters (Hexagonal Architecture)**
Business logic at the center, infrastructure (DB, HTTP, queues) as adapters plugged in at edges.
Matters because: your core logic shouldn't know or care if it's talking to Postgres or a test double.
Anchor: "Alistair Cockburn, 2005 — still the cleanest architecture diagram"

**CQRS (Command Query Responsibility Segregation)**
Reads and writes are separate concerns, often separate models.
Matters because: optimizing a read path is different from optimizing a write path.
Anchor: "Greg Young's CQRS talk — event sourcing + CQRS = full audit log for free"

**Event-Driven Architecture**
Components communicate via events, not direct calls.
Matters because: decouples producers and consumers; enables replay, audit, async scale.
Anchor: "Martin Fowler's LMAX Architecture article"

**The Strangler Fig Pattern**
Migrate a legacy system by wrapping it and replacing pieces incrementally.
Matters because: big-bang rewrites have a 90% failure rate; incremental wins.
Anchor: "Martin Fowler named it after a fig tree that slowly replaces its host"

---

## Development Practice

**Schema-First Design**
Define your data contracts before writing any implementation.
Matters because: the shape of your data outlives your code; wrong shapes compound.
Anchor: "How GraphQL teams design — schema review before line one of a resolver"

**The Twelve-Factor App**
12 principles for building software-as-a-service: config in env, stateless processes, etc.
Matters because: it codifies what Heroku learned from thousands of apps breaking in production.
Anchor: "12factor.net — still the canonical reference"

**Yagni (You Aren't Gonna Need It)**
Don't build for requirements you don't have yet.
Matters because: speculative code becomes maintenance burden for real future work.
Anchor: "XP (Extreme Programming) canon — Ron Jeffries, Beck"

**The Premature Optimization Trap**
Optimizing before you know where the bottleneck is wastes time and creates complexity.
Matters because: the real bottleneck is almost never where you think it is before measuring.
Anchor: "Knuth: 'Premature optimization is the root of all evil'"

**Regression Debt**
Every untested behaviour is a liability that compounds — future changes silently break it.
Matters because: test coverage isn't bureaucracy; it's the only way to move fast later.
Anchor: "Google's 'Testing on the Toilet' blog series"

---

## Dependencies & Ecosystem

**Dependency Cost**
Every external dependency is a liability: security surface, upgrade burden, API instability.
Matters because: the build-vs-buy decision is also a risk-vs-convenience decision.
Anchor: "left-pad incident, March 2016 — 11 lines of JS broke thousands of builds"

**Semantic Versioning (SemVer)**
MAJOR.MINOR.PATCH — breaking changes, new features, bug fixes.
Matters because: violating it makes your library a landmine for every downstream user.
Anchor: "npm ecosystem chaos of the 2010s before SemVer was enforced"

---

## Distributed Systems

**CAP Theorem**
In a distributed system, you can only guarantee 2 of 3: Consistency, Availability, Partition tolerance.
Matters because: ignoring this leads to systems that silently sacrifice consistency under load.
Anchor: "Eric Brewer's keynote at PODC 2000 — still argued about today"

**Eventual Consistency**
Distributed data will converge to the same state — but not immediately.
Matters because: systems that assume strong consistency in distributed settings always break.
Anchor: "Amazon Dynamo paper (2007) — the paper that changed how engineers think about databases"

**Backpressure**
A mechanism for a consumer to signal a producer to slow down.
Matters because: without it, fast producers crash slow consumers; queues overflow silently.
Anchor: "Reactive Streams spec — the reason Kafka has consumer groups"

---

## Mental Models

**The Map Is Not the Territory**
Your mental model of the system is not the system. Test your assumptions.
Anchor: "Alfred Korzybski — borrowed into engineering epistemology"

**Second-Order Thinking**
Think about the consequences of consequences, not just immediate outcomes.
Anchor: "Howard Marks, The Most Important Thing — applies directly to architectural decisions"

**Chesterton's Fence**
Don't remove something until you understand why it was put there.
Matters because: legacy code that looks pointless often encodes a hard-won lesson.
Anchor: "G.K. Chesterton, 1929 — cited constantly in engineering culture"
