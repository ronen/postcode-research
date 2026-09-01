# PostCode: Design

This document describes the current design hypothesis for PostCode: what the system is and how its concepts fit together.

The research questions motivating the design are described in [`research.md`](research.md).

## 1. Design Premise

The research goal is a projection-based software-development environment through which a human can understand, direct, and supervise software using task-appropriate, epistemologically qualified representations rather than routinely working through conventional programming-language source.

The first design decision is a simplification: PostCode's projections and views are read-only. The human continues to direct program changes by instructing coding agents in prose. This simplification defers questions about semantics, authority, ambiguity, round-tripping, and implementation conformance that need not be answered to investigate the core projection model. Later versions of PostCode could support bidirectional views without invalidating the projection model described here.

The core projection pipeline is therefore:

```text
filesystem + Git
       │
       ↓
analysis / adapter layer
       │
       ↓
read-only PostCode workspace
```

## 2. Lenses, Projections, and Views

PostCode distinguishes three related concepts that should not be used interchangeably. They need not become formal software abstractions prematurely; their immediate purpose is to keep the design vocabulary clear.

### 2.1 Lens

A **lens** describes the aspect of the program being investigated: the question being asked of it.

Examples include:

- dependencies;
- callers;
- references;
- construction;
- mutation;
- tests;
- behavior;
- history;
- rationale;
- summary.

A lens answers:

> **What aspect of this subject are we interested in?**

A lens may accept lens-specific parameters that refine the information requested. A summary lens might specify focus, breadth, depth, or an information budget; a callers lens might distinguish direct from transitive callers.

### 2.2 Projection

A **projection** is the information produced by applying a lens to a particular program state and subject.

Conceptually:

```text
projection = lens(repository, revision, subject, parameters)
```

The lens parameter values are part of the projection's identity and must remain distinct from choices about how the projection is presented.

A projection includes both its content and the qualifications needed to understand what that content establishes.

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

### 2.3 View

A **view** is the human-facing presentation of a projection.

A projection might be presented as:

- a graph;
- a table;
- a tree;
- a timeline;
- annotated text;
- a diagram;
- a combination of these.

Presentation can be selected independently of the information requested. Four dependencies might be most useful as a small graph; eighty-seven might be better as a searchable or clustered table. A rationale projection might be best presented as annotated text.

## 3. Epistemological Contract

The requirement is not that every projection be exact or complete.

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

or simply:

> Cannot project this property reliably.

The unacceptable result is presenting partial, historical, asserted, observed, or inferred information in a way that implies a stronger claim than the evidence supports.

For mechanically derived information, a projection might be:

- exact;
- sound but incomplete;
- complete but over-approximate;
- observational;
- unavailable.

Other kinds of information require different qualifications. PostCode need not finalize a formal terminology immediately; plain-English qualification may initially be clearer.

Two things must remain conceptually distinct:

- **Provenance or method:** where the information came from or how it was obtained.
- **Epistemological status or guarantee:** what can safely be concluded from it.

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
  Source structure + Git + tests

Status
  Interpretive explanation.
  Plausible but not mechanically established.
```

### 3.1 Status is part of the view

Epistemological qualification must not exist only in internal metadata or surrounding documentation.

> **The status of a claim must survive into the human-facing view of that claim.**

The eventual interface might represent status through text, badges, typography, icons, expandable evidence, interaction, or some combination of these. The presentation is open to experimentation; the requirement is not.

A weaker claim must not visually masquerade as a stronger one.

The governing principle is:

> **Graceful refusal or explicit qualification is preferable to plausible-looking certainty.**

Trust is critical. If subtle errors cause the user to doubt every projection, the environment loses its value as an alternative working surface.

## 4. Sources of Program Knowledge

Program understanding can draw on several epistemologically different sources. PostCode should not collapse them into a single category of facts.

### 4.1 Derived facts

Derived facts are established through a defined analysis, such as an import relationship or a set of statically identifiable direct callers. The relevant adapter must describe what the analysis does and does not establish.

### 4.2 Recorded assertions

Programs and their histories contain statements made by humans or agents about the program. Possible sources include comments, structured annotations, design documents, commit messages, pull-request descriptions, issue discussions, agent-supplied development context, and other project documentation.

PostCode can establish precisely that an explanation was recorded. It cannot thereby establish that the explanation is true, current, complete, or still the reason the code exists.

```text
Assertion
  Foo is true.

Source
  Annotation in Bar.ts

Historical context
  The annotation first appears in commit 8fa39c2 "Frobnify the glomax..."
  The same commit introduced Bar and modified Baz.

Status
  Recorded assertion with derived historical context.
  The history does not establish that the assertion
  remains true or current.
```

### 4.3 Behavioral and observational evidence

Tests, runtime traces, profiler output, debugger observations, and similar evidence establish something different again.

```text
Tests X and Y reject duplicate media IDs.

Status
  Derived observation about test behavior
```

That is stronger than merely guessing that duplicates are invalid, but weaker than proving that their rejection is a complete intended invariant of the system.

Likewise, a runtime call count is an observation about a particular execution, not necessarily a statement about all executions.

### 4.4 Inferred explanations

Some useful questions inherently require interpretation:

> Why does this exist?

> Why is this functionality split across two modules?

> What happened to `MediaManager`?

> What would be affected if this went away?

An answer may combine current source structure, derived relationships, recorded assertions, commit history, tests, runtime observations, and language-model interpretation.

Such an answer may be extremely useful while still being an interpretation rather than an established program fact. Its evidence, confidence, and limitations should remain visible.

## 5. Investigation and Representation Selection

The human can choose a subject, lens, lens parameter values, view, or any combination of them. PostCode can choose whichever elements the human leaves unspecified, based on the expressed information need and the projections available.

Selection can therefore be explicit, automatic, or mixed. For example:

> What depends on this?

leaves PostCode to choose an appropriate lens and view.

> Show callers of this.

effectively selects the lens while leaving the presentation open.

> Show this as a tree.

selects a view for information established by the surrounding context.

> Show the transitive callers of this as a tree.

selects a lens, a lens parameter value, and a view.

The prose interface supports questions at several levels:

> Show me everything related to synchronization.

> What calls this?

> Why does this exist?

> What happened to `MediaManager`?

> What behavior do these tests appear to protect?

For whatever the human leaves unspecified, the prose interface can act as a query planner:

```text
human information need
and explicit choices
        │
        ↓
prose interpretation
        │
        ↓
subject / lens / parameter selection
        │
        ↓
qualified projection
        │
        ↓
view selection
```

“What calls this?” may map almost directly to a callers lens backed by static analysis. “Why does this exist?” may select evidence, history, and rationale lenses and synthesize several projections. “What behavior do these tests appear to protect?” may combine mechanically established test structure with recorded descriptions and explicitly marked interpretation.

PostCode may therefore reduce two different kinds of effort:

1. determining what information about the program would answer the question;
2. determining how that information should be presented.

The important rule is:

> **Interpretation may guide investigation and may itself be useful output, but it must not masquerade as mechanically established program truth.**

Text is a first-class kind of view. A projection need not be graphical or mechanically derived, provided the provenance and epistemological status of its claims remain visible.

## 6. Summary and Recursive Investigation

One particularly important lens is also one of the simplest and most familiar:

> **Summarize this.**

Conceptually:

```text
summarize(subject)
```

The subject might be a repository, package, subsystem, module, type, function, test, collection of entities, or change between revisions.

Unlike a conventional prose summary generated directly from source, a PostCode summary can be assembled from other qualified projections:

```text
summarize(MediaManager)
        │
        ├── structure(MediaManager)
        ├── dependencies(MediaManager)
        ├── callers(MediaManager)
        ├── tests(MediaManager)
        ├── history(MediaManager)
        │
        ↓
qualified summary
```

Summary is therefore potentially a composite lens. Its output may contain derived facts, recorded assertions, observations, and interpretations. It must preserve those distinctions rather than flattening everything into equally authoritative prose.

This makes summary a useful stress test of PostCode's epistemological contract: it deliberately compresses several kinds of program knowledge while still preserving the strength and provenance of consequential claims.

### 6.1 `summarize(root)`

When PostCode first opens an unfamiliar repository, the natural initial projection may be:

```text
summarize(root)
```

Its purpose is not to produce a definitive architecture document. It is to provide enough orientation for the human to decide where to look next.

A root summary might identify, where supportable:

- major packages and modules;
- executable applications or libraries;
- major dependency boundaries;
- entry points and exported APIs;
- tests and their distribution;
- build and package structure;
- major externally recorded descriptions;
- candidate architectural groupings, explicitly marked as interpretation.

The summary is therefore not merely an endpoint. It is a navigation surface.

A typical investigation might proceed:

```text
summarize(root)
        ↓
summarize(publishing)
        ↓
structure(publishing)
        ↓
summarize(MediaManager)
        ↓
tests(MediaManager)
        ↓
callers(reconcile)
```

This gives PostCode a simple recursive interaction model:

> **Summarize where I am; then let me follow whatever becomes interesting.**

## 7. Subjects, Identity, and Workspace

PostCode does not initially require persistent semantic identities or a formal architecture model.

Entities can be discovered from the implementation according to explicit adapter rules. Possible entities include repositories, packages, modules, files, namespaces, types, functions, methods, exported symbols, tests, and fields or variables where useful. The available entities may vary by language.

### 7.1 Persistence of human attention

PostCode can persist workspace state without claiming that program identities survive arbitrary transformations.

For example:

```text
MediaManager / dependencies
SyncReconciler / callers
sync tests
```

This records what the human was paying attention to.

If `MediaManager` later disappears, PostCode need not infer that another entity is its conceptual successor. It can show that the entity no longer exists, identify the revisions in which it was last present and removed, and allow the user to ask what happened. Git history and interpretation can then address the question without pretending to have established persistent semantic identity.

### 7.2 Workspace model

A workspace contains an arbitrary number of independent views over projections.

```text
projection = lens(repository, revision, subject, parameters)
view       = present(projection, context)
```

Presentation context might eventually include the current investigation, the number and shape of results, available screen space, neighbouring views, user preferences, and previous interaction.

A revision may be the current working tree, a branch, or a commit. Staged or index state may also be useful.

Views may be:

- **live:** the underlying projection follows a working tree or branch;
- **pinned:** the projection remains attached to a particular revision.

The user constructs the working surface appropriate to the current problem rather than operating within a predetermined dashboard.

### 7.3 Structural navigation

Hierarchy may be useful as a structural lens rather than as the universal representation of the program.

Containment or decomposition may be hierarchical; dependencies, behavior, data flow, calls, and other relationships generally are not. PostCode should not assume that there is one uniquely correct conceptual hierarchy.

Initially, structural projections should be based only on relationships the relevant adapter can define accurately.

## 8. Candidate Lens Families

The initial vocabulary should avoid claims such as “important component” or “architectural responsibility” that inherently require judgment unless those claims are explicitly presented as interpretation.

These are candidate lenses, not a proposed universal ontology.

### 8.1 Summary lenses

Summary is a composite, qualified orientation to a subject and a way to expose useful directions for further investigation. It should be recursive across entity levels, with `summarize(root)` as the candidate entry point for an unfamiliar repository.

### 8.2 System and repository lenses

Examples include:

- module and package hierarchy;
- imports and dependencies;
- exported API;
- test inventory;
- type relationships;
- package and module references.

### 8.3 Entity cross-reference lenses

For an identified entity, possible lenses include:

- definition;
- callers and callees;
- references;
- construction and allocation sites;
- reads and writes;
- values passed to and from it;
- implementations;
- inheritance, interface, or trait relationships;
- ownership or lifetime information where meaningful.

The available facts and guarantees are language-dependent. PostCode should not manufacture symmetry where language semantics differ.

### 8.4 Test lenses

Tests occupy a semi-formal boundary between intended program behavior and source-language implementation. A test may be considered at several distinct levels:

- **test intent:** the behavior or property the test appears intended to protect;
- **test realization:** the setup, fixtures, mocks, calls, and assertions used to exercise it;
- **evidence:** what passing or failing the test establishes;
- **language- or runtime-specific mechanism:** concepts necessary to express or execute it.

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

PostCode should project a test at the highest useful abstraction level that preserves what it actually establishes. It should not require every test to have a language-independent behavioral description.

Potential test lenses include inventory, association with entities, setup/action/assertion structure, behavior or property summaries, dependencies, affected tests, and history across revisions.

### 8.5 Path lenses

Possible path lenses include call paths, dependency paths, data-propagation paths, and possible control-flow paths. These may frequently produce qualified rather than exact projections.

### 8.6 Temporal and revision lenses

Examples include:

- where and when an entity appeared or disappeared;
- callers and dependencies across revisions;
- tests added or removed;
- changes in what a test exercises or asserts;
- the same projection across branches.

### 8.7 Rationale and evidence lenses

Possible lenses include recorded rationale, relevant annotations, history explaining a design choice, tests that appear to encode requirements, evidence supporting or contradicting old rationale, and synthesized explanations with explicit epistemological status.

Whether these become stable lens families should emerge from use rather than being assumed.

## 9. Source as a Secondary View

Source should not be PostCode's default or primary representation. Completely excluding it, however, would hide the cases in which projections are insufficient and add artificial friction to investigation.

PostCode may therefore provide an explicit **Show Source** escape hatch.

Source can be understood as a special view whose underlying information is the conventional implementation itself rather than a deliberately reduced PostCode projection.

Opening source is a legitimate action, not a failure. It allows the human to obtain implementation detail, verify a projection, or continue an investigation for which PostCode cannot yet provide an adequate representation.

## 10. Revision and Projection Comparison

During agent-mediated development, one of the most important questions is:

> **What did the agent just change?**

Git source diffs answer that at the implementation-text level. A projection comparison can instead ask:

> **What changed at the level at which I was thinking about the program?**

Examples include changed dependencies, callers, construction sites, test relationships, behavior, call paths, or recorded rationale.

The smallest design is to apply the same lens to the same subject at two revisions and compare the resulting projections:

```text
before = lens(repository, revisionA, subject, parameters)
after  = lens(repository, revisionB, subject, parameters)

compare(before, after)
```

The two projections may initially be placed side by side. More specialized comparison views can emerge if use demands them.

Projection stability is particularly important here: changes in the projection mechanism must not masquerade as changes in the program.

## 11. Agent Integration

Separating PostCode from the coding agent creates an important interaction question.

The human may understand a desired change through a PostCode view, but the agent ordinarily sees the repository and the human's prose—not necessarily the projection, its qualifications, or the investigation that produced it. If the human must repeatedly translate a projected concept back into filenames, symbols, and implementation details, much of the value of working at the projection level may be lost.

The human and agent should be able to discuss the software using projections as shared referents. For example:

> Separate the synchronization policy shown in this projection from catalog-state management.

or:

> Preserve the behavior represented here, but remove this dependency path.

### 11.1 Shared machine-readable context

The initial mechanism can be a machine-readable context artifact that PostCode keeps synchronized with the current workspace. Agent instructions such as `AGENTS.md` or `CLAUDE.md` can direct coding agents to read that artifact when interpreting the human's prompts.

The purpose is not merely to give the agent another description of the repository. It is to let the human refer directly to PostCode context in a prompt: the focused view, a projected relationship, a qualified summary, or the current investigation. The agent can then resolve that reference without requiring the human to translate the projection back into filenames, symbols, and implementation details.

The artifact should describe at least:

- the repository and revision or working-tree state against which it was generated;
- the open views and their stable identifiers;
- which view or subject currently has the human's focus;
- the lens, subject, and projection underlying each view;
- the projection's content, provenance, epistemological status, and limitations;
- source entities or locations that allow an agent to reconnect projected concepts to the implementation;
- relationships among views where they form part of the same investigation.

Conceptually:

```text
PostCode workspace
        │
        ↓ continuously updates
machine-readable context artifact
        │
        ↓ read according to project agent instructions
external coding agent
```

The context artifact should be generated state rather than a canonical program representation. It should not normally be committed, and updating it should not dirty the repository or trigger PostCode to analyze its own output. It should be written atomically and carry enough revision information for an agent to recognize when the context no longer describes the current program state.

A compact manifest may be preferable to duplicating every projection into one indefinitely growing file. The manifest can describe the current workspace and point to separate machine-readable projection records when necessary. The exact representation can emerge with the implementation, but it should be documented and stable enough that different coding agents can consume it without bespoke integration.

This allows prompts such as “remove the dependency shown in the focused view” or “preserve the behavior represented here” to carry useful shared context.

### 11.2 Agent-supplied context

Communication can also flow from the coding agent back into PostCode.

Project instructions can ask the agent to leave a structured response artifact or invoke a command to record context relating to its work. That context might include:

- which projected concept the agent understood the request to concern;
- how the implementation corresponds to that concept;
- rationale for a change;
- constraints, uncertainty, or missing information encountered;
- tests or other verification performed;
- source entities affected;
- projections that should be refreshed or shown;
- questions that another lens might help answer.

Agent-supplied context must retain its provenance and epistemological status. An agent's account of its rationale, behavior, or interpretation is a recorded assertion or interpretation, not a derived fact merely because it was written in a structured form.

The response artifact should be associated with the relevant repository state and, where possible, the task or conversation that produced it. PostCode can then present this development context alongside derived structure, history, tests, and other evidence without collapsing their distinctions.

### 11.3 Bidirectional interaction

The file-based exchange can later develop into a more interactive protocol. An external agent might:

- query PostCode lenses directly;
- refer to projections and views by stable identifier;
- request a new projection or refresh;
- contribute rationale or uncertainty during development rather than only after a task;
- suggest useful additions to the current investigation.

PostCode might in turn generate prompt-ready references, expose structured queries, or eventually contain the agent conversation itself. These mechanisms can build on the same shared context model rather than replacing it.

## 12. Language Adapters

A language adapter supplies the entity discovery, analyses, and guarantees available for a particular language.

The first adapter should not be prematurely generalized into a universal programming ontology.

The rule is:

> **Accrete shared abstractions upward from multiple languages; never discard language-specific semantics merely to fit a shared model.**

Tests are a particularly useful stress case. A behavioral test may project naturally into a shared concept such as “duplicate identifiers are rejected,” while another test may fundamentally concern a language's type system, ownership rules, macro behavior, linking semantics, runtime scheduling, or memory management.

Shared concepts and language-specific extensions can coexist. The adapter model should allow experience across languages to reveal their boundary rather than deciding that boundary in advance.

## 13. Runtime Observations

Runtime information fits naturally into the projection model without requiring PostCode itself to become a debugger, profiler, test runner, or execution environment.

External systems can produce observations through runtime adapters:

```text
debugger / profiler / tracer / test runner
                 │
                 ↓
            runtime adapter
                 │
                 ↓
              PostCode
```

Such observations might concern calls, time, allocation, coverage, values, stack frames, or debugger state.

Runtime observations have a natural epistemological qualification:

> Observed during run X.

They must not silently become claims about all possible executions.
