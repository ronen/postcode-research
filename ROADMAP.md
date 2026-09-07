# PostCode: Roadmap

This document describes the current development plan for PostCode and records plausible later directions without treating them as commitments.

The research questions are described in [`research.md`](research.md), the current design in [`product-design.md`](product-design.md), and the process by which development produces research evidence in [`methodology.md`](methodology.md).

## 1. Roadmap Stance

The roadmap distinguishes:

- **planned work:** work that the project has explicitly committed to doing next;
- **candidate directions:** plausible next experiments or capabilities, selected when evidence makes them useful;
- **deferred directions:** ideas that fit the design but are not needed to investigate the core projection model;
- **non-requirements:** outcomes PostCode does not need to achieve in order for the research to succeed.

This is a living roadmap. As evidence and explicit decisions turn candidate directions into commitments, they can be added or moved into Planned Work; planned work can likewise be revised when subsequent evidence warrants it. Completed work can be removed from the roadmap or reduced to a brief checklist when retaining it helps explain later dependencies or decisions.

Candidate capability directions and formative contexts may be reordered, combined, revisited, skipped, or abandoned as evidence develops. The roadmap records them so that useful possibilities are not forgotten, not to prescribe the project before experience exists.

After each meaningful use, apply the methodological loop before extending the roadmap. Ask:

- What limitation, friction, success, or surprise was observed?
- Is the resulting finding supported by the available evidence?
- Does it call for a design revision, a new capability, another development context, or a change to the research question?
- What small or inexpensive next step could distinguish among plausible interpretations, remove disproportionate friction, or unlock useful formative work?

The next step should be selected for what it can clarify or make possible.

At suitable checkpoints, also consider whether [Publication-Aware Prioritization](research-strategy.md#33-publication-aware-prioritization) should affect what comes next.

## 2. Planned Work

### 2.1 Complete and publish the project foundation

Before substantial implementation begins:

- finish decomposing the original PostCode document;
- compare the resulting documents with the original for omissions;
- resolve any resulting inconsistencies or missing material;
- define and document the initial operational workflow for developing PostCode;
- add a README describing the project's status and document structure;
- choose a license;
- audit the repository and its history for material that should not become public;
- create and push a public GitHub repository.

This establishes public repository visibility. It is not yet a public launch, an invitation to use PostCode, or a solicitation of contributions.

### 2.2 Initial implementation and bootstrap transition

The immediate milestone is the smallest trustworthy read-only version of PostCode that can be used during development of PostCode itself. Its purpose is to make the projection model concrete enough to evaluate and to create the conditions for sustained formative use.

It should support:

- analysis of the PostCode repository in one programming language;
- `summarize(subject, lens_parameters)` and a few mechanically derived lenses;
- simple views that preserve provenance, epistemological status, guarantees, and limitations;
- navigation among subjects, relationships, and views;
- convenient access to source;
- enough formative observation support to record use, friction, and immediate reactions.

Including summary from the beginning puts the epistemological contract under pressure: PostCode must combine useful interpretation with precise analysis while keeping their status distinguishable.

PostCode should be used on its own development as soon as any implemented capability can contribute usefully. That use will broaden as further subjects, lenses, views, and observation support become available.

There is no objective boundary between the bootstrap transition and ongoing formative development. At some point, experience may support the judgment that PostCode has a coherent minimal set of capabilities for sustained formative use. That judgment marks the end of the bootstrap transition; PostCode-on-PostCode use will already have begun and will continue afterward.

## 3. Candidate Capability Directions

The first formative loop should determine which capabilities become useful next. The following are candidates rather than a fixed sequence.

### 3.1 Live repository updates

Observe changes made by external coding agents and keep affected projections and views current. This becomes important when manual refresh disrupts sustained use or leaves the workspace visibly stale.

### 3.2 Prose investigation and selection

Allow prose requests to identify subjects, select or parameterize lenses, choose or parameterize presentations, create useful views, and request qualified explanations. This becomes important when explicit controls make investigation awkward or require the user to know the lens and presentation vocabulary prematurely.

### 3.3 Shared coding-agent context

Generate the machine-readable context described in [`product-design.md`](product-design.md#371-shared-machine-readable-context), allowing prompts to refer directly to focused views, projected relationships, and the current investigation. Agent-supplied context can later complete the exchange.

Its timing should depend on when repeatedly translating PostCode concepts back into source-level terms becomes a material obstacle to formative use.

### 3.4 Revision and projection comparison

Allow the same lens and subject to be projected at two repository states and initially place the results side by side:

```text
before = lens(repository, revisionA, subject, lens_parameters)
after  = lens(repository, revisionB, subject, lens_parameters)

compare(before, after)
```

Stable projection behavior is a prerequisite: changes in the projection mechanism must not masquerade as changes in the program.

Specialized diff presentations—such as highlighted additions and removals, overlays, movement, animation, or conceptual change summaries—should be added only if simpler comparison proves useful but inadequate.

### 3.5 Lens and presentation growth

Add or revise lenses and presentations in response to recurring needs. A failed investigation does not by itself imply that a new lens is required; the problem may instead lie in projection content, lens parameters, presentation behavior, presentation parameters, selection, available evidence, or the underlying projection approach.

Candidate lenses are recorded in [`product-design.md`](product-design.md#41-candidate-lenses). Their eventual set, behavior, and grouping should be shaped by use.

### 3.6 Workspace usability and chrome

Refine shared workspace controls, layout, navigation, feedback, and presentation affordances when interface friction interferes with sustained use or obscures what is being learned about projections. Visual polish by itself is not a roadmap milestone.

## 4. Expanding Formative Contexts

PostCode should eventually be exercised across the different contexts described in [`methodology.md`](methodology.md#2-formative-use). These contexts are sources of different pressure, not consecutive milestones that must all be completed.

### 4.1 Continued Development of an Existing Project

Apply PostCode in the [existing-project development context](methodology.md#existing-project-development) when the bootstrap is useful enough to remain present during real work. This will exercise PostCode during the creation of new behavior and structural change, not only retrospective investigation.

### 4.2 Ab initio project

Begin a separate new project with PostCode present from its inception. Unlike PostCode-on-PostCode, the tool and its subject are distinct; unlike existing-project development, the project begins without a pre-existing implementation or development history.

This context tests whether intentions, rationale, requirements, and conceptual structure can be captured as they arise; whether PostCode's existing projection capabilities are useful for guiding a new project's early development; and how PostCode-mediated supervision affects the software being produced.

### 4.3 Unfamiliar software in an existing language

Apply PostCode to unfamiliar open-source repositories in a language PostCode already supports. This tests whether PostCode can provide enough orientation and understanding for a user to pursue a useful investigation or development task without a pre-existing mental model. Keeping the programming language fixed helps separate variation across codebases, domains, and architectures from variation across languages.

Additional repositories are useful only while they expose new assumptions, needs, or failure modes.

### 4.4 Additional languages

Apply PostCode to software in another programming language when cross-language pressure can test concepts that have emerged through actual use. PostCode should preserve the language's semantics rather than force them into abstractions inherited from the first language.

Observe which entities, lenses, lens parameter values, guarantees, and test concepts transfer; which require language-specific treatment; and where shared terminology conceals different semantics.

### 4.5 Unfamiliar-language challenge

A later experiment may use a language the developer does not know well. Where practical, coding agents can integrate the new language into PostCode from PostCode-level requirements while reporting where the existing abstractions fail to transfer.

The developer's unfamiliarity with the language also strengthens the trust experiment: source-language expertise is less available to expose a plausible-looking but incorrect projection. PostCode must instead earn trust through analysis, provenance, and explicit guarantees.

The experiment can ask:

> **Can the developer form a useful understanding of a program through PostCode without first learning enough of its implementation language to reconstruct that understanding from source?**

Difficulty integrating a language through an existing abstraction is evidence about the abstraction, not merely an implementation inconvenience.

### 4.6 Cross-language consolidation

After multiple languages and real tasks have exerted pressure on the design, compare the language integrations, lenses actually used, guarantees, unavailable projections, language-specific concepts, test projections, and source excursions.

Shared abstractions should be consolidated only where the evidence supports them. A federation of common concepts and language-specific extensions may be preferable to a universal ontology.

## 5. Public Availability, External Use, and Evaluation

Opening PostCode to others involves several separable choices:

- making the repository publicly visible;
- presenting PostCode publicly as a project;
- inviting others to try it;
- making the project ready to accept contributions;
- actively soliciting and supporting contributors.

The first choice is part of [Planned Work](#21-complete-and-publish-the-project-foundation). The others need not occur together or in a fixed order. Each becomes useful when its expected gains justify the corresponding documentation, stability, communication, and coordination work.

External exploratory use becomes useful once PostCode supports a sufficiently coherent and reliable workflow for other developers to try it during their own development work. It can expose assumptions created by the author's knowledge, vocabulary, workflow, and tolerance for friction.

Formal user studies become useful when a specific research question and the relevant tasks, methods, and outcomes are sufficiently mature.

The evidence and claims appropriate to these forms of evaluation are described in [`methodology.md`](methodology.md#8-evidence-and-claim-scope).

## 6. Deferred Directions

The following fit the design but are not required for the immediate investigation:

- direct editing or manipulation of projected representations;
- bidirectional projection and round-tripping;
- authoring or specifying tests directly through PostCode views;
- an integrated coding-agent conversation;
- runtime adapters for debuggers, profilers, tracers, or test runners;
- debugger or execution control;
- polished or specialized projection-diff presentations;
- educational tooling.

Runtime observations can be introduced if static repository evidence proves insufficient for important questions. Existing runtime systems should supply the observations; PostCode need not become the debugger, profiler, tracer, test runner, or execution environment.

Deferred directions are not rejected. They become candidates when formative use shows that they would answer a consequential question or remove a material obstacle.

## 7. Non-Requirements

PostCode does not need to produce:

- a universal intermediate representation or cross-language ontology;
- a new programming language;
- a formal architecture model;
- persistent semantic identity for program entities or relationships;
- authoritative architectural judgment;
- an optimal representation for coding agents;
- proof that all software concepts can be expressed independently of programming language;
- proof that source should cease to be the canonical persistent representation;
- proof that coding agents should cease working with conventional source.

These remain possible adjacent questions or outcomes, but the roadmap does not depend on resolving them.
