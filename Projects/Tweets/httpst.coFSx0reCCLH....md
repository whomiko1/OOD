# https://t.co/FSx0reCCLH...

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/static/images/article3.5c705a01b476.png)

## Metadata
- Author: [[@addyosmani on Twitter]]
- Full Title: https://t.co/FSx0reCCLH...
- Category: #tweets
- URL: https://x.com/addyosmani/status/2053231239721885918

## Highlights
- ![Agent Harness Engineering](https://pbs.twimg.com/media/HH6JVpKbUAA1doY.jpg)
  *A coding agent is the model plus everything built around it. Harness engineering treats that scaffolding as a living artifact, tightening it every time the agent makes a mistake.* 
  Simply put: whenever an agent fails, you engineer a permanent solution so it never makes that exact mistake again. 
  For the last two years, the industry has debated models: which is the smartest, which writes the cleanest React, or which hallucinates the least. While that conversation matters, it misses the other half of the system. 
  The model is merely one input into a running agent. The rest is the **harness**: the prompts, tools, context policies, hooks, sandboxes, subagents, feedback loops, and recovery paths wrapped around the model so it can actually complete tasks. 
  **A decent model with a great harness consistently beats a great model with a bad harness.** Increasingly, the most interesting engineering work isn't in selecting the model, but in designing the scaffolding around it. 
  That discipline now has a name. @Vtrivedy10 coined the term *harness engineering*, providing a clean breakdown of what a harness actually is and why each piece exists. Other industry voices like @dexhorthy tracking emergent patterns, HumanLayer framing agent failures as configuration "skill issues" Anthropic's engineering team publishing guides on long-running app design, and Birgitta Böckeler exploring the user-side experience - are all convergng on roughly the same idea. 
  This post pulls those threads together. 
  ## What is a Harness, Really? 
  Trivedy's core definition does most of the heavy lifting: 
  **Agent = Model + Harness.** If you're not the model, you're the harness. 
  A harness encompasses every piece of code, configuration, and execution logic that isn't the model itself. A raw model is not an agent. It only becomes one when a harness provides it with state, tool execution, feedback loops, and enforceable constraints. 
  ![Image](https://pbs.twimg.com/media/HH6JkuzaEAAYR1T.jpg) 
  Concretely, a harness includes: 
  - System prompts, CLAUDE.md, AGENTS.md, skill files, and subagent instructions. 
  - Tools, skills, MCP servers, and their technical descriptions. 
  - Bundled infrastructure, such as the filesystem, sandboxes, and headless browsers. 
  - Orchestration logic for spawning subagents, handling handoffs, and routing models. 
  - Hooks and middleware for deterministic execution, like lint checks or context compaction. 
  - Observability tools for logs, traces, cost, and latency metering. 
  At its core, an agent is a system that runs tools in a loop to achieve a goal. The real skill lies in designing both the tools and that loop. 
  While this represents a massive surface area, it is *your* surface area, not the model provider's. Claude Code, Cursor, Codex, Aider, and Cline are all harnesses. **The underlying model might be identical across platforms, but the behavior you experience is dominated by the harness.** 
  ## Let's reframe the "skill Issue" 
  It is common to see engineers blame the model when an agent does something nonsensical, often filing the problem away as something to "wait for the next version" to fix. 
  The harness-engineering mindset rejects this default. Failures are usually somewhat legible. **If the agent ignored a convention, add it to AGENTS.md.** If it ran a destructive command, write a hook to block it. If it got lost in a 40-step task, split the architecture into a planner and an executor. If it consistently finishes with broken code, wire a type-checking back-pressure signal into the loop. 
  As HumanLayer puts it: *"It's not a model problem. It's a configuration problem."* Consider performance benchmarks: a leading model running inside an off-the-shelf framework often scores drastically lower than the exact same model running in a custom, highly-tuned harness. Moving a model into an environment with better codebase tools, tighter prompts, and sharper back-pressure can unlock capabilities the original setup left behind. 
  **The gap between what today's models can theoretically do and what you actually see them doing is largely a harness gap.** 
  ## The Ratchet: Every mistake becomes a rule 
  The most vital habit in harness engineering is treating agent mistakes as permanent signals - not one-off flukes to retry and forget. 
  If an agent ships a PR with a commented-out test that gets merged by accident, that is an input. The next iteration of AGENTS.md must state: "Never comment out tests; delete or fix them." The next pre-commit hook should automatically flag .skip( in the diff. The reviewer subagent must be updated to block commented-out tests. 
  Constraints should only be added when you observe a real failure, and removed only when a capable model renders them redundant. **Every line in a good system prompt should trace back to a specific, historical failure.** 
  Because of this, harness engineering is a discipline rather than a one-size-fits-all framework. The right harness for a specific codebase is entirely shaped by its unique failure history. 
  ## Working backwards from behavior 
  The most effective way to design a harness is to start with the desired behavior and build the component that delivers it: *Behavior we want → Harness design to achieve it.* 
  Every piece of the harness must have a distinct job. **If you cannot name the specific behavior a component exists to deliver, it should be removed.** 
  ![Image](https://pbs.twimg.com/media/HH6JvwebkAAT69Y.jpg) 
  **Filesystem and Git - durable state** 
  The filesystem is foundational. Models can only operate on what fits in their context window. A filesystem provides a workspace to read data, a place to offload intermediate work, and a surface for multiple agents to coordinate. 
  Adding Git provides free versioning, allowing the agent to track progress, branch experiments, and roll back errors. 
  **Bash and Code Execution: general-purpose tooling** 
  Most agents operate on a ReAct loop: reason, act via a tool call, observe, repeat. Instead of pre-building a tool for every conceivable action, giving the agent bash access allows it to build what it needs on the fly. 
  Agents generally excel at shell commands, making bash and code execution the default strategy for autonomous problem-solving. 
  **Sandboxes and Default Tooling** 
  Bash is only useful if it runs safely. Sandboxes provide agents with an isolated environment to run code, inspect files, and verify work without risking the host machine. 
  A good sandbox ships with strong defaults: pre-installed language runtimes, test CLIs, and headless browsers, allowing the agent to observe its own work and close the self-verification loop. 
  **Memory and Search: Continual Learning** 
  Models have no knowledge beyond their training weights and current context. Harnesses bridge this gap using memory files (like AGENTS.md) that inject knowledge into every session. 
  For real-time information like new library versions or live data web search and MCP tools are baked directly into the harness. 
  **Battling Context Rot** 
  Models degrade in reasoning as their context windows fill up. Harnesses manage this scarcity using three primary techniques: 
  - **Compaction:** Intelligently summarizing and offloading older context to prevent API errors. 
  - **Tool-call offloading:** Storing massive tool outputs (like 2,000-line logs) in the filesystem while keeping only the essential headers and footers in context. 
  - **Progressive disclosure:** Revealing instructions and tools only when a task explicitly requires them, rather than loading everything at startup. 
  **Long-Horizon Execution** 
  Autonomous, long-running work suffers from early stopping and poor problem decomposition. Harnesses counter this through structural design: 
  - **Loops:** Intercepting a model's attempt to exit and forcing it to continue against a completion goal in a fresh context window. 
  - **Planning:** Forcing the model to decompose goals into a step-by-step plan file, checking its work via self-verification hooks after each step. 
  - **Splits:** Sep ([View Tweet](https://x.com/addyosmani/status/2053231239721885918))
