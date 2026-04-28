# SkillOS Kernel Plugin for Claude Code

This plugin installs the core kernel of the **SkillOS "Pure Markdown Operating System"** into Claude Code. It does not contain pre-built solutions; it provides the factory to build them.

The kernel is powered by a single command, `/skillos`, which enables Claude to solve complex goals by **dynamically creating and orchestrating a team of specialized agents on the fly.**

## Overview

SkillOS represents a paradigm shift in how AI systems solve complex problems. Rather than shipping pre-built agents for specific domains, SkillOS provides a **self-evolving kernel** that:

- **Creates agents on demand** tailored to your specific problem
- **Learns from every execution** by capturing and consolidating patterns
- **Evolves continuously** by reusing successful strategies from past projects
- **Operates purely through markdown** using Claude Code's native capabilities

Think of it as an operating system where the "programs" (specialized agents) are written at runtime based on the task at hand, rather than installed in advance.

## Core Components

This plugin provides the essential "daemons" and system files for the SkillOS:

### Core System Agents

-   **SystemAgent**: High-level orchestrator responsible for agent lifecycle management, task decomposition, and workflow coordination
-   **MemoryAnalysisAgent**: Captures and logs all system activities in structured memory traces
-   **MemoryConsolidationAgent**: Extracts learnings from execution logs and generates reusable patterns

### System Specifications

-   **SmartMemory.md**: Defines the hierarchical memory architecture (short-term logs, long-term learnings)
-   **QueryMemoryTool.md**: Specifies how to search and retrieve knowledge from past projects
-   **MemoryTraceManager.md**: Documents the lifecycle and relationships of memory traces
-   **ClaudeCodeToolMap.md**: Maps SkillOS conceptual operations to Claude Code's actual tools

### Master Command

-   **/skillos**: The kernel shell that analyzes goals, creates specialized agents, orchestrates execution, and consolidates learnings

## How It Works: Dynamic Evolution

When you provide a goal, the `/skillos` command follows this workflow:

### 1. Analyze the Goal
Decomposes your high-level objective into distinct tasks requiring specialized expertise (e.g., 'high-level vision', 'mathematical theory', 'quantum coding', 'technical documentation').

### 2. Create Project Structure
Generates a dedicated project workspace:
```
projects/[ProjectName]/
├── components/
│   └── agents/           # Domain-specific agents created for this project
├── output/               # Final deliverables
└── memory/
    ├── short_term/       # Raw interaction logs
    └── long_term/        # Consolidated learnings
```

### 3. Create Specialized Agents
**This is the core innovation.** For each required expertise, SkillOS writes a new agent markdown file with:
- **YAML frontmatter** defining capabilities, tools, and metadata
- **Detailed system prompt** tailored to the specific project domain

Examples of dynamically created agents:
- `VisionaryAgent.md` - Strategic conceptualization
- `MathematicianAgent.md` - Theoretical framework development
- `QuantumEngineerAgent.md` - Quantum circuit implementation
- `TechnicalWriterAgent.md` - Documentation generation
- `CodeReviewerAgent.md` - Quality assurance

### 4. Orchestrate Execution
Delegates tasks to agents by:
1. Reading the agent's markdown definition
2. Invoking it via the `Task` tool with specific instructions
3. Logging the complete interaction (request + response)
4. Managing dependencies and data flow between agents

### 5. Produce Outputs
All deliverables (code, documentation, data files, visualizations) are saved to the project's `output/` directory.

### 6. Learn and Improve
After execution:
1. **MemoryConsolidationAgent** analyzes all short-term logs
2. Extracts successful patterns, agent designs, and strategies
3. Generates `project_learnings.md` in long-term memory
4. Creates reusable templates for future projects

### 7. Continuous Evolution
Future projects query long-term memory to:
- Reuse proven agent designs
- Apply successful workflow patterns
- Avoid documented pitfalls
- Bootstrap faster with adapted templates

## Installation

### Install from Marketplace

```bash
/plugin marketplace add evolving-agents-labs/skillos_plugin
/plugin install skillos-plugin
```

### Install from Local Directory

```bash
/plugin install /path/to/skillos_plugin/skillos-plugin
```

### Verify Installation

```bash
/skillos --help
```

## Usage Examples

### Example 1: Quantum Computing Research

```bash
/skillos "Develop a quantum computing solution for radiation-free arterial navigation by analyzing pressure wave echoes"
```

### Example 2: Full-Stack Application Development

```bash
/skillos "Build a real-time collaborative whiteboard application with WebSocket synchronization and persistent storage"
```

### Example 3: Data Science Pipeline

```bash
/skillos "Create a machine learning pipeline to predict customer churn using behavioral analytics and feature engineering"
```

## Architecture Philosophy

### Why Dynamic Agent Creation?

Traditional approaches pre-define agents for specific domains. This has limitations:

- **Domain coverage is bounded** - Can't handle novel combinations
- **Agents are generic** - Not tailored to specific problem nuances
- **System grows bloated** - Shipping hundreds of pre-built agents
- **No learning feedback loop** - Each execution starts from scratch

SkillOS inverts this model:

- **Infinite domain coverage** - Creates agents for any expertise needed
- **Problem-specific agents** - Tailored prompts for exact requirements
- **Minimal kernel size** - Only core system agents shipped
- **Continuous evolution** - Every project improves future performance

### The Pure Markdown Paradigm

SkillOS operates entirely through markdown files:

- **Agent definitions** = Markdown files with YAML frontmatter + prompt
- **Memory traces** = Markdown logs of interactions
- **Knowledge base** = Markdown documents with structured learnings
- **Orchestration** = Reading markdown to generate prompts

This approach is:
- **Human-readable**: All system state is inspectable
- **Version-controllable**: Track agent evolution in git
- **Portable**: No binary dependencies or databases
- **Extensible**: Easy to modify and enhance

## Memory System

### Short-Term Memory (Episodic)
Located in `projects/[ProjectName]/memory/short_term/`

- **Purpose**: Capture raw execution traces during project runtime
- **Format**: Timestamped markdown logs with full prompts and responses
- **Lifecycle**: Created during execution, consumed during consolidation
- **Structure**: One file per agent interaction

### Long-Term Memory (Semantic)
Located in `projects/[ProjectName]/memory/long_term/`

- **Purpose**: Store distilled knowledge for future reuse
- **Format**: Structured markdown with patterns, templates, and insights
- **Lifecycle**: Created by consolidation, queried at project start
- **Structure**: Organized by type (agent templates, workflow patterns, domain knowledge)

## Project Structure

Every SkillOS project follows this structure:

```
projects/[ProjectName]/
├── components/
│   └── agents/
│       ├── Agent1.md              # Dynamically created agents
│       ├── Agent2.md
│       └── Agent3.md
├── output/
│   ├── deliverable1.md            # Final outputs
│   ├── code_artifact.py
│   └── visualization.png
└── memory/
    ├── short_term/
    │   ├── 20250111_143022_Agent1_task.md    # Interaction logs
    │   ├── 20250111_143045_Agent2_task.md
    │   └── 20250111_143102_Agent3_task.md
    └── long_term/
        ├── project_learnings.md              # Consolidated insights
        ├── agent_templates/                  # Reusable agent specs
        └── workflow_patterns/                # Orchestration patterns
```

## Extending SkillOS

### Add Core Agents

To add a new core system agent:

1. Create `agents/NewCoreAgent.md` with full specification
2. Reference in `/skillos` command documentation
3. Update `ClaudeCodeToolMap.md` with usage patterns

### Enhance System Files

To improve OS specifications:

1. Edit `system_files/*.md` with new patterns or insights
2. Ensure consistency with Claude Code's tool capabilities
3. Document changes in learning files

### Customize Orchestration

To modify the master orchestrator:

1. Edit `commands/skillos.md`
2. Adjust workflow steps or add new phases
3. Update README with new capabilities

## About Claude Code Plugins

SkillOS is built as a [Claude Code Plugin](https://www.anthropic.com/news/claude-code-plugins), a powerful extension system that lets you customize Claude Code with:

- **Slash commands**: Custom shortcuts for frequently-used operations
- **Subagents**: Purpose-built agents for specialized tasks
- **MCP servers**: Connections to tools and data sources
- **Hooks**: Behavior customization at key workflow points

Plugins are designed to be lightweight, shareable, and easy to toggle on/off based on your needs.

## Contributing

We welcome contributions to enhance the SkillOS kernel:

- **Core agent improvements**: Refine system agent prompts and capabilities
- **System specifications**: Enhance memory management and tool mappings
- **Documentation**: Add examples, tutorials, and use cases
- **Bug reports**: Submit issues with agent creation or orchestration

## License

Apache License 2.0

Copyright 2025 Evolving Agents Labs

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Credits

**Evolving Agents Labs** - Creators of SkillOS

Built on [Claude Code](https://claude.ai/code) by Anthropic.

## Links

- **Plugin Documentation**: [Claude Code Plugins](https://www.anthropic.com/news/claude-code-plugins)
- **Claude Code**: [Official Website](https://claude.ai/code)
- **Repository**: [GitHub](https://github.com/evolving-agents-labs/skillos_plugin)

---

**Start building with SkillOS:**

```bash
/skillos "Your ambitious goal here"
```

Let the system create the agents. Let the agents build the solution. Let the solution teach the system.

**Dynamic evolution in action.**
