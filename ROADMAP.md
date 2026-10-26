# PostCode: Roadmap

This document describes the current development plan for PostCode and records plausible later directions without treating them as commitments.

It identifies which research-enabling capabilities and contexts may be pursued and why; it does not define detailed application behavior.

The research questions are described in [`research.md`](research.md), the conceptual product design in [`product-design.md`](product-design.md), and the process by which development produces research evidence in [`methodology.md`](methodology.md).

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

### 2.1 Initial implementation and bootstrap transition

The immediate milestone is a bounded, trustworthy, read-only architectural investigation experience that can be used during real development and compared with capable agent chat. It builds on the bootstrap implementation of the projection model and enables evaluation through sustained formative use. Implementation increments should serve that experience rather than define the research ambition.

It should support:

- analysis of the PostCode repository in one programming language;
- a small initial set of mechanically derived lenses;
- one or more basic interpretive lenses whose claims remain explicitly qualified;
- a usable set of views through which the developer can conduct a genuine investigation;
- views that preserve provenance, epistemological status, guarantees, and limitations;
- a practical way to request and inspect those views;
- enough navigation, qualification and supporting information to sustain an investigation without displaying programming-language source;
- enough formative observation support to record use, inadequate explanations or views, friction, and immediate reactions.

Including both mechanically derived and interpretive information from the beginning puts the epistemological contract under pressure: PostCode must keep interpretation distinguishable from precise analysis while making both useful during investigation.

PostCode should be used on its own development as soon as any implemented capability can contribute usefully. That use will broaden as further subjects, lenses, views, and observation support become available.

There is no objective boundary between the bootstrap transition and ongoing formative development. At some point, experience may support the judgment that PostCode has a coherent minimal set of capabilities for sustained formative use. That judgment marks the end of the bootstrap transition; PostCode-on-PostCode use will already have begun and will continue afterward.

### 2.2 Bounded architectural representation exploration

Develop and evaluate a bounded PostCode investigation using shared architectural representations, including visual structural or behavioral presentations where useful. Choose the codebase, architectural question, and relevant notations when planning the investigation. Examine whether partial, qualified retained accounts support reasoning across perspectives and whether revisiting a subject reveals gaps, consequences, or corrections.

Compare with capable coding-agent chat that can already generate diagrams and maintain notes. Use the findings to refine PostCode's presentations and investigation capabilities. This does not require a universal architecture model or a visual editor.

## 3. Candidate Capability Directions

The first formative loop should determine which capabilities become useful next. The following are candidates rather than a fixed sequence.

### 3.1 Following repository changes

Support continued investigation as coding agents change a repository, without allowing information based on an earlier state to appear current. This becomes important when manually reconstructing an investigation after each change disrupts sustained use or obscures what the human is supervising.

### 3.2 Prose investigation and selection

Allow prose information needs to produce useful qualified views without requiring the human to know PostCode's full lens and presentation vocabulary. This becomes important when explicit selection makes investigation awkward or forces the human to translate conceptual questions into PostCode mechanics.

### 3.3 Shared coding-agent context

Provide the shared machine-readable context described in [`product-design.md`](product-design.md#shared-machine-readable-context), allowing instructions to coding agents to refer directly to focused views, projected relationships, and the current investigation. Agent-supplied context can later complete the exchange.

Its timing should depend on when repeatedly translating PostCode concepts back into source-level terms becomes a material obstacle to formative use.

### 3.4 Revision and projection comparison

Support comparison of qualified information across repository states so the human can investigate what changed at a conceptual level rather than relying solely on an agent's description of the patch. Begin with the smallest comparison capability that can produce formative evidence; add conceptual-diff analysis when simpler comparison proves useful but inadequate.

Stable projection behavior is a prerequisite: changes in PostCode must not masquerade as changes in the program.

### 3.5 Capability growth

Add or revise capabilities in response to recurring architectural investigative needs, drawing provisionally on established architecture/design concepts and visual languages where useful. A failed investigation does not by itself imply that a new lens is required; the problem may instead concern available information, representation, selection, interaction, evidence, or the underlying projection approach.

Illustrative lens families are described in [`product-design.md`](product-design.md#illustrative-lens-families). The capabilities pursued next should be shaped by use rather than by treating those examples as a backlog.

### 3.6 Usability and sustained interaction

Address interaction friction when it interferes with sustained formative use or obscures what is being learned about projections. Visual polish by itself is not a roadmap milestone.

### 3.7 Assessing related systems

A bounded assessment of systems identified in [`related-work.md`](related-work.md#28-implications-of-recent-prior-art) could clarify opportunities for reuse and meaningful interaction comparisons. Archbird is a candidate for assessing analysis reuse and its existing interface; Whiteboard and Glamorous Toolkit are also candidates for interaction comparison.

Select a small set of representative questions or development tasks and identify the versions, implemented capabilities, actual guarantees, and unresolved limitations. For reuse, assess fit with PostCode's captured evidence, qualification, language semantics, and observation requirements, together with integration effort. For comparison, assess whether the interface supports the human tasks relevant to the research question. Follow the [methodological distinctions](methodology.md#84-comparisons-and-reuse-assessments) when interpreting the results.

The assessment could support reuse, a later comparison study, a more precise research claim, or retaining the current approach. It is candidate work, not a commitment to adopt another system or replace existing implementation, and should be selected when its likely value justifies the effort and any delay to formative use.

## 4. Expanding Formative Contexts

PostCode should eventually be exercised across the different contexts described in [`methodology.md`](methodology.md#2-formative-use). These contexts are sources of different pressure, not consecutive milestones that must all be completed.

### 4.1 Inspection-only use

Use PostCode to pursue genuine questions about accessible codebases without intending to modify them. These investigations may involve familiar or unfamiliar software and can begin as soon as the implemented lenses and views are useful for them.

Inspection-only use provides a low-cost way to exercise orientation, explanation, navigation, epistemological qualification, and trust across varied software. It can expose missing lenses and projection failures, but does not provide evidence about directing changes or supervising implementation outcomes.

### 4.2 Continued Development of an Existing Project

Apply PostCode in the [existing-project development context](methodology.md#existing-project-development) when the bootstrap is useful enough to remain present during real work. This will exercise PostCode during the creation of new behavior and structural change, not only retrospective investigation.

### 4.3 Ab initio project

Begin a separate new project with PostCode present from its inception. Unlike PostCode-on-PostCode, the tool and its subject are distinct; unlike existing-project development, the project begins without a pre-existing implementation or development history.

This context tests whether intentions, rationale, requirements, and conceptual structure can be captured as they arise; whether PostCode's existing projection capabilities are useful for guiding a new project's early development; and how PostCode-mediated supervision affects the software being produced.

### 4.4 Unfamiliar software in an existing language

Apply PostCode to unfamiliar open-source repositories in a language PostCode already supports. This tests whether PostCode can provide enough orientation and understanding for a user to pursue a useful investigation or development task without a pre-existing mental model. Keeping the programming language fixed helps separate variation across codebases, domains, and architectures from variation across languages.

Additional repositories are useful only while they expose new assumptions, needs, or failure modes.

### 4.5 Additional languages

Try PostCode on software written in another programming language. Check which architectural concepts and investigation capabilities remain useful, what needs adaptation, and where language-specific differences matter.

The exploratory note on [cross-paradigm stress tests](notes/cross-paradigm-architectural-concepts.md) considers how a bounded conceptual exercise could challenge architectural assumptions before implementing another language adapter. It does not change current priorities or commit to a language integration.

### 4.6 Unfamiliar-language challenge

A later experiment may use a language the developer does not know well. Where practical, coding agents can integrate the new language into PostCode from PostCode-level requirements while reporting where the existing abstractions fail to transfer.

The developer's unfamiliarity with the implementation language places greater demands on the accuracy, provenance, and limitations of PostCode's architectural representations. An apparently convincing account must not conceal what has not been established.

The experiment can ask:

> **Can the developer understand and evaluate a program through PostCode without proficiency in its implementation language?**

Difficulty integrating a language through an existing abstraction is evidence about the abstraction, not merely an implementation inconvenience.

### 4.7 Cross-language consolidation

After multiple languages and real tasks have exerted pressure on the design, compare the language integrations, lenses actually used, guarantees, unavailable projections, language-specific concepts, test projections, and reports of inadequate representations.

## 5. Public Availability, External Use, and Evaluation

Opening PostCode to others involves several separable choices:

- making the repository publicly visible;
- presenting PostCode publicly as a project;
- inviting others to try it;
- making the project ready to accept contributions;
- actively soliciting and supporting contributors.

The research and application repositories are publicly visible. The remaining choices need not occur together or in a fixed order. Each becomes useful when its expected gains justify the corresponding documentation, stability, communication, and coordination work.

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
- specialized comparison interaction;
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
