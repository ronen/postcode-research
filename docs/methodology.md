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

## 2. Formative Use

PostCode should be exercised across substantially different projects, tasks, architectures, domains, and programming languages. No single development context is representative; variation helps expose context-specific assumptions and reduces the risk of optimizing PostCode for any one of them.

Differences among these contexts should be formulated as findings and fed back into the methodological loop.

### 2.1 PostCode on PostCode

PostCode must initially be developed without the benefit of PostCode itself. Once it becomes minimally usable, it can be introduced into its own continued development. This bootstrapping transition creates an unusually tight formative context: the tool, its design, and the software being investigated can evolve together.

Using PostCode while developing PostCode provides sustained access to the developer's own questions, intentions, and moments of friction.

It is especially useful for discovering:

- missing lenses and projection capabilities;
- unsuitable view choices;
- awkward navigation and workspace behavior;
- failures in agent-context exchange;
- distinctions the current design vocabulary does not capture;
- ways in which PostCode and the software developed through it co-adapt.

This context is primarily formative self-study, not an efficacy experiment. It is intended to expose missing representations, bad abstractions, insufficient precision, awkward interactions, and limits of the underlying idea.

It also has important limitations. The developer is motivated to exercise PostCode and can change both the tool and its subject in response to friction. It cannot by itself establish how other developers would behave or whether they would prefer PostCode to source.

### 2.2 Enblog

Using PostCode during ordinary Enblog development provides a familiar but independently evolved codebase, substantial existing design history, and real development tasks not invented solely to exercise PostCode.

This context can expose:

- assumptions created by PostCode's own architecture;
- difficulty introducing PostCode during continued development;
- interactions with pre-existing design and decision artifacts;
- projections needed for work in a different domain;
- whether PostCode supports ordinary tasks rather than only self-directed demonstrations.

The developer's prior familiarity remains a confound. Enblog is not evidence about unfamiliar-user comprehension.

### 2.3 Unfamiliar open-source software

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

Each time the user uses this initial view provides an opportunity to observe their subsequent behavior, both to evaluate the hypothesis and to refine the summary lens. The recurring operation is:

```text
summarize(subject, parameters)
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
- which parameter values the user selects explicitly or implies through the request, and how those choices vary by task and context;
- what stable or navigational structure should accompany the summary.

These observations should combine interaction logs with contemporaneous annotations or other direct user reports, as described in [Self-Observation and Formative Logging](#6-self-observation-and-formative-logging).

## 4. Interpreting Formative Use

The developer should deliberately exercise PostCode during real work, including tolerating some friction that might ordinarily cause an immediate return to source.

That tolerance is useful during formative self-study because sustained use exposes missing representations and awkward interactions. It also means that source-use frequency during formative use is not an unbiased measure of PostCode's success.

When PostCode creates friction, the useful question is not merely whether it failed. Ask:

> **Was the problem in lens selection, projection capability, presentation, interaction, available evidence, or the underlying idea?**

Possible interpretations include:

- the needed lens does not exist;
- the lens exists but lacks necessary information;
- the projection contains the information but its view presents it poorly;
- the system selected an inappropriate lens or view;
- the available repository evidence cannot support the desired claim;
- source is intrinsically clearer or more efficient for this question;
- the projection-based approach is poorly suited to the activity.

Formative use should also help determine which textual results belong in transient conversation, which should become retained views, and which should contribute to longer-lived workspace context.

## 5. Source Excursions

Opening source is a legitimate investigative action, not a failure.

Source should remain conveniently available during formative use for two methodological reasons:

1. PostCode needs visibility into when and why source was needed.
2. The cost of switching to another application should not become an artificial source of friction.

Source excursions help answer:

> **What information was missing from the projection-based workflow?**

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

PostCode should record its own use rather than relying on the developer to maintain a separate research diary.

Potential automatically recorded events include:

- prose questions asked;
- explicit and automatically selected lenses, parameters, and views;
- entities and relationships discovered or opened;
- projections produced;
- views and linked workspaces opened, closed, or revisited;
- test projections inspected;
- revisions and branches inspected;
- projection comparisons;
- source views opened;
- navigation between projections and source;
- unavailable, refused, or failed projections;
- changes in workspace state;
- interactions with coding-agent context.

PostCode should also make it easy to record subjective observations at the moment they occur.

Two useful first-class actions are:

> **Wanted source here**

and:

> **Wish I had lens/projection…**

The observation may be refined when useful:

- wanted different information;
- wanted a different presentation of existing information;
- distrusted the projection;
- source was intrinsically clearer;
- lost orientation or a coherent sense of the program;
- could not express the intended change to the coding agent using the available context.

The goal is not exhaustive annotation. It is to avoid losing useful observations because they were not recorded when they occurred.

The log is primarily a **design instrument**, not an unbiased behavioral dataset. Instrumentation may affect behavior, and the developer decides when to persevere, when to open source, and what deserves annotation.

## 7. From Observation to Finding

Individual events do not automatically constitute findings.

A source excursion, failed projection, or awkward view should retain enough context to support later interpretation. Relevant context may include:

- the development task and information need;
- the repository and revision;
- the current subject, lens, parameters, projection, and view;
- other views and workspace context available at the time;
- the action taken next;
- contemporaneous subjective explanation;
- whether the event recurred in other tasks or contexts.

Recurring patterns can motivate design changes or research hypotheses. For example:

- repeatedly wanting a lens showing who can modify an object;
- dependency projections proving less useful than expected;
- repeatedly asking why particular structures exist;
- consulting source for local sequential behavior;
- projection comparisons becoming unexpectedly important;
- explicit incompleteness increasing willingness to rely on static-analysis results;
- comments and commit history becoming useful ingredients of projected rationale;
- behavioral descriptions of tests proving useful;
- some tests resisting abstraction because their subject is language-specific;
- automatic lens or view selection failing in characteristic ways;
- different presentations proving appropriate for the same projection in different contexts.

The interpretation should record contrary instances and boundaries rather than preserving only evidence that supports the current design.

Findings can change:

- the design hypothesis;
- the candidate lens vocabulary;
- the interaction model;
- the roadmap;
- the research questions themselves.

## 8. Evidence and Evaluation Stages

Evaluation should progress in stages rather than treating early formative use as a user study.

### 8.1 Formative self-study

Question:

> **What is required to make projection-based investigation viable?**

Evidence may include:

- sustained PostCode-on-PostCode use;
- Enblog development;
- unfamiliar-repository investigations;
- automatic usage logs;
- contemporaneous subjective observations;
- source excursions and their stated reasons;
- missing-projection requests;
- design changes motivated by recurring friction.

This stage supports design findings, bounded observations about the author's experience, and hypotheses for later investigation.

### 8.2 External exploratory use

Question:

> **Can unfamiliar developers use this approach, and what happens when they try?**

External users can reveal assumptions caused by the author's prior knowledge, vocabulary, workflow, and willingness to tolerate friction. Exploratory use can refine tasks, instrumentation, and hypotheses without yet supporting broad comparative claims.

### 8.3 Comparative user study

Question:

> **When developers have convenient access to both projections and source, what do they choose, for which tasks, and why?**

This is the appropriate stage for stronger claims concerning:

- voluntary source reduction;
- preference;
- task effectiveness;
- speed;
- comprehension;
- confidence;
- trust;
- differences among task types and development contexts.

Comparative studies should be designed around specific mature questions rather than treated as a single final verdict on PostCode.

## 9. Claim Discipline

Formative experience can produce legitimate findings when claims are scoped to the evidence.

The governing distinction is:

> **Formative use can produce design findings and hypotheses; independent evaluation is required for general claims about developer behavior.**

Appropriate formative claims include:

- “During PostCode development, the author repeatedly wanted mutation information that the available projections did not provide.”
- “Across these three repositories, qualified summaries repeatedly led to useful next investigations.”
- “In this task, source was preferred for understanding local sequential behavior.”
- “This projection vocabulary failed to transfer from TypeScript to Rust.”

Inappropriate generalizations include:

- “Developers prefer projections to source.”
- “PostCode improves comprehension.”
- “Projection comparisons make agent supervision faster.”

unless those claims are supported by evidence designed for the relevant population, tasks, comparison, and outcome.

Negative and mixed findings should be reportable with the same discipline. A technique can be useful for one task, repository, language, or development context and unhelpful for another.

## 10. Relationship to Development Workflow

This methodology overlays software development; it does not prescribe the operational workflow by which development is planned and implemented.

A development workflow may define design plans, implementation tasks, checkpoints, decision logs, backlogs, testing, and updates to canonical system documentation. The research methodology instead determines what observations are gathered during that work, how they are interpreted, and which claims they can support.

The same checkpoint may produce both kinds of output:

- an engineering decision about what to change next;
- a research observation about what PostCode made easy, difficult, trustworthy, or unclear.

Those outputs should remain distinguishable. Architectural rationale should not be buried in research logs, and subjective formative-use observations should not silently become canonical design decisions.

The development workflow for building PostCode itself may eventually differ from the workflow for using PostCode to develop another system. That distinction should emerge from actual use rather than be prescribed before sufficient experience exists.
