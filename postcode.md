# PostCode: Program Projection Environment
## Research Direction and Initial Development Plan

**PostCode** is the current working project name.

---

## 1. Motivation

The long-term question motivating this project is:

> **What does programming become when humans increasingly delegate implementation to agents?**

A particularly interesting version is:

> **If humans are no longer routinely reading or writing TypeScript, Python, Rust, etc., why should those source languages remain the primary persistent representation of a program?**

This is a motivating research curiosity, not a premise of PostCode.

It is entirely possible that conventional source remains an excellent canonical representation even when humans rarely inspect it. It is also possible that source contains information that cannot usefully be replaced by higher-level views, or that agents themselves continue to work best with conventional languages.

PostCode should be capable of producing evidence against the motivating intuition.

The immediate question is deliberately narrower:

> **Can trustworthy, read-only projections of conventional codebases become a viable way for humans to investigate and supervise software instead of routinely reading source?**

If so, a natural next question is:

> **When are projections preferable to source, and when is source preferable to projections?**

PostCode need not demonstrate that projections universally outperform source. Discovering which kinds of software questions are well served by projections—and which continue to send the developer back to source—is itself a useful result.

### 1.1 What PostCode does not establish about source

There are at least three distinct questions:

1. **Human representation:** Does source need to remain the primary representation through which humans understand and supervise a program?
2. **Agent representation:** Is source the best representation for coding agents to consume and manipulate?
3. **Persistent program representation:** Should source remain the canonical durable representation from which the program is built?

PostCode directly investigates only the first.

Even a maximally successful PostCode—one in which developers can conduct sustained software work without routinely inspecting source—would not establish that source should disappear.

Agents might still work best with conventional source. Source might still be the best canonical representation. Or some future system might eventually replace source with a different persistent representation.

Those are separate research questions.

PostCode may remove one historical reason for source's privileged status:

> Humans need source because source is how programmers understand programs.

It does not establish what should replace source, or even that source should be replaced.

---

## 2. Core Idea

PostCode is a read-only application that watches a filesystem/Git repository and allows the user to investigate the program through any number of projected views.

Editing happens elsewhere: Claude Code, Codex, an IDE, command-line tools, a human editor, etc.

PostCode notices repository changes and updates its live views.

```text
                    external tools
                edit / build / test / etc.
                        │
                        ↓
                 filesystem + Git
                        │
                        ↓
             analysis / adapter layer
                        │
                        ↓
           read-only PostCode workspace
```

PostCode includes a prose interface for investigation and query planning, not initially for editing.

For example:

> Show me everything related to media synchronization.

or:

> Why does this exist?

or:

> Why is this functionality split across two modules?

These questions need not all be answered in the same way.

Some may resolve into mechanically derived projections. Others may require recorded rationale, historical evidence, tests, runtime observations, or interpretation of several kinds of evidence.

The important distinction is not simply between “mechanical projection” and “LLM answer.”

It is between claims with different **provenance and epistemological status**.

### 2.1 Lenses, projections and views

PostCode distinguishes three related concepts that should not be used interchangeably.

**Lens** describes the aspect of the program being investigated: the question being asked of it.

Examples include:

- dependencies;
- callers;
- references;
- construction;
- mutation;
- tests;
- behavior;
- history;
- rationale.

A lens answers:

> **What aspect of this subject are we interested in?**

**Projection** is the information produced by applying a lens to a particular program state and subject.

Conceptually:

```text
projection = lens(repository, revision, subject)
```

A projection includes not only its content but the qualifications necessary to understand what that content establishes.

For example, applying a callers lens to `MediaManager` might produce:

```text
Subject
  MediaManager

Direct static callers
  A
  B
  C

Method
  TypeScript static analysis

Guarantee
  Shown direct static calls are real.

Limitation
  Calls through escaped closures cannot be
  exhaustively determined.
```

**View** is the human-facing presentation of a projection.

A projection might be presented as:

- a graph;
- a table;
- a tree;
- a timeline;
- annotated text;
- a diagram;
- a combination of these.

A visualization is therefore one kind of view, not a synonym for projection.

This distinction allows PostCode to choose presentation independently of the information requested.

For example:

> What depends on `MediaManager`?

The human need not specify:

> Draw a dependency graph.

PostCode can identify an appropriate dependency lens, derive a qualified projection, and then choose a useful view for the resulting information.

Four dependencies might be best shown as a small graph.

Eighty-seven dependencies might be better shown as a searchable or clustered table.

A rationale projection might be best presented as annotated text rather than graphically at all.

Thus the user can primarily specify an **information need**, while PostCode helps choose both the lens and the representation appropriate to answering it.

The terminology is therefore:

> **Lens:** what aspect are we asking about?  
> **Projection:** what information does that lens produce here?  
> **View:** how should that information be presented to the human?

The boundaries need not become formal abstractions prematurely. They are primarily intended to keep the design vocabulary clear.

### 2.2 PostCode is not an AI code-review system

PostCode should be explicitly distinguished from the increasingly crowded category of AI code-review and pull-request-review tools.

Its organizing abstraction is not:

> Find problems in this patch.

It is:

> Help me investigate the current program through useful, trustworthy projections.

Reviewing an agent's recent changes is one important application of PostCode, particularly through revision and projection comparison.

But PostCode is not fundamentally organized around:

- pull requests;
- patch review;
- defect detection;
- automated review comments;
- approval/rejection of agent changes.

Its subject is the **program**, viewed through multiple qualified projections.

---

## 3. Why Read-Only First?

Directly modifying projected representations raises difficult questions about semantics, authority, round-tripping, ambiguity and implementation conformance.

Those questions are interesting, but unnecessary for the first experiment.

The existing workflow already provides an adequate modification interface:

> **Tell a coding agent in prose what to change.**

PostCode can therefore concentrate on the less-solved problem:

> **How should the human inspect and understand the resulting program?**

This also keeps PostCode independent of any particular coding agent.

Again, this separation is methodological rather than a claim about the eventual programming system.

PostCode investigates the **human inspection surface**.

It does not investigate whether coding agents themselves would benefit from a richer semantic representation, nor whether such a representation should eventually become the persistent program.

---

## 4. Fundamental Epistemological Rule

The requirement is **not** that every projection be exact or complete.

The requirement is:

> **Every projection must be accurate about what is known, what is asserted, what is observed, what is inferred, and what cannot be determined.**

For example:

> Direct static callers: A, B and C.  
> Additional callers through escaped closures cannot be exhaustively determined.

or:

> According to a source annotation, this module exists to cache remote catalog state.

or:

> Tests X and Y reject duplicate media IDs.

or:

> **Interpretation:** These tests appear intended to protect uniqueness of media IDs.

or:

> **Interpretation:** The available evidence suggests that these modules were separated to isolate remote synchronization from local catalog management.

or:

> This analysis cannot determine whether this callback ultimately performs filesystem I/O.

or simply:

> Cannot project this property reliably.

The unacceptable result is presenting partial, historical, asserted, observed, or inferred information in a way that implies a stronger claim than the evidence supports.

For mechanically derived information, a projection might therefore be:

- exact;
- sound but incomplete;
- complete but over-approximate;
- observational;
- unavailable.

Other kinds of information need different qualifications.

The terminology need not be finalized in PostCode. Plain-English qualification may initially be preferable.

Two things should always remain conceptually distinct:

**Provenance/method** — where the information came from or how it was obtained.

**Epistemological status/guarantee** — what can safely be concluded from it.

For example:

```text
Method
  TypeScript static analysis

Guarantee
  All shown direct static import edges are real.
  Dynamic imports are not included.
```

or:

```text
Claim
  MediaCatalog exists to avoid repeated remote queries.

Provenance
  Source annotation in MediaCatalog.ts

Status
  Recorded design assertion.
  May be historical or stale.
```

or:

```text
Claim
  Duplicate media IDs are invalid.

Evidence
  Tests X, Y and Z

Status
  Interpreted test intent.
  The tests establish particular expected behavior,
  but not necessarily the complete intended invariant.
```

or:

```text
Claim
  MediaCatalog separates local catalog state
  from synchronization policy.

Evidence
  Source structure + Git history + tests

Status
  Interpretive explanation.
  Plausible but not mechanically established.
```

### 4.1 Epistemological status is part of the projection

Epistemological qualification must not exist only in internal metadata or surrounding documentation.

> **The status of a claim must survive into the human-facing view of that claim.**

If PostCode displays:

> Duplicate IDs are rejected.

when the stronger defensible statement is:

> **[interpreted intent]** Duplicate IDs are rejected.

then PostCode has violated its own epistemological contract even if some internal data structure correctly records that distinction.

The eventual UI might represent status through:

- text;
- badges;
- typography;
- icons;
- expandable evidence;
- interaction;
- some combination of these.

That is a design question for experimentation.

The requirement is not.

A weaker claim must not visually masquerade as a stronger one.

The governing principle is:

> **Graceful refusal or explicit qualification is preferable to plausible-looking certainty.**

Trust is critical. Once subtle errors cause the user to doubt all projections, the environment loses its value as an alternative inspection surface.

---

## 5. Sources of Program Knowledge

Program understanding can draw on several epistemologically different sources.

PostCode should not collapse them into a single category of “facts.”

### 5.1 Derived facts

These are established through some defined analysis.

For example:

> `SyncReconciler` imports `MediaCatalog`.

or:

> These three statically identifiable functions directly call `reconcile()`.

The relevant adapter should describe what the analysis does and does not establish.

### 5.2 Recorded assertions

Programs and their histories contain statements made by humans or agents about the program.

Possible sources include:

- source comments;
- structured annotations;
- architecture/design documents;
- commit messages;
- PR descriptions;
- issue discussions;
- other project documentation.

For example:

```text
MediaCatalog exists to avoid repeated remote catalog queries.

Status
  Recorded assertion

Source
  Annotation in MediaCatalog.ts
```

PostCode can establish precisely that this explanation was recorded.

It cannot thereby establish that the explanation is true, current, complete, or still the reason the code exists.

That distinction should remain visible.

### 5.3 Behavioral or observational evidence

Tests, runtime traces, profiler output, debugger observations and similar evidence establish something different again.

For example:

```text
Tests X and Y reject duplicate media IDs.

Status
  Derived observation about test behavior
```

That is stronger than an LLM merely guessing that duplicates are invalid, but weaker than proving that rejection of duplicates is an intended invariant of the entire system.

Similarly:

```text
Function A called function B 417 times.

Status
  Runtime observation

Scope
  Test run X
```

This is an accurate observation about that execution, not necessarily a statement about all executions.

#### Tests as projected evidence

Tests are themselves implemented in the source language and may depend on source-language or runtime-specific concepts.

PostCode should not assume that every test has a language-independent interpretation.

Where useful, however, a test can be considered at several distinct levels:

- **test intent** — the behavior or property the test appears intended to protect;
- **test realization** — setup, fixtures, mocks, calls and assertions used to exercise it;
- **evidence** — what passing or failing the test establishes;
- **language/runtime-specific mechanism** — implementation concepts necessary to express or execute the test.

For example:

```text
Test
  rejects duplicate media IDs

Behavior/property
  Duplicate IDs are rejected.

Status
  Interpreted test intent

Evidence
  Test name + setup + assertion structure

Realization
  Creates a catalog containing A.
  Attempts to add another item with A's ID.
  Expects the operation to fail.

Status of realization
  Derived from test structure
```

The behavioral statement may be the more useful human-facing representation.

But it must not be displayed as though its interpretation were mechanically established.

Other tests may fundamentally concern language-specific properties:

> A union containing `undefined` must be narrowed before this operation.

or runtime-specific properties:

> Repeated calls schedule only one microtask.

or implementation properties:

> This operation performs no heap allocation.

Those should not be forced into falsely language-independent vocabulary.

The goal is:

> **Project a test at the highest useful abstraction level that preserves what it actually establishes.**

Tests are particularly interesting because they already occupy a semi-formal boundary between intended program behavior and source-language implementation.

### 5.4 Inferred explanations

Some useful questions inherently require interpretation.

For example:

> Why does this exist?

> Why is this functionality split across two modules?

> What happened to `MediaManager`?

> What would be affected if this went away?

An answer may combine:

- current source structure;
- derived relationships;
- source comments;
- commit history;
- tests;
- issue/PR history;
- runtime observations;
- LLM interpretation.

For example:

```text
MediaCatalog separates local catalog state
from synchronization policy.

Status
  Interpretation

Evidence
  Current source structure
  Tests
  Commit 8fa39c2

Confidence/limitations
  No authoritative current design rationale found.
```

That may be extremely useful while still being an interpretation rather than an established program fact.

---

## 6. Prose Investigation and Lens Selection

The prose interface can support questions at several levels:

> Show me everything related to synchronization.

> What calls this?

> Why does this exist?

> Why is this functionality split across two modules?

> What happened to `MediaManager`?

> What would be affected if this went away?

> What behavior do these tests appear to protect?

The human need not necessarily know which PostCode lens or presentation technique best answers the question.

The prose interface can act as a **query planner**:

```text
human information need
        │
        ↓
prose interpretation
        │
        ↓
lens / subject selection
        │
        ↓
qualified projection
        │
        ↓
appropriate view
```

“Show me everything related to synchronization” may use interpretive query planning to propose candidate entities and useful lenses.

“What calls this?” may map almost directly to a callers lens backed by static analysis.

“Why does this exist?” may select evidence/history/rationale lenses and synthesize several projections.

“What behavior do these tests appear to protect?” may combine mechanically established test structure with recorded descriptions and explicitly identified interpretation.

Thus PostCode may reduce two different kinds of effort:

1. determining **what information about the program would answer the question**;
2. determining **how that information should be presented**.

The important rule is:

> **Interpretation may guide investigation and may itself be useful output, but it must not masquerade as mechanically established program truth.**

### Textual views

A projection need not be graphical or mechanically derived.

Its view may be textual and may present recorded or interpreted information, provided the provenance and epistemological status of each claim remain visible.

For example:

```text
Why does MediaCatalog exist?

"Cache remote catalog state and avoid repeated queries."

Status
  Recorded assertion

Source
  Annotation in MediaCatalog.ts


MediaCatalog was introduced during synchronization work.

Status
  Derived historical fact

Source
  Commit 8fa39c2


Tests exercise local lookup and mutation independently
of remote synchronization.

Status
  Derived test relationship

Source
  Tests X, Y, Z


MediaCatalog appears to separate local catalog state
from synchronization policy.

Status
  Interpretation

Evidence
  Structure + tests + history

Caveat
  No authoritative current design rationale was found.
```

Whether this belongs primarily in transient conversation or in a pinnable view should not be decided in advance.

Dogfooding can answer the question.

---

## 7. Entities and Identity

PostCode does not initially require persistent semantic identities or a formal architecture model.

Entities can instead be **discovered from the implementation according to explicit adapter rules**.

Possible entities include:

- repositories;
- packages;
- modules;
- files;
- namespaces;
- types/classes/interfaces;
- functions/methods;
- exported symbols;
- tests;
- fields or variables where useful.

The available entities may vary by language.

### Persistence of Human Attention

PostCode can persist workspace state without claiming that program identities survive arbitrary transformations.

For example:

```text
MediaManager / dependencies
SyncReconciler / callers
sync tests
```

This tool state records:

> **What was I paying attention to?**

If `MediaManager` later disappears, PostCode need not infer that another entity is its conceptual successor.

Instead:

```text
MediaManager / dependencies

⚠ Entity no longer exists in the current revision.

Last present:  8fa39c2
Removed in:    b27d9e1
```

The user can then ask:

> What happened to MediaManager?

Git history plus agent reasoning can address that interpretive question.

Thus PostCode may support continuity of human attention without solving persistent semantic identity.

---

## 8. Workspace Model

A workspace contains an arbitrary number of independent views over projections.

A projected result is approximately:

```text
projection = lens(repository, revision, subject)
```

Its presentation is approximately:

```text
view = present(projection, context)
```

where context might eventually include:

- current investigation;
- number and shape of results;
- available screen space;
- neighbouring views;
- user preferences;
- previous interaction.

A revision may be:

- current working tree;
- branch;
- commit;
- possibly staged/index state later.

Views may be:

**Live** — their underlying projection follows a working tree or branch.

**Pinned** — their projection remains attached to a particular revision.

The user constructs whatever working surface suits the current problem rather than using a predetermined dashboard.

---

## 9. Structural Navigation

Hierarchy may be useful as a **structural lens**, rather than as the universal representation of the program.

For example:

```text
System
 ├─ Publishing
 │   ├─ MediaManager
 │   │   ├─ MediaCatalog
 │   │   ├─ SyncReconciler
 │   │   └─ StagingMirror
 │   └─ ViewerBuilder
 └─ ...
```

Selecting an entity can open other lenses over it.

Containment/decomposition may be hierarchical; dependencies, behavior, data flow, calls and other relationships generally are not.

PostCode should not assume that there is one uniquely correct conceptual hierarchy.

Initially, structural projections should be based only on relationships the relevant adapter can define accurately.

---

## 10. Candidate Lens Families

The initial vocabulary should avoid claims such as “important component” or “architectural responsibility” that inherently require judgment unless those claims are explicitly presented as interpretation.

These are **candidate lenses**, not a proposed universal ontology.

### 10.1 System/repository lenses

Examples:

- module/package hierarchy;
- imports/dependencies;
- exported API;
- test inventory;
- type relationships;
- package/module references.

### 10.2 Entity cross-reference lenses

For an identified entity:

- definition;
- callers;
- callees;
- references;
- construction/allocation sites;
- reads/accesses;
- writes/modifications;
- values passed to/from;
- implementations;
- inheritance/interface/trait relationships;
- ownership/lifetime information where meaningful.

The available facts and guarantees are language-dependent.

Do not manufacture symmetry where language semantics differ.

### 10.3 Test lenses

Potential test projections include:

- test inventory;
- tests associated with an entity;
- entities exercised by a test;
- setup/action/assertion structure;
- behavioral or property summaries where supportable;
- test dependencies;
- tests affected by a projected change;
- language/runtime-specific properties being tested;
- test history across revisions.

For example:

```text
Test
  rejects duplicate media IDs

Behavior/property
  Duplicate IDs are rejected.

Status
  Interpreted test intent

Evidence
  Test name + structure + assertions


Realization
  Creates catalog containing A.
  Attempts to add another item with A's ID.
  Expects failure.

Status
  Derived from test structure
```

PostCode should not require every test to have a language-independent behavioral description.

### 10.4 Path lenses

Potential examples:

- call paths from A to B;
- dependency paths;
- data propagation paths;
- possible control-flow paths.

These may frequently produce qualified rather than exact projections.

### 10.5 Temporal/version lenses

Examples:

- where/when an entity appeared;
- where/when it disappeared;
- callers/dependencies across revisions;
- tests added or removed;
- changes in what a test exercises or asserts;
- the same projection across branches.

### 10.6 Rationale/evidence lenses — if demanded by use

Possible examples:

- recorded rationale for an entity;
- relevant comments/annotations;
- commit history explaining a design choice;
- tests that appear to encode requirements;
- current evidence supporting or contradicting old rationale;
- synthesized explanation with explicit epistemological status.

Whether these become real lens families should emerge from use rather than being assumed.

---

## 11. Source as a Secondary View

Source should not be PostCode's default or primary representation.

However, completely excluding source creates two problems:

1. PostCode loses visibility into when and why source was needed.
2. The cost of switching to another application becomes a confounding source of friction.

PostCode may therefore provide an explicit **Show Source** escape hatch.

Source can be understood as a special view whose underlying information is the conventional implementation itself rather than a deliberately reduced PostCode projection.

Opening source is a legitimate action, not a failure.

Its use should be automatically recorded as part of PostCode's formative observation log.

When practical, PostCode may unobtrusively ask:

> **What information were you looking for?**

Possible quick responses might include:

- missing projection;
- needed more detail;
- wanted to verify/trust-check;
- source seemed clearer;
- needed local implementation logic;
- other.

The prompt should not block access to source and should be easy to ignore.

During dogfooding, source-use frequency itself should not be treated as an unbiased measure of PostCode's success.

The developer is deliberately exercising PostCode and may consciously tolerate inconvenience rather than immediately falling back to source.

Source excursions instead help answer:

> **What information was missing from the projection-based workflow?**

Later evaluation with independent users can address:

> **When developers have convenient access to both projections and source, what do they actually choose, for which tasks, and why?**

---

## 12. Revision and Projection Diffs

During agent-mediated development, one of the most important questions is:

> **What did the agent just change?**

Git source diffs answer that at implementation-text level.

A projection diff could instead answer:

> **What changed at the level at which I was thinking about the program?**

Examples:

- dependency structure changed;
- callers appeared or disappeared;
- object construction moved;
- test relationships changed;
- test behavior or assertions changed;
- a call path changed;
- recorded rationale changed or disappeared.

PostCode does not need sophisticated diff visualization initially.

The smallest experiment is:

> Apply the same lens to the same subject at two revisions and place the resulting projections side by side.

Conceptually:

```text
before = lens(repository, revisionA, subject)
after  = lens(repository, revisionB, subject)

compare(before, after)
```

Later possibilities include:

1. stable correspondence/layout;
2. additions/removals/movement highlighting;
3. overlays;
4. animation;
5. conceptual change summaries.

Projection stability matters especially for diffs: changes in the projection mechanism must not masquerade as changes in the program.

---

## 13. Language Adapters

The first implementation can support one language.

The first adapter should not be prematurely generalized into a universal programming ontology.

Later unfamiliar OSS projects can naturally create pressure for additional adapters.

The rule is:

> **Accrete shared abstractions upward from multiple languages; never discard language-specific semantics merely to fit a shared model.**

Tests are a particularly useful cross-language stress case.

A behavioral test may project naturally into a shared concept such as:

> Duplicate identifiers are rejected.

while another test may fundamentally concern:

- a language's type system;
- ownership or lifetime rules;
- macro behavior;
- module/linking semantics;
- runtime scheduling;
- memory management.

The fact that test **intent** sometimes transfers while the test **mechanism** or even the property being tested does not is useful evidence about the boundary between shared and language-specific abstractions.

If lenses repeatedly prove meaningful across TypeScript, Python, Rust, C++, etc., that provides empirical evidence for a language-independent program vocabulary.

If they do not, do not shoehorn them.

---

## 14. Runtime Information — Post-Initial PostCode

Runtime information fits naturally into the projection model but is not initially required.

Possible later data includes:

- call counts;
- time spent in functions/modules;
- allocation information;
- coverage;
- runtime call graphs;
- observed values;
- active stack frames;
- breakpoint locations;
- debugger state.

PostCode need not become the debugger, profiler or execution environment.

Existing external systems can produce observations:

```text
debugger / profiler / tracer / test runner
                 │
                 ↓
            runtime adapter
                 │
                 ↓
              PostCode
```

Runtime observations have a natural epistemological qualification:

> Observed during run X.

They must not silently become claims about all possible executions.

---

## 15. Explicit Initial Non-Goals

PostCode does not initially attempt:

- source editing;
- test authoring;
- specification of tests through prose or other representations;
- coding-agent integration;
- direct manipulation of projections;
- bidirectional projection;
- a universal IR;
- a new programming language;
- a formal architecture model;
- persistent semantic identity;
- authoritative architectural judgment;
- runtime instrumentation;
- debugger control;
- polished projection diffs;
- a universal cross-language ontology;
- educational tooling;
- determining the optimal representation for coding agents;
- replacing source as the canonical persistent representation.

In particular, PostCode does not need to answer whether future developers can request all tests using purely language-independent concepts.

Nor does success in PostCode establish that coding agents should cease working with conventional source.

---

## 16. Dogfooding and Exploration

Dogfooding is primarily **formative self-study**, not an efficacy experiment.

The central dogfooding question is:

> **What is required to make projection-based investigation viable?**

The developer should deliberately exercise PostCode, including tolerating some friction that might ordinarily cause an immediate return to source.

That is a feature of this phase, not a methodological flaw: sustained use exposes missing representations, bad abstractions, insufficient precision and awkward interactions.

It does mean that dogfooding cannot establish whether other developers would naturally prefer PostCode to source.

### 16.1 PostCode on PostCode

Build the minimum version conventionally, then use PostCode to develop PostCode.

Whenever source would be easier, ask:

> Why would source be easier here?

Sometimes the answer may be a missing lens.

Sometimes the lens exists but the projection lacks information.

Sometimes the projection may contain the information but its view may present it badly.

And sometimes source may genuinely be the best representation.

This distinction itself may prove useful during dogfooding:

> **Was the failure in lens selection, projection capability, presentation, or the underlying idea?**

### 16.2 Enblog

Use PostCode during ordinary Enblog development.

This provides an independent existing architecture and real development tasks.

The aim is not to count how rarely source can be opened.

Instead ask:

> What does PostCode need in order to support this work?

---

## 17. Self-Observation and Formative Logging

PostCode should record its own use rather than relying on the developer to maintain a separate research diary.

Possible automatically recorded events include:

- prose questions asked;
- lenses selected or suggested;
- entities discovered/opened;
- projections produced;
- views opened and closed;
- test projections inspected;
- revisions/branches inspected;
- projection comparisons;
- source views opened;
- navigation between projections and source;
- unavailable or failed projections;
- changes in workspace state.

PostCode should also make it extremely easy to record subjective observations at the moment they occur.

Two particularly useful first-class actions are:

> **Wanted source here**

and:

> **Wish I had lens/projection…**

The distinction may later be worth recording more precisely:

- wanted different information;
- wanted a different presentation of existing information;
- distrusted the projection;
- source was intrinsically clearer.

The goal is not exhaustive annotation.

The goal is to avoid losing useful observations simply because they were not written down at the time.

The log is primarily a **design instrument** during dogfooding, not an unbiased behavioral dataset.

---

## 18. Evidence and Evaluation Strategy

Evaluation should progress in stages rather than treating early dogfooding as a user study.

### 18.1 Stage 1 — Formative self-study

Question:

> **What is required to make projection-based investigation viable?**

Evidence may include:

- sustained PostCode-on-PostCode use;
- Enblog development;
- automatic usage logs;
- contemporaneous subjective observations;
- “wanted source” events;
- “wish I had lens/projection X” events;
- source excursions and their stated reasons;
- design changes motivated by recurring friction.

### 18.2 Stage 2 — External exploratory use

Question:

> **Can unfamiliar developers use this approach, and what happens when they try?**

External users can reveal assumptions caused by the author's prior knowledge and source needs the author did not encounter.

### 18.3 Stage 3 — Comparative user study

Question:

> **When developers have convenient access to both projections and source, what do they actually choose, for which tasks, and why?**

This is the appropriate stage for stronger claims about:

- voluntary source reduction;
- preference;
- task effectiveness;
- speed;
- comprehension;
- confidence;
- trust;
- differences among task types.

---

## 19. Reportable Formative Experience

Dogfooding can produce legitimate design findings and hypotheses when claims are appropriately scoped.

Potential observations include:

- repeatedly wanting a lens showing who can modify an object;
- dependency projections proving less useful than expected;
- repeatedly asking why particular structures existed;
- consulting source for local sequential behavior;
- projection diffs becoming unexpectedly important;
- explicit incompleteness increasing willingness to rely on static-analysis results;
- comments and commit history becoming useful ingredients of projected rationale;
- behavioral descriptions of tests proving useful;
- some tests resisting abstraction because their subject is inherently language-specific;
- PostCode selecting useful views automatically;
- automatic lens selection failing in characteristic ways;
- different presentations proving appropriate for the same projection in different contexts.

The distinction is:

> **Dogfooding can produce design findings and hypotheses; independent evaluation is required for general claims about developer behavior.**

---

## 20. Success and Failure

During the formative phase, success should not be defined primarily as reducing the number of source openings.

A useful early success is:

> **PostCode becomes sufficiently expressive that real development can be carried out primarily through it, while the remaining sources of friction and reasons for consulting source become increasingly identifiable.**

Another useful result is:

> **Recurring lens and projection needs emerge clearly enough to guide subsequent design.**

Failures are equally informative:

- projections are less efficient than source for broad classes of questions;
- useful analyses cannot provide adequate guarantees;
- PostCode frequently chooses inappropriate lenses or views;
- the human must understand the visualization vocabulary well enough that automatic selection adds little;
- recorded rationale is too stale or unreliable to help;
- test intent cannot be projected usefully without source-level detail;
- cross-language abstractions fail;
- important implementation facts routinely escape projection;
- prose + source + existing agents already constitute a better workflow.

Mixed results may be especially interesting.

---

## 21. Research Practice: Speculative Papers

An occasional useful research exercise is to write the paper **before the research is complete**, explicitly as speculative fiction.

Rather than writing only the hoped-for paper, imagine incompatible outcomes:

### A — Projections work

Developers supervising agents substantially reduce routine source inspection.

### B — Source survives

Higher-level projections help in particular circumstances, but source remains extraordinarily efficient and information-dense.

### C — Diffs are the result

Projection diffs substantially improve review of agent-generated changes.

### D — Trust is the result

Representation choice matters less than explicit epistemological guarantees about what projections do and do not establish.

### E — Cross-language vocabulary emerges

Multiple adapters converge on a stable set of language-independent program concepts.

### F — Provenance is the result

The useful replacement for source is an environment that distinguishes derived facts, recorded rationale, behavioral evidence and interpretation while allowing them to be investigated together.

### G — Tests are the bridge

Behavioral test intent can often be separated usefully from source-language realization, while cases that resist abstraction expose important boundaries.

### H — Representation selection is the result

The important capability is not any particular visualization but automatically selecting a useful lens and view for the developer's current information need.

For each speculative result, ask:

> **What observations would make this paper impossible to write?**

---

## 22. Impact Goal

If the work proves worthwhile, it should make a meaningful contribution to how programming evolves in an agent-mediated world.

Possible routes include:

- open-source software;
- research publication;
- eventual collaboration.

Potential research contributions may concern:

- projections as substitutes for source inspection;
- epistemological contracts for program views;
- automatic lens and representation selection;
- combining derived facts, recorded assertions, observations and interpretation;
- tests as projected behavioral evidence;
- projection diffs for supervising agent changes;
- persistence of human attention without semantic identity;
- language-independent versus language-specific abstractions;
- circumstances in which source remains necessary.

> **Build to discover; publish what turns out to have been discovered.**

---

## 23. Publication-Aware Prioritization

Publication opportunities are legitimate factors in research planning.

The distinction is:

> **Publication-aware prioritization is useful; publication-driven distortion is dangerous.**

At suitable checkpoints ask:

- What coherent contribution do we have now?
- What additional work would make it a credible submission?
- Is an appropriate venue/deadline approaching?
- Is that additional work independently useful, or at least inexpensive?
- What useful work would be postponed?

---

## 24. Collaboration Strategy

Collaboration should initially be demand-driven.

Reasons to seek collaborators later might include:

- missing static-analysis/PL expertise;
- software visualization/InfoVis;
- HCI study design;
- runtime/debugger systems;
- empirical software engineering;
- particular language ecosystems;
- independent users becoming necessary;
- a research result crystallizing;
- open-source contributors naturally becoming collaborators.

The guiding principle is:

> **Add collaborators when there is a concrete reason the work will become better with them.**

---

## 25. Impact Checkpoints

Reconsider dissemination and collaboration periodically.

Useful checkpoints include:

- after PostCode-on-PostCode;
- after Enblog;
- after unfamiliar same-language OSS;
- after second-language OSS;
- after an unfamiliar-language challenge;
- after multiple languages;
- before a comparative user study.

At each checkpoint ask separately:

> **Could this be useful enough to affect how people work?**

and:

> **Have we learned something general enough that other researchers should know it?**

Either can be true without the other.

---

## 26. Provisional Experimental Roadmap

**This is not a committed twelve-phase implementation plan.**

Only the Immediate Bootstrap and the first dogfooding loop should currently be treated as planned work.

Everything beyond that is a **candidate experimental direction** recording hypotheses and potentially useful next steps.

Later stages should be changed, reordered, skipped or abandoned according to what earlier work discovers.

The roadmap exists primarily so that useful experimental ideas are not forgotten—not to prescribe the project before PostCode exists.

### Phase 0 — Smallest trustworthy slice

Choose:

- one language;
- one repository;
- a few precisely defined entity types;
- 2–4 lenses with explicit semantics;
- simple views appropriate to their results.

Deliverable:

> A library/command capable of answering a few projection queries and accurately stating their limitations.

### Phase 1 — Minimal projection workspace

Build enough UI to leave PostCode open while developing PostCode.

Include basic self-observation.

### Phase 2 — Live repository watching

Observe external edits and update projections/views.

Begin serious PostCode-on-PostCode dogfooding.

### Phase 3 — Prose investigation and lens selection

Support questions that select subjects/lenses, establish investigation workspaces, choose useful views, or provide appropriately qualified explanations.

### Phase 4 — Revision/branch pinning

Allow the same lens to be applied at multiple revisions.

### Phase 5 — Dogfood-driven lens growth

Add lenses only when real use repeatedly demands them.

Do not assume that every new need requires a new lens: some may require a better projection, a different view, or improved lens selection.

### Phase 6 — Enblog dogfooding

Apply PostCode to a pre-existing real project with independent development goals.

### Phase 7 — Unfamiliar OSS, same language

Separate generalization across codebases from generalization across languages.

Continue within a language only while new repositories are teaching something.

### Phase 8 — Second-language OSS

Allow another language to exert pressure on the existing abstractions.

Do not generalize first.

### Phase 9 — Third language / unfamiliar-language challenge

Preferably choose a language the developer does not know.

Where practical, have coding agents implement the adapter without language-specific guidance from the developer.

Ask:

> **Can PostCode support meaningful investigation of a program whose source language the human cannot comfortably read?**

### Phase 10 — Cross-language refactoring

Only now ask which concepts genuinely survived contact with multiple languages and tasks.

### Phase 11 — External exploratory use

Observe how developers other than the system's author use and understand PostCode.

### Phase 12 — Comparative evaluation

If warranted, compare convenient access to projections and source and ask which developers voluntarily choose for different tasks.

Again, none of Phases 2–12 should currently be regarded as promised work.

> **The next experiment is determined by what the previous experiment teaches.**

---

## 27. Immediate Bootstrap

This is the actual near-term plan.

The first useful PostCode should be almost embarrassingly small.

```text
Repository: ./postcode
Revision: working tree

Entities
  ▾ src
    ▾ analysis
      typescript-adapter
      repository
      projection
    ▾ ui
      workspace
      pane
  ▾ tests
      repository.test
      projection.test

Open views:

┌────────────────────────────┐
│ repository / dependencies  │
│                            │
│ [dependency graph]         │
│                            │
│ Lens: dependencies         │
│ Status: derived            │
│ Method: TS static analysis │
│ Limits: dynamic imports…   │
└────────────────────────────┘

┌────────────────────────────┐
│ Projection / references    │
│                            │
│ [reference table]          │
│                            │
│ Lens: references           │
│ Status: derived            │
│ Guarantee: sound but…      │
└────────────────────────────┘

────────────────────────────────────────────
Wanted source · Missing lens… · Note…
```

Then use it to answer a real question encountered while building the next part of PostCode.

When it fails to answer the question, record the failure in PostCode itself.

That is the bootstrap threshold.

---

## 28. Guiding Principle

Across design, research, languages, tests, evaluation, publication and collaboration:

> **Don't design an abstraction because it seems elegant. Accumulate pressure for it.**

Let real use determine:

- which lenses matter;
- which projections matter;
- which views work;
- when PostCode can usefully select lenses and views automatically;
- which identities matter;
- which kinds of evidence matter;
- which explanations deserve persistent views;
- which aspects of tests can be projected above their implementation language;
- which test properties remain inherently language-specific;
- which abstractions survive across languages;
- whether projection diffs matter;
- where source remains superior;
- and eventually whether source itself is still doing enough conceptual work to deserve its privileged role.

The long-term question remains open:

> **What should the persistent program ultimately be?**

PostCode does not answer that question.

It investigates one prerequisite:

> **What happens when source stops being assumed to be the primary human representation?**

---

# Appendix A — Initial Related-Work Bibliography

This is a **working bibliography**, not a systematic literature review.

Its purpose at this stage is to identify nearby research traditions, potentially overlapping systems, useful methodological precedent, and work that may sharpen PostCode's eventual research questions.

The bibliography should evolve as the project does.

## A.1 Agentic software engineering and changing human roles

**Davis, J. C., Kalu, K., Peng, H., & Patil, P. V. (2026). _Model-Based Agentic Software Engineering (MAGE)._ arXiv:2608.25174.**

Particularly close conceptually. MAGE argues that increased implementation capacity makes explicit abstractions, evidence and engineering obligations increasingly important, and proposes externalizing purposeful representations rather than repeatedly reconstructing consequential properties.

Relevant distinction: MAGE primarily addresses governed agentic engineering and durable engineering structure; PostCode experimentally investigates the human inspection surface while initially leaving conventional code canonical.

**Hassan, A. E., et al. (2025). _Agentic Software Engineering: Foundational Pillars and a Research Roadmap._ arXiv:2509.06216.**

Broad framing of Agentic Software Engineering and the emerging distinction between software engineering for humans and software engineering for agents.

Particularly relevant to PostCode's explicit separation between the representation humans need and the representation agents may need.

**Fowler, M. (2026). _Agentic Programming._**

Discusses the transition from humans directly writing source toward humans overseeing agents that generate it.

Useful contextual motivation rather than direct technical prior art.

**de Halleux, P., Syme, D., & Zorn, B. (2026). _Repositories Are Human/Agent Knowledge Factories._ SIGPLAN Blog.**

Argues that repositories in agent-driven development should become explicit knowledge structures supporting agents and human supervision, including formalized conventions, specifications and validation.

Strongly adjacent to PostCode's motivating problem, but focuses more on repository structure and agent-consumable knowledge than on replacing source as the human inspection surface.

## A.2 Human oversight of software agents

**Dhanorkar, S., Passi, S., & Vorvoreanu, M. (2026). _Human oversight of agentic systems in practice: Examining the oversight work, challenges, and heuristics of developers using software agents._ FAccT 2026 / arXiv:2606.05391.**

Empirical study of experienced developers identifying forms of oversight including a priori control, co-planning, real-time monitoring and post-hoc review.

Especially relevant because developers report difficulty reviewing agent-generated code and use artifacts such as test results as proxies or guarantees during oversight.

Potentially important empirical motivation for PostCode's attempt to provide better human-facing supervisory representations.

## A.3 Code comprehension and software visualization

**Gao, J., Xue, Y., Xie, X., Cao, J., et al. (2026). _Understanding Codebase like a Professional! Human–AI Collaboration for Code Comprehension._ ICPC 2026.**

Introduces CodeMap, an LLM-supported environment for hierarchical codebase understanding informed by interviews with professional code auditors.

CodeMap provides dynamic information extraction and interactive switching between abstraction levels.

Very close prior art for PostCode's projected codebase views.

Important distinction: its usage scenario still treats source inspection in VS Code as the verification surface; PostCode deliberately asks whether qualified projections themselves can support sustained investigation and supervision.

**Merino, L., Ghafari, M., & Nierstrasz, O. (2018). _Towards Actionable Visualization for Software Developers._ Journal of Software: Evolution and Process, 30, e1923.**

Important software-visualization background.

Merino et al. begin from the observation that many studies have found visualization useful for software developers, while adoption in ordinary development remains limited. They identify the effort involved in finding an appropriate visualization as an important barrier and argue for better support in connecting visualizations with developers' immediate tasks.

This suggests a particularly relevant hypothesis for PostCode.

Historically, software visualization has often involved a nontrivial acquisition cost: finding the right tool, configuring it, choosing the appropriate visualization, generating it, and interpreting a representation that may contain considerably more information than the developer's current question requires.

Agent-mediated generation may alter that cost structure.

A PostCode projection can potentially be:

- requested for one particular question;
- generated on demand;
- narrowly scoped to the relevant entities or relationships;
- discarded once it has served its purpose;
- regenerated automatically as the program changes.

Under this model, a visualization becomes less like a separately designed artifact and more like a **query result over the program**.

Moreover, PostCode may reduce not merely the cost of generating a visualization but the cost of **selecting an appropriate representation in the first place**.

The developer need not necessarily know whether the current question is best answered by a dependency graph, call tree, table, timeline, behavioral summary, or some other representation.

The developer can instead express the information need:

> What depends on this?

> What changed here?

> Why does this exist?

PostCode can potentially choose an appropriate lens, derive the projection, and select a view suited to the resulting information.

This changes the interaction from:

> **Which visualization tool should I use?**

toward:

> **What do I need to know about the program right now?**

There may also be a second and independent change in the economics of visualization.

In conventional development, developers continuously read and manipulate source. In doing so, they acquire and refresh a detailed source-grounded mental model of the program as a side effect of implementation work. A separate visualization must therefore provide enough additional value to justify leaving or supplementing an already-familiar representation.

This does not imply that developers can always maintain adequate mental models from source; large and unfamiliar systems have long made program comprehension difficult. The hypothesis concerns the **marginal value** of additional representations when source is already the developer's everyday working surface.

Agent-mediated development may weaken that incidental acquisition of source-level knowledge. If an agent performs much of the implementation, the human may increasingly need to reconstruct only those aspects of the program relevant to the decision currently being made.

This suggests at least three reasons why earlier conclusions about the limited adoption of software visualization may deserve reconsideration:

1. **The cost of obtaining a task-specific projection may fall dramatically.**
2. **The cost of choosing the appropriate lens and presentation may also fall dramatically.**
3. **The human may no longer acquire a detailed source-level model automatically through the act of implementation.**

Put differently:

> **In conventional development, visualization competes with source. In agent-mediated development, visualization may instead compete with having to reconstruct the program from source at all.**

A working PostCode hypothesis is therefore:

> **Software visualization may become more valuable in agent-mediated development because generative systems reduce the cost of producing and selecting task-specific views while delegation of implementation reduces the developer's incidental acquisition of detailed source-level knowledge.**

PostCode can test whether those changes are sufficient to move projected representations from **occasional comprehension aids** toward a **routine working surface**.

This is a hypothesis, not a distinction that should be assumed in advance.

PostCode may instead reproduce the historical pattern: source may remain sufficiently efficient and information-dense that even cheap, automatically selected, targeted projections provide too little additional value.

That possibility makes the Merino et al. work particularly useful prior art rather than merely historical background.

**Code2UML: Agentic LLMs with Context Engineering for Scalable Software Visualization (Văduva et al., 2026). arXiv:2605.24453.**

Generates multiple UML views from repositories across Java, JavaScript, PHP and Python using deterministic IR processing plus specialized agents.

Especially interesting for PostCode because it demonstrates multi-language projection generation while reporting high relationship precision but deliberately limited entity recall.

This provides a concrete nearby example of useful projections whose incompleteness matters.

## A.4 Architecture and agent-generated software

**Konrad, P. M., Adam, T. L., Terrenzi, R., & Ayvaz, S. (2026). _Architecture Without Architects: How AI Coding Agents Shape Software Architecture._ arXiv:2604.04990.**

Argues that coding agents make consequential architectural decisions implicitly through implementation and prompt interpretation.

Relevant motivation for PostCode's supervisory goal: humans may need representations that expose architectural consequences without reconstructing them manually from source.

**Vasilevski, K., Dong, X., Rombaut, B., et al. (2026). _Beyond Correctness: Enhancing Architectural Reasoning in Code LLMs via Scalable Labeling with Agentic Judgment._ arXiv:2606.14948.**

Examines architectural understanding and architectural quality of agent-generated patches rather than functional correctness alone.

Relevant to the broader distinction between source-level correctness and higher-level program properties.

**Sapunov, G. (2026). _Theory of Code Space: Do Code Agents Understand Software Architecture?_ arXiv:2603.00601.**

Studies whether agents construct and maintain structured beliefs about codebase architecture while exploring repositories.

Particularly relevant to the distinction between repeatedly reconstructing relationships from source and externalizing useful program structure.

Unlike PostCode, the subject is primarily the agent's architectural understanding rather than the human-facing representation.

**Irion, J., Leugers, M., Hartwig, P., et al. (2026). _Architectural Constraints Alignment in AI-Assisted, Platform-Based Service Development._ CAiSE Workshops 2026 / arXiv:2605.04973.**

Addresses architectural constraints that general-purpose coding agents may miss and uses structured retrieval/scaffolding to improve alignment.

Relevant to the growing recognition that functional source generation alone is insufficient for reliable agent-mediated engineering.

## A.5 LLMs and software architecture — broader background

**Schmid, L., Hey, T., Armbruster, M., et al. (2025). _Software Architecture Meets LLMs: A Systematic Literature Review._ arXiv:2505.16697.**

Reviews LLM applications to software-architecture tasks including design generation, classification and pattern detection.

Useful starting point for mapping the broader architecture/LLM literature and locating older work that may overlap individual PostCode projections.

## A.6 Human–AI debugging and evidence presentation

**Shen, S., Lu, S., Shen, L., & Luo, Y. (2026). _Debugging Defective Visualizations: Empirical Insights Informing a Human–AI Co-Debugging System._ CHI 2026.**

Not directly about source-code projection, but potentially useful methodological prior art concerning how humans and AI divide investigative/debugging work and how evidence is presented during that process.

This should be read before deciding how strongly it belongs in PostCode's eventual related work.

## A.7 Potentially relevant but more peripheral

Work on:

- explainable AI and uncertainty/provenance visualization;
- information provenance;
- proof-carrying or evidence-carrying systems;
- abstract interpretation and soundness/completeness of static analyses;
- software architecture recovery;
- architecture conformance;
- program comprehension;
- software cartography;
- live programming;
- projectional editors;
- bidirectional transformations/lenses;
- model-driven engineering;
- literate programming;
- intentional programming;
- structure editors;
- semantic IDEs;
- software visualization;
- change-impact analysis;
- conceptual/semantic diffs.

These traditions predate agentic programming but may contain important prior art for individual PostCode ideas.

In particular, the **epistemological-status discipline** should eventually be compared not only with contemporary LLM systems but with older work on static-analysis guarantees, provenance, uncertainty visualization and evidence-bearing software tools.

That literature may prove more relevant to this aspect of PostCode than current AI-programming work.

---

# Appendix B — Related-Work Positioning Hypotheses

These are provisional distinctions to test against the literature, not novelty claims.

### Versus conventional software visualization

PostCode is not primarily asking:

> Can a visualization make source easier to understand?

It asks:

> Can multiple trustworthy projections become a viable primary human investigation surface?

It additionally asks whether agent-mediated selection and generation can make task-specific projections cheap enough to alter the historical economics of software visualization.

### Versus AI code review

PostCode is not primarily asking:

> Did the agent's patch contain a defect?

It asks:

> What does the program now look like at the levels relevant to the human supervising it?

### Versus architecture recovery

PostCode does not assume that one recovered architecture is the privileged higher-level representation.

Different questions may require different lenses and projections.

### Versus agent knowledge representations

PostCode does not initially attempt to improve the representation consumed by coding agents.

It investigates the representation presented to humans.

### Versus model-driven development

PostCode does not initially make a higher-level model authoritative or generate implementation from it.

Conventional source remains canonical during the experiment.

### Potential distinctive conjunction

The current working hypothesis is that the less-occupied research territory lies in the combination of:

- sustained software development rather than one-shot comprehension;
- source as a secondary rather than assumed-primary human representation;
- multiple task-dependent lenses and projections;
- automatic selection of lenses and views from human information needs;
- epistemological status and provenance visible at the point of every claim;
- explicit accommodation of incomplete and language-dependent analyses;
- tests treated as projected evidence rather than merely pass/fail gates;
- revision/projection comparison for agent-mediated changes;
- empirical pressure across unrelated projects and eventually languages;
- explicit willingness to discover that source remains superior for some classes of work.

Whether that conjunction is genuinely novel remains an empirical literature question and should continue to be checked as PostCode develops.