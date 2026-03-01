---
name: human-training
description: "Reviews the prompts and instructions given in this session and teaches the user how to improve their AI instruction skills across 5 disciplines: prompt engineering, context engineering, intent engineering, specification engineering, and agent and workflow engineering. Use when the user wants feedback on their AI instructions or wants to learn from the current session."
---

Review every prompt and instruction the user has given in this session. For each of the 5 areas below, identify what they did well and what could be improved. Be specific - reference their actual prompts where relevant. Suggest improved versions where the learning value is high.

Output must be plain prose. Do not use markdown formatting (no headers with #, no bold with **, no bullet points with - or *). Use numbered lists and plain section labels only. If an area is not relevant to the tasks reviewed, mark it N/A with a one-line explanation. Be concise but not superficial. Depth matters where learning value is high.

Impact tagging. Every improvement you recommend must be tagged with one of the following two labels, placed in square brackets at the start of the point:

[ERROR RISK] means this gap caused, or could realistically have caused, an actual error, incorrect output, rework, or a failed action in this specific session. Reference the specific moment where it mattered.

[GOOD PRACTICE] means this is a sound improvement but had no material negative consequence in this session. It builds robustness for more complex future tasks.

Apply these tags consistently across all 5 areas. Do not use [ERROR RISK] unless you can point to a concrete moment in the session where the gap had or could have had a real consequence. The distinction matters because it tells the user where to invest their learning effort first.

The overall goal is to educate the user in excellent AI instruction skills and provide ongoing learning as AI systems evolve.


AREA 1: PROMPT ENGINEERING

Scope: the craft of writing individual instructions. This area covers how the user words, structures, and constrains specific prompts. It does not cover what background information is provided (Area 2), why the work matters (Area 3), or how work is governed over time (Area 4). Note that briefly explaining why a specific rule exists within a prompt (for example, "use plain language because our learners are non-technical") is a prompt-level technique that belongs here — it helps Claude apply a rule correctly. The broader organisational why — mission, values, decision principles — belongs in Area 3.

Review each prompt the user gave in this session and assess the following:

Clarity and the colleague test. Apply the Anthropic standard: if you showed this prompt to a capable colleague with no context, would they be confused? Wherever the answer is yes, explain what was ambiguous and suggest a clearer version. Note that Claude, like a new employee, lacks implicit context - explicit instructions always outperform assumed knowledge.

Examples and counter-examples. Should the user have provided 3-5 representative examples in <example> tags showing exact desired input-output format? Should they have shown examples of what NOT to do? Were edge cases and variations represented?

Guard rails and constraints. What boundaries or restrictions were missing? Where could Claude have gone off-course without explicit limits? Note any missing instructions about tone, length, scope, audience, or error-handling behaviour.

Output format. How explicitly did the user define expected format, structure, length, and style? Flag any cases where Claude had to guess the output form.

Conflict and ambiguity resolution. Did the user give guidance on how to handle edge cases, contradictions, or unclear situations? What priority order should have been stated? What fallback behaviour should have been specified?

XML structure. Should the user have used XML tags (such as <instructions>, <context>, <examples>, <documents>, <input>) to separate the parts of their prompt? Unstructured prompts make it harder for Claude to distinguish instructions from content.


AREA 2: CONTEXT ENGINEERING

Scope: the information environment — what Claude knows. This area covers the data, documents, reference material, and environmental resources the user provides. It is distinct from how instructions are written (Area 1) and from the values and purpose that guide judgement (Area 3). If the user provided a fact, a file, or a configuration, that is context. If the user communicated a goal, a value, or a decision principle, that is intent.

Review how well the user set up and maintained the information environment for the session:

Pre-loaded resources. What reference files (.md documents, course outlines, brand guidelines, student personas, organisational documents, style guides) should have been provided at the start of the session? Identify every instance where Claude had to infer or guess something that a well-prepared file would have resolved.

Token efficiency. Were there repeated explanations across prompts that a single context file would have eliminated? Long conversations degrade in accuracy as tokens accumulate (context rot). What could have been front-loaded to reduce this?

Document structure for long-context tasks. When the user provided long documents or reference material, were they placed correctly (at the top of the prompt, above queries and instructions)? Should they have been wrapped in <documents> tags with <source> labels? Should Claude have been asked to quote relevant sections in <quotes> tags before answering?

Tool and environment configuration. Were there tool configurations, file paths, platform settings, or system behaviours the user should have documented and shared upfront (for example, Thinkific course IDs, folder structures, naming conventions)?

Context window awareness. For long-running tasks, should the user have set up state management - structured progress notes, JSON summaries, or git-tracked outputs - so that if the context window compacted, Claude could recover efficiently? Note any multi-session work where this would have applied.

Informational resource files. What standing reference files would add ongoing value across future sessions (for example, a course_structure.md, a platform_conventions.md, or a brand_voice.md)?


AREA 3: INTENT ENGINEERING

Scope: the purpose and values layer — why the work matters and how Claude should exercise judgement when not explicitly instructed. This area covers goals, success criteria, organisational mission, values, and decision principles. It is distinct from factual background (Area 2) and individual instruction clarity (Area 1). The test is: if Claude encountered a situation not covered by explicit instructions, would it know what to do? If not, that is an intent engineering gap. Note that organisational purpose belongs here — not in context engineering — because it shapes judgement and values, not just knowledge.

Review whether the user communicated purpose and values clearly enough to guide autonomous decision-making:

Session goals and success criteria. Were the goals of the session stated explicitly at the outset? Did the user define what a successful outcome looks like? Anthropic's standard is to define success criteria before engineering begins, not during.

Values and principles. What organisational or personal values should the user have made explicit so Claude could make better judgement calls without asking? For example, values around accessibility, tone, learner experience, or content standards.

Organisational purpose. Would it have helped Claude to understand the broader mission - what Inner Success Leadership is, who it serves, and what transformation it creates? This is not background information; it is the lens through which Claude makes decisions when the instructions run out. Note any decisions Claude had to make on behalf of the organisation that would have been better guided by a stated mission.

Decision boundaries. What decisions should the user have explicitly authorised or restricted? Where did Claude make judgement calls that should have been pre-defined? Note any moments where Claude had to assume rather than follow stated principles.

Priority order. When the user's instructions contained potential conflicts (for example, between speed and quality, or brevity and completeness), was a priority order stated? Flag any missing hierarchy of values.


AREA 4: SPECIFICATION ENGINEERING

Scope: the governance and quality layer — how work is managed, tracked, and verified over time. This area covers the documents, standards, progress logs, quality rubrics, and verification processes that surround a session. It is distinct from in-prompt instructions (Area 1), the information provided during a session (Area 2), and the values that guide decisions (Area 3). The test is: if someone reviewed this work tomorrow, would they have enough documentation to understand what was done, assess its quality, and know what comes next?

Review the structural and documentary scaffolding around the session:

Organisational documents. What documents should the user have given Claude access to before the session began? Consider course outlines, learning objectives, learner personas, content quality standards, brand guidelines, platform usage rules, and any existing deliverables.

Progress logs. Should a progress log have been set up? What format would have been most useful - a running markdown file, a structured JSON log, a git-tracked changelog? What should it have recorded (decisions made, steps completed, items deferred, open questions)?

Output quality assessment. How should the user have defined quality criteria in advance? What rubric or checklist would have helped Claude verify that outputs were correct and complete before saving them? Note any cases where errors were only caught after the fact.

Results verification. What verification steps should have been built into the workflow? For example, should Claude have been instructed to re-read saved content to confirm it matched the intended input, or to screenshot and check Thinkific pages after saving? Note any gaps in the review loop.

Test-first design. For complex or multi-step tasks, should the user have defined test cases or acceptance criteria upfront - before Claude began work - so that success could be measured objectively?


AREA 5: AGENT AND WORKFLOW ENGINEERING

Scope: the process design layer — how multi-step autonomous work is structured, sequenced, and safeguarded. This area covers workflow patterns, tool definitions, safety and reversibility, state management, subagent use, and feedback loops. It is distinct from how individual instructions are written (Area 1), what information is provided (Area 2), what values guide decisions (Area 3), and how work is governed over time (Area 4). The test is: if Claude ran this workflow autonomously from start to finish, would it do so reliably, safely, and efficiently?

Review how well the user designed for autonomous, multi-step operation:

Simplicity and necessity. Was the level of complexity in the workflow appropriate? Anthropic's principle is to start with the simplest solution and only add complexity when it demonstrably improves outcomes. Were there steps that could have been combined, eliminated, or handled more directly?

Workflow pattern. What workflow pattern best fits this session's tasks - prompt chaining (sequential steps with checks), routing (classifying inputs to different processes), parallelisation (independent subtasks run simultaneously), orchestrator-workers (delegating to specialised processes), or evaluator-optimiser (iterative refinement with feedback)? Was the pattern the user implicitly used the most appropriate one?

Tool definitions. When tools or external systems were involved (such as Thinkific, browser automation, or file operations), were the tool parameters, expected behaviours, and edge cases defined clearly enough? Anthropic's standard is to give tool definitions as much attention as the main prompt.

Reversibility and safety. Were destructive or hard-to-reverse actions (saving content, publishing lessons, overwriting files) handled with appropriate caution? Should the user have built in explicit confirmation steps or staged the work in a way that allowed review before committing?

State management and recovery. For multi-step or multi-session tasks, was there a plan for how Claude would recover if the context window compacted or a step failed? Should structured checkpoints, recovery scripts, or state files have been defined?

Subagent and parallelisation opportunities. Were there independent subtasks in this session that could have been run in parallel using subagents, reducing total time? Conversely, were subagents used where direct work would have been faster and more coherent?

Feedback loops. Were there points in the workflow where Claude should have paused, reported progress, and received user input before continuing? Note any long autonomous sequences that ran without a built-in review gate.

Effort ceiling. Did the user define a complexity budget — a point at which Claude should stop attempting workarounds and instead present options, including manual alternatives, before continuing? Claude's default behaviour under autonomous operation is to keep solving; without an explicit effort ceiling it will apply increasing ingenuity to overcome obstacles the user would have preferred to handle manually. Assess whether the session would have benefited from a standing rule such as: "If you hit an obstacle you cannot resolve in two attempts, stop, describe what you tried and why it failed, present your remaining options including any manual alternatives with a recommendation, and wait for approval before continuing." Flag any session where token spend on recovery work exceeded token spend on productive task execution, as this is a reliable signal that an effort ceiling was missing.


TOKEN USAGE ANALYSIS

This section estimates the token cost of the actual session versus what an optimised session would have cost. The purpose is to give the user a concrete, quantified signal of how much context engineering and prompt clarity affect efficiency. This is an approximation based on text length (roughly 4 characters per token for English prose). It will not match exact API counts but is directionally reliable and improves as a comparative tool across sessions.

Step 1: Estimate actual session tokens. Review the full conversation and estimate the total token count across all turns — user messages, Claude responses, tool calls, and tool results. Group them into: setup and clarification turns (questions asked, corrections made, information that should have been pre-loaded), task execution turns (the actual work), and recovery turns (retries, error handling, rework caused by ambiguous instructions).

Step 2: Estimate optimised session tokens. Model what the session would have looked like if all the [ERROR RISK] and [GOOD PRACTICE] improvements had been applied. Replace each clarifying exchange with the token cost of a well-written context file or upfront instruction. Replace each rework turn with zero. Add the estimated token cost of the recommended pre-loaded files (a typical 400-word .md reference file costs approximately 500 tokens). Show the calculation.

Step 3: State the comparison. Present three numbers: estimated actual tokens, estimated optimised tokens, and the estimated saving as a percentage. Then give a one-sentence interpretation — for example, whether the saving came mainly from eliminated clarification, reduced rework, or shorter per-turn context.

Step 4: Efficiency rating. Give the session an efficiency rating out of 10, where 10 means all tokens were spent on productive task execution with no clarification overhead or rework, and 1 means the majority of tokens were spent on setup, correction, and recovery. State briefly what the main drag on efficiency was.

Be transparent that these are estimates. Label the section clearly as approximate. The value is in the comparison across sessions over time, not in the absolute numbers.


FURTHER COMMENTS

After reviewing all 5 areas, add a section called Further Comments. Address the following:

Missed elements. Note anything significant the user missed that does not fit into the 5 areas above.

Gaps in the human_training skill itself. Assess the specification the user wrote for this skill. What did they do well? What should they have included or done differently? Apply the same standards the skill teaches.

Emerging best practices. Note any relevant Anthropic-documented practices from 2025-2026 that are applicable to what the user is trying to achieve and that they may not yet be applying. Reference the Anthropic engineering principle that performance should be measured empirically and that complexity should only be added when proven necessary.

Continuous learning note. Close with a one-sentence observation about how the user's AI instruction skills are developing, and what the single highest-leverage improvement would be for their next session.
