# PostCode: Research Methodology

This document describes how building and using PostCode can produce trustworthy research evidence.

The research questions are described in [`research.md`](research.md). The system through which the research is conducted is described in [`design.md`](design.md).

## 1. Methodological Stance

PostCode is a development project conducted as formative research.

Building the system is necessary because many of the relevant questions cannot be answered in advance: which projections prove useful, which information remains difficult to expose, when source is preferable, how much qualification users need, and which abstractions survive contact with real software.

The initial method is therefore sustained use, observation, and revision rather than a fixed efficacy experiment.

The central formative question is:

> **What is required to make projection-based software investigation and supervision viable?**

The governing methodological loop is:

```text
build
  ↓
use during real development
  ↓
observe limitations, friction, success, and surprise
  ↓
formulate findings based on the evidence
  ↓
revise design, research questions, or roadmap
  ↓
use again
```

The process is directed by what the evidence supports. Positive, negative, limiting, mixed, and unexpected findings should all be allowed to redirect the work.

Abstractions should likewise earn their place through accumulated pressure from real use rather than elegance alone.

## 2. Formative Use

PostCode should be exercised across substantially different projects, tasks, architectures, domains, and programming languages. No single development context is representative; variation helps expose context-specific assumptions and reduces the risk of optimizing PostCode for any one of them.

Differences among these contexts should be formulated as findings and fed back into the methodological loop.

### 2.1 PostCode on PostCode

PostCode must initially be developed without the benefit of PostCode itself. Once it becomes minimally usable, it can be introduced into its own continued development. This bootstrapping transition creates an unusually tight formative context: the tool, its design, and the software being investigated can evolve together.

Using PostCode while developing PostCode provides sustained access to the developer's own questions, intentions, and moments of friction.

It is especially useful for discovering:

- missing lenses and projection capabilities;
- unsuitable presentation choices;
- awkward navigation and workspace behavior;
- failures in agent-context exchange;
- distinctions the current design vocabulary does not capture;
- ways in which PostCode and the software developed through it co-adapt.

This context is primarily formative self-study, not an efficacy experiment. It is intended to expose missing representations, bad abstractions, insufficient precision, awkward interactions, and limits of the underlying idea.

It also has important limitations. The developer is motivated to exercise PostCode and can change both the tool and its subject in response to friction. It cannot by itself establish how other developers would behave or whether they would prefer PostCode to source.

<a id="existing-project-development"></a>

### 2.2 Continued Development of an Existing Project

One useful formative context is to apply PostCode during the continued development of an existing project already familiar to the investigator. PostCode's author has a suitable pre-existing personal project. It remains in progress and undeployed, so it presents genuine development needs that were not invented to exercise PostCode. It also has no specific delivery deadline, allowing some tolerance of formative friction without interfering with time-critical work.

Prior familiarity makes it possible to compare PostCode's projections with an established understanding of the system, but remains a confound when interpreting the resulting observations. The project's specific product details are not relevant here. As with every formative context, however, characteristics of its domain and development circumstances should be considered when interpreting observations.

This context can expose:

- assumptions created by PostCode's own architecture;
- difficulty introducing PostCode during continued development;
- interactions with pre-existing design and decision artifacts;
- projections needed for work in a different domain;
- whether PostCode supports ordinary tasks rather than only self-directed demonstrations.

Existing-project development is not evidence about unfamiliar-user comprehension.

### 2.3 Ab initio project

Developing a separate new project with PostCode present from its inception tests whether projections can support the creation and continued supervision of software, rather than only the reconstruction of an existing implementation.

Unlike PostCode-on-PostCode, the tool and its subject are distinct. Unlike existing-project development, the project begins without a pre-existing implementation or development history. This context can expose whether intentions, rationale, requirements, and conceptual structure can be captured as they arise; whether PostCode's existing projection capabilities are useful for guiding a new project's early development; and how PostCode-mediated supervision affects the software being produced.

### 2.4 Unfamiliar open-source software

Unfamiliar OSS projects provide software whose development PostCode did not influence and for which the investigator lacks a pre-existing mental model.

They can test whether PostCode can:

- establish enough orientation to begin a useful investigation;
- derive useful concepts from the evidence an arbitrary repository provides;
- expose where missing rationale or history limits projection;
- avoid relying on private conventions shared by PostCode and PostCode-native software;
- generalize across application domains;
- accommodate substantially different software architectures;
- identify concepts that generalize across programming languages;
- identify concepts and mechanisms that remain language-specific.

OSS use should involve genuine questions or development tasks where possible. Artificial tours of repositories may reveal projection defects, but they provide weaker evidence about sustained usefulness.

## 3. Evaluating and Refining Summary as an Initial View

PostCode's design makes [summary the initial view and a basis for recursive navigation](design.md#32-summary-as-initial-view-and-recursive-navigation). We treat this design decision as a hypothesis:

> **A summary can satisfy the user's current information need or usefully support the next step in their investigation.**

Each use of this initial view provides an opportunity to observe the user's subsequent behavior, both to evaluate the hypothesis and to refine the summary lens. The recurring operation is:

```text
summarize(subject, lens_parameters)
```

This provides a repeatable starting point across development contexts without treating the resulting summaries as standardized measurements.

Observations relevant to evaluating the hypothesis include:

- whether the summary satisfies the user's current information need;
- whether it supports a useful next step in the investigation;
- whether it provides a coherent sense of the program or only a list of facts;
- which suggested next lenses are actually followed;
- when the user stops after the summary, and whether that reflects sufficient understanding, an unhelpful result, or abandonment.

Observations relevant to refining the lens include:

- which information is consistently useful for orientation;
- which information is omitted but immediately wanted;
- which claims are difficult to qualify;
- which summaries merely restate obvious repository structure;
- which interpretations genuinely help navigation;
- which lens parameter values the user selects explicitly or implies through the request, and how those choices vary by task and context;
- what stable or navigational structure should accompany the summary.

These observations should combine interaction logs with contemporaneous annotations or other direct user reports, as described in [Self-Observation and Formative Logging](#6-self-observation-and-formative-logging).

## 4. Interpreting Formative Use

To gather formative evidence, the developer will deliberately use PostCode during real development work and tolerate some friction that might otherwise prompt an immediate return to source.

That tolerance is useful during formative self-study because sustained use exposes missing representations and awkward interactions. It also means that source-use frequency during formative use is not an unbiased measure of PostCode's success.

When PostCode creates friction, the useful question is not merely whether it failed. Ask:

> **Was the problem in lens selection, projection capability, presentation, interaction, available evidence, or the underlying idea?**

Possible interpretations include:

- the needed lens does not exist;
- the lens exists but lacks necessary information;
- the projection contains the information but the selected presentation shows it poorly;
- the system selected an inappropriate lens or presentation;
- the available repository evidence cannot support the desired claim;
- source is intrinsically clearer or more efficient for this question;
- the projection-based approach is poorly suited to the activity.

Formative use should also help determine which textual results belong in transient conversation, which should become retained views, and which should contribute to longer-lived workspace context.

### 4.1 Evaluating Conventions

In addition to individual prompts, coding agents commonly receive standing project instructions in the form of conventions to follow. Formative use of PostCode will therefore take place alongside such conventions, and the investigation should observe how those conventions affect PostCode-mediated supervision.

When evaluating a convention in relation to PostCode, its rationale and whether it was already in force or adopted during formative use should be recorded where possible. Its intended role may be a project-specific engineering choice, a deliberate formative intervention, or both; that role is not a conclusion about the convention's effects or generality.

Evidence about the convention's effects can be gathered from interaction logs and contemporaneous observations of whether projections become clearer, more complete or easier to trust; whether users need fewer source excursions or explanatory prompts; whether agents can implement conceptual requests with less clarification; whether the convention creates friction, artificial structure or other costs; and whether the resulting software remains clear outside PostCode. Before-and-after observations and comparison among PostCode-on-PostCode, existing-project development, ab initio development, unfamiliar software and different languages can provide further evidence.

Interpretation should distinguish:

- a convention that formalizes a property already observed without explicit instruction from one intended to produce a property not yet observed;
- a response to a missing PostCode capability from a property genuinely needed for source-secondary supervision;
- an independently useful improvement in conceptual clarity from adaptation that merely makes the software easier for PostCode to project;
- a convention that generalizes across projects or languages from one that depends on a particular implementation, analysis, project or language.

Local adoption creates an opportunity for observation; it does not by itself establish benefit, necessity, causation or generalizability.

## 5. Source Excursions

Opening source is a legitimate investigative action, not a failure.

Source should remain conveniently available during formative use for two methodological reasons:

1. PostCode needs visibility into when and why source was needed.
2. The cost of switching to another application should not become an artificial source of friction.

Source excursions help answer:

> **What prompted this source excursion, and what did source provide?**

Their use should be recorded automatically when possible. PostCode may also ask unobtrusively what the developer was looking for, with responses such as:

- missing projection;
- needed more detail;
- wanted to verify or trust-check;
- source seemed clearer;
- needed local implementation logic;
- other.

The prompt should not block source access and should be easy to ignore.

The count of source openings is not meaningful by itself. Interpretation requires the task, reason, available alternatives, and the developer's deliberate willingness to tolerate formative friction.

Independent evaluation can later ask a different question:

> **When developers have convenient access to both projections and source, what do they choose, for which tasks, and why?**

## 6. Self-Observation and Formative Logging

Formative evidence should combine automatically recorded interaction events with contemporaneous subjective observations. PostCode's support for capturing this evidence is described in [Formative Observation Support](design.md#38-formative-observation-support).

Formative investigation should maintain an explicit evidence boundary. Observation records, subsequent analysis, and withheld reference material remain outside the repository under investigation and outside the evidence available to PostCode and its coding agents.

Without this boundary, coding agents developing PostCode might use research observations or findings as development guidance, and PostCode-on-PostCode projections might rely on those same materials rather than independently recovering information from application-development evidence.

Relevant recorded context and events include:

- the current operational task and information need, where formalized;
- prompts and prose requests submitted to PostCode;
- prompts sent to coding agents, when available, and references to external tasks or conversations;
- explicit and automatically selected lenses, lens parameter values, presentations, presentation parameter values, and resulting views;
- entities and relationships discovered or opened;
- projections produced;
- views and linked workspaces opened, closed, or revisited;
- relationships among views, including derivation, placement, live dependencies, and changes in investigation roots;
- test projections inspected;
- revisions and branches inspected;
- projection comparisons;
- source views opened;
- navigation between projections and source;
- unavailable, refused, or failed projections;
- changes in workspace state;
- interactions with coding-agent context.

Subjective observations may record that the user:

- wanted different information;
- wanted a different presentation of existing information;
- distrusted the projection;
- source was intrinsically clearer;
- lost orientation or a coherent sense of the program;
- could not express the intended change to the coding agent using the available context.

The goal is not exhaustive annotation. It is to avoid losing useful observations because they were not recorded when they occurred.

Immediate reactions provide context for later interpretation; they are not standardized satisfaction measurements or evidence of effectiveness by themselves.

The log is primarily a **design instrument**, not an unbiased behavioral dataset. Instrumentation may affect behavior, and the developer decides when to persevere, when to open source, and what deserves annotation.

## 7. From Observation to Finding

Individual events do not automatically constitute findings.

A source excursion, failed projection, awkward view, or other event should retain enough context to support later interpretation. This includes the development task and information need; the PostCode version; the observed repository and its Git commit or relevant working-tree state; subject, lens, lens parameter values, projection, presentation, presentation parameter values, view, workspace context, and relevant navigation lineage; the action taken next; and any contemporaneous subjective explanation.

Recurring patterns can motivate design changes or research hypotheses. Interpretation should also preserve contrary instances and contextual boundaries rather than retaining only evidence that supports the current design.

Findings may revise the design hypothesis, the set and behavior of lenses, the interaction model, the roadmap, or the research questions themselves.

## 8. Evidence and Claim Scope

The methodology distinguishes forms of evidence by the claims they can support.

The governing distinction is:

> **Formative use can produce design findings and hypotheses; independent evaluation is required for general claims about developer behavior.**

### 8.1 Formative self-study

Evidence from sustained formative use, interaction logs, contemporaneous observations, source excursions, and resulting design changes can help determine what is required to make projection-based investigation viable. It supports design findings, bounded observations about the developer's experience, and hypotheses for later investigation.

### 8.2 External exploratory use

External users can reveal assumptions caused by the author's prior knowledge, vocabulary, workflow, and willingness to tolerate friction. Exploratory use can refine tasks, instrumentation, and hypotheses without yet supporting broad comparative claims.

### 8.3 Formal user studies

User studies can support appropriately scoped claims about developer behavior, including what developers choose when both projections and source are available, and about preference, effectiveness, speed, comprehension, confidence, and trust. They should address specific mature questions and identify the relevant population, tasks, methods, outcomes, and development contexts rather than act as a single final verdict on PostCode.

All findings should remain scoped to their evidence. Negative and mixed findings should be treated with the same discipline as positive ones; a technique may be useful for one task, repository, language, or development context and unhelpful for another.

## 9. Relationship to Development Workflow

This methodology overlays software development; it does not prescribe the operational workflow by which development is planned and implemented.

A development workflow may define design plans, implementation tasks, checkpoints, decision logs, backlogs, testing, and updates to canonical system documentation. The research methodology instead determines what observations are gathered during that work, how they are interpreted, and which claims they can support.

The same checkpoint may produce both kinds of output:

- an engineering decision about what to change next;
- a research observation about what PostCode made easy, difficult, trustworthy, or unclear.

Those outputs should remain distinguishable. Architectural rationale should not be buried in research logs, and subjective formative-use observations should not silently become canonical design decisions.

Development workflows may vary across developers, projects, tasks, and contexts, including between building PostCode itself and using PostCode to develop other systems. The methodology should accommodate those differences rather than presuppose a single PostCode workflow.
