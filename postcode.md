# PostCode: Program Projection Environment
## Research Direction and Initial Development Plan

**PostCode** is the current working project name.

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

## 21. Research Practice: Speculative Papers

An occasional useful research exercise is to write the paper **before the research is complete**, explicitly as speculative fiction.

Rather than writing only the hoped-for paper, imagine incompatible outcomes. See [`research.md` — “What Might We Learn?”](research.md#possible-findings) for examples of possible findings the project might produce.

For each speculative result, ask:

> **What observations would make this paper impossible to write?**

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

Among the initial lenses, strongly consider including:

```text
summarize(subject)
```

alongside a small number of mechanically defined lenses.

This deliberately puts the epistemological contract under pressure early: PostCode must combine precise analysis with useful interpretation rather than postponing the difficult case until after a purely mechanical browser has been built.

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

Observe:

- which entities and lenses transfer;
- which assumptions were artifacts of the first language;
- which new language-specific concepts appear;
- whether guarantees change;
- whether the existing entity model breaks;
- whether shared terminology conceals importantly different semantics;
- how test projections transfer or fail to transfer.

Repeat with another repository in the second language if doing so still teaches something.

### Phase 9 — Third language / unfamiliar-language challenge

Preferably choose a language the developer does not know.

Where practical, have coding agents implement the adapter without language-specific guidance from the developer.

The developer supplies PostCode-level requirements:

- the kinds of entities PostCode currently understands;
- questions existing lenses answer;
- epistemological requirements;
- adapter interfaces that have emerged from previous implementations;
- the requirement not to discard language-specific information merely to fit existing abstractions.

The agent supplies the language-specific realization:

- learns the relevant semantics;
- finds parser/compiler/indexer/LSP/static-analysis tooling;
- determines which projections can be supported;
- determines what guarantees can be made;
- identifies where existing semantics do not transfer;
- proposes language-specific concepts where necessary.

The experiment should begin with:

```text
summarize(root)
```

This provides a particularly clean question:

> **Can I begin forming a useful mental model of a program through PostCode when I do not know its implementation language well enough to comfortably reconstruct that model from source?**

Investigation can then proceed recursively from the summary into whatever subjects and lenses appear useful.

If the developer must first learn substantial source-language semantics before `summarize(root)` becomes trustworthy or useful, that is important negative evidence.

If an agent reports:

> The existing `callers` lens cannot provide the same semantics in this language because X; I can instead provide A, B and C with these guarantees.

that is not merely an adapter inconvenience.

It is evidence about the abstraction itself.

> **An adapter fighting the abstraction is exactly the pressure this phase is intended to discover.**

The unfamiliar-language case also strengthens the epistemological experiment: the developer cannot rely as readily on source-language expertise to notice that a plausible-looking projection is wrong.

PostCode must increasingly earn trust through analysis, provenance and explicit guarantees.

### Phase 10 — Cross-language refactoring

Only now ask which concepts genuinely survived contact with multiple languages and tasks.

Compare:

- adapter implementations;
- lenses actually used;
- projections repeatedly wanted;
- unavailable projections;
- guarantees;
- language-specific concepts;
- test projections;
- source excursions;
- successful and failed reuse of abstractions.

Ask:

> **Which concepts genuinely survived contact with multiple languages and multiple real programming tasks?**

A federation of shared concepts plus language-specific extensions may be preferable to a universal ontology.

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

Choose:

- one language;
- one repository;
- a few precisely defined entity types;
- 2–4 projections/lenses with explicit semantics.

A minimal workspace might look approximately like:

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
│ repository / summary       │
│                            │
│ [qualified summary]        │
│                            │
│ Lens: summary              │
│ Status: mixed              │
│ Evidence: expand…          │
└────────────────────────────┘

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

**Văduva, et al. (2026). _Code2UML: Agentic LLMs with Context Engineering for Scalable Software Visualization._ arXiv:2605.24453.**

Generates multiple UML views from repositories across Java, JavaScript, PHP and Python using deterministic IR processing plus specialized agents.

Especially interesting for PostCode because it demonstrates multi-language projection generation while reporting high relationship precision but deliberately limited entity recall.

This provides a concrete nearby example of useful projections whose incompleteness matters.

**CodeSkyline (VISSOFT 2026). _A Code-Map Visualization with Juxtaposed Views for Program Comprehension and Navigation._**

Provides multiple simultaneous code-map views and abstraction levels, with a four-week adoption study in which some participants continued using the system occasionally.

Relevant precedent for multi-view and sustained-use software visualization, while remaining primarily within the conventional program-comprehension/navigation framing.

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

### Versus conventional LLM code summarization

PostCode overlaps superficially with an already common AI interaction:

> Summarize this code.

The distinction is not that PostCode can produce prose summaries while existing LLMs cannot.

Instead, PostCode asks whether program summarization can become part of a **qualified, navigable projection system**.

A PostCode summary may:

- compose mechanically defined lenses;
- incorporate recorded assertions and behavioral evidence;
- expose provenance;
- distinguish derived facts from interpretation;
- state limitations and unavailable information;
- link directly into deeper projections;
- remain associated with a particular repository revision;
- be compared across revisions.

Thus `summarize(root)` is not intended merely as a better prompt for an LLM.

It is a candidate entry point into a structured investigation of the program.

This may also provide a useful bridge between familiar contemporary AI use and PostCode's broader research question:

> **Can the adaptive representation pattern people increasingly use for documents and other information become trustworthy enough to serve as a routine human interface to software?**

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
