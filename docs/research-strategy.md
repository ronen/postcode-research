# PostCode: Research Strategy

This document describes how PostCode's broader research direction will respond to what the project learns.

The research questions are described in [`research.md`](research.md), the current design in [`design.md`](design.md), the process by which development produces evidence in [`methodology.md`](methodology.md), and candidate development directions in [`roadmap.md`](roadmap.md).

Research strategy is distinct from both methodology and roadmap. Methodology governs how observations become findings and claims. The roadmap records implementation and formative-use possibilities. Research strategy asks which possible contributions deserve further investigation, when they may be ready to communicate, and what additional people or work could strengthen them.

## 1. Strategy Stance

PostCode may produce several kinds of value:

- a tool or interaction model useful in software development;
- design knowledge about projection-based development environments;
- empirical findings about how people understand and supervise agent-produced software;
- concepts or mechanisms that transfer beyond PostCode;
- negative results that narrow the plausible role of projections.

These outcomes should not be collapsed into a single measure of success. Practical usefulness does not by itself establish a general research contribution, and a useful research finding need not produce a broadly successful tool.

The strategy should remain responsive to evidence. It may be useful to investigate and communicate a finding before the larger PostCode vision is complete, while avoiding work whose primary effect would be to manufacture a cleaner publication story.

## 2. Impact and Dissemination Checkpoints

Reconsider practical impact, research contribution, dissemination, and collaboration periodically rather than waiting for a nominally final system. Useful checkpoints may arise after sustained PostCode-on-PostCode use, work on Enblog, unfamiliar software, an additional language, a cross-language comparison, or preparation for a formal user study. The relevant contexts are described in the [`roadmap`](roadmap.md#4-expanding-formative-contexts).

At each checkpoint ask separately:

> **Could this be useful enough to affect how people work?**

and:

> **Have we learned something general enough that other researchers should know it?**

Either can be true without the other. The answers may suggest different actions: continuing formative development, releasing software or demonstrations, writing up a finding, seeking collaborators, conducting a more focused evaluation, or doing none of those yet.

## 3. Publication Strategy

PostCode crosses several existing research areas, but the project need not address all of their communities, and an individual contribution may address only one—or none—of them. The appropriate audience should follow from the finding rather than from the full scope of the project.

### 3.1 Candidate Audiences

Candidate audiences include:

- software engineering, including program comprehension, empirical software engineering, software architecture, software visualization, and AI-assisted development;
- HCI and human-centered AI;
- programming languages, where findings concern projection semantics, cross-language concepts, or program representation;
- information visualization and visual analytics;
- AI and agent research, where findings concern agent context, behavior, or oversight;
- software practitioners, for tools, workflows, demonstrations, and experience reports.

This list is provisional rather than exhaustive. Related work and emerging findings may identify other audiences or show that some of these are not relevant.

For each prospective contribution, ask who could use or evaluate it, what evidence that audience expects, which terminology and related work it requires, and whether presenting the contribution for that audience would clarify or distort the finding.

### 3.2 Speculative Papers

Speculative papers can be useful at different points in the research. Early in an investigation, drafts describing incompatible possible findings can clarify what evidence would distinguish them. The possible findings in [`research.md`](research.md#possible-findings) provide starting points: projections might substantially improve supervision, prove useful only for particular tasks, expose irreducibly language-specific concepts, or fail in consequential ways.

When a particular contribution begins to emerge, drafting its anticipated paper can expose missing evidence, unsupported inferential steps, alternative explanations, and work needed to establish an appropriate claim scope. A provisional audience can help make the expected contribution and evidence concrete.

For each speculative paper, ask:

- What is the claimed contribution?
- What evidence would be needed to support it?
- What alternative explanations would remain?
- What observations would make this paper impossible to write?
- What smaller or different contribution might those observations support instead?

The resulting drafts are reasoning artifacts, not predetermined publication plans. They should test anticipated results rather than turn the roadmap into a plan for producing them.

### 3.3 Publication-Aware Prioritization

Publication opportunities are legitimate inputs to research planning, but should not silently become the project's objective function.

> **Publication-aware prioritization is useful; publication-driven distortion is dangerous.**

When a coherent contribution begins to emerge, ask:

- What contribution and evidence exist now?
- What additional work would make the contribution credible and clearly scoped?
- Is an appropriate venue or deadline approaching?
- Is the additional work independently useful, or at least inexpensive?
- What useful work would be postponed or distorted?
- Would waiting materially improve the finding, or merely make the story larger?

A publication opportunity may reasonably change which work comes next when preparing a contribution would consolidate the work, sharpen the research, attract useful feedback or collaboration, or provide other substantial benefits. The relevant question is whether those gains justify postponing other useful work.

## 4. Collaboration Strategy

Collaboration can be added as specific research or development needs emerge. Potential reasons include:

- missing static-analysis or programming-languages expertise;
- software visualization or information-visualization questions;
- HCI or study-design needs;
- runtime, debugger, profiler, or tracing systems;
- empirical software-engineering methods;
- knowledge of a particular language ecosystem;
- a need for independent users or interpretations;
- a research result that would benefit from another disciplinary perspective;
- open-source contributors naturally developing a sustained role.
