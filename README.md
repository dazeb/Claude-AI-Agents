# Claude AI Agents Collection

A comprehensive library of 34 specialized AI agent role definitions for software development studios, covering the entire software development lifecycle from design to deployment.

## Overview

This collection provides detailed role definitions for AI agents that can assist with various aspects of running a modern software development studio. Each agent is specialized for a specific domain and includes comprehensive guidance on capabilities, tools, workflows, and best practices.

All agents are designed to work collaboratively, with clear interfaces for how they receive inputs from and provide outputs to other agents in the ecosystem.

## Repository Structure

```
.claude/agents/
├── design/              # 5 agents - Visual design and user experience
├── engineering/         # 6 agents - Software development and architecture
├── marketing/           # 7 agents - Growth, content, and community
├── product/             # 3 agents - Product strategy and prioritization
├── project-management/  # 3 agents - Portfolio and release coordination
├── studio-operations/   # 5 agents - Finance, legal, support, and infrastructure
└── testing/             # 5 agents - Quality assurance and workflow optimization
```

## Agent Categories

### 🎨 Design (5 agents)

Design agents focus on creating cohesive, accessible, and delightful user experiences.

- **[Brand Guardian](/.claude/agents/design/brand-guardian.md)** - Maintains brand consistency across all touchpoints
- **[UI Designer](/.claude/agents/design/ui-designer.md)** - Crafts user interfaces from wireframes to production-ready components
- **[UX Researcher](/.claude/agents/design/ux-researcher.md)** - Validates designs through user research and testing
- **[Visual Storyteller](/.claude/agents/design/visual-storyteller.md)** - Creates illustrations, infographics, and data visualizations
- **[Whimsy Injector](/.claude/agents/design/whimsy-injector.md)** - Adds delightful micro-interactions and personality

### 💻 Engineering (6 agents)

Engineering agents handle the technical implementation and architecture of software systems.

- **[AI Engineer](/.claude/agents/engineering/ai-engineer.md)** - Integrates LLMs, RAG systems, and AI capabilities
- **[Backend Architect](/.claude/agents/engineering/backend-architect.md)** - Designs APIs, databases, and server-side architecture
- **[DevOps Automator](/.claude/agents/engineering/devops-automator.md)** - Manages CI/CD, infrastructure, and deployments
- **[Frontend Developer](/.claude/agents/engineering/frontend-developer.md)** - Builds responsive web applications with modern frameworks
- **[Mobile App Builder](/.claude/agents/engineering/mobile-app-builder.md)** - Develops cross-platform mobile applications
- **[Rapid Prototyper](/.claude/agents/engineering/rapid-prototyper.md)** - Builds MVPs and proof-of-concepts quickly

### 📣 Marketing (7 agents)

Marketing agents drive user acquisition, engagement, and retention across multiple channels.

- **[App Store Optimizer](/.claude/agents/marketing/app-store-optimizer.md)** - Optimizes app store presence and conversion
- **[Content Creator](/.claude/agents/marketing/content-creator.md)** - Writes SEO-optimized long-form content
- **[Growth Hacker](/.claude/agents/marketing/growth-hacker.md)** - Runs experiments to optimize acquisition funnels
- **[Instagram Curator](/.claude/agents/marketing/instagram-curator.md)** - Manages Instagram strategy and content
- **[Reddit Community Builder](/.claude/agents/marketing/reddit-community-builder.md)** - Builds authentic communities on Reddit
- **[TikTok Strategist](/.claude/agents/marketing/tiktok-strategist.md)** - Creates viral short-form video content
- **[Twitter Engager](/.claude/agents/marketing/twitter-engager.md)** - Builds thought leadership and engagement on Twitter

### 📦 Product (3 agents)

Product agents synthesize user feedback, market research, and strategic priorities.

- **[Feedback Synthesizer](/.claude/agents/product/feedback-synthesizer.md)** - Analyzes and categorizes user feedback at scale
- **[Sprint Prioritizer](/.claude/agents/product/sprint-prioritizer.md)** - Manages backlogs and prioritizes work
- **[Trend Researcher](/.claude/agents/product/trend-researcher.md)** - Identifies market trends and competitive intelligence

### 📋 Project Management (3 agents)

Project management agents coordinate delivery, track experiments, and allocate resources.

- **[Experiment Tracker](/.claude/agents/project-management/experiment-tracker.md)** - Manages A/B tests and learning repositories
- **[Project Shipper](/.claude/agents/project-management/project-shipper.md)** - Coordinates releases and removes blockers
- **[Studio Producer](/.claude/agents/project-management/studio-producer.md)** - Orchestrates portfolio resources and priorities

### 🏢 Studio Operations (5 agents)

Operations agents handle the business infrastructure that keeps the studio running.

- **[Analytics Reporter](/.claude/agents/studio-operations/analytics-reporter.md)** - Tracks KPIs and generates business intelligence
- **[Finance Tracker](/.claude/agents/studio-operations/finance-tracker.md)** - Manages burn rate, budgets, and financial health
- **[Infrastructure Maintainer](/.claude/agents/studio-operations/infrastructure-maintainer.md)** - Maintains internal tools and access management
- **[Legal & Compliance Checker](/.claude/agents/studio-operations/legal-compliance-checker.md)** - Ensures GDPR, SOC 2, and regulatory compliance
- **[Support Responder](/.claude/agents/studio-operations/support-responder.md)** - Handles customer support and documentation

### 🧪 Testing (5 agents)

Testing agents ensure quality through comprehensive testing and continuous optimization.

- **[API Tester](/.claude/agents/testing/api-tester.md)** - Validates API contracts and integration quality
- **[Performance Benchmarker](/.claude/agents/testing/performance-benchmarker.md)** - Stress-tests systems and identifies bottlenecks
- **[Test Results Analyzer](/.claude/agents/testing/test-results-analyzer.md)** - Analyzes test failures and quality trends
- **[Tool Evaluator](/.claude/agents/testing/tool-evaluator.md)** - Evaluates technologies and performs build vs. buy analysis
- **[Workflow Optimizer](/.claude/agents/testing/workflow-optimizer.md)** - Eliminates SDLC bottlenecks and friction

## Agent Definition Format

Each agent definition follows a consistent structure:

- **Profile** - High-level description of the agent's purpose and philosophy
- **Capabilities** - Specific skills and areas of expertise (8-10 key capabilities)
- **Tools & Technologies** - Recommended tools and platforms for this role
- **When to Use This Agent** - Specific scenarios and use cases
- **Example Tasks** - 7 concrete examples demonstrating the agent's work
- **Deliverables** - Expected outputs and artifacts
- **Collaboration** - How this agent works with other agents
- **Success Metrics** - KPIs and measurements of effectiveness
- **Anti-patterns** - Common mistakes to avoid (10 specific anti-patterns)

## How to Use These Agents

### With Claude

These agent definitions can be used as system prompts or role definitions when working with Claude (or other LLMs):

1. **Select the appropriate agent** based on your task
2. **Include the agent definition** in your system prompt or context
3. **Provide task-specific instructions** aligned with the agent's capabilities
4. **Reference collaboration patterns** when multiple agents need to work together

### As Team Templates

These definitions also serve as:

- **Job descriptions** for hiring specialized roles
- **Training materials** for onboarding new team members
- **Process documentation** for standardizing workflows
- **Performance frameworks** defining success metrics for each role

## Key Features

- ✅ **Comprehensive Coverage** - 34 agents spanning all SDLC phases
- ✅ **Detailed Guidance** - Each agent expanded from ~15 to ~100 lines with actionable detail
- ✅ **Collaborative Design** - Clear interfaces showing how agents work together
- ✅ **Practical Examples** - 7+ concrete example tasks per agent
- ✅ **Tool Recommendations** - Specific tools and platforms for each domain
- ✅ **Anti-patterns** - Common mistakes to avoid (10 per agent)
- ✅ **Success Metrics** - Measurable KPIs for each role
- ✅ **Consistent Format** - Standardized structure across all agents

## Statistics

- **Total Agents**: 34
- **Total Categories**: 7
- **Average Agent Length**: ~95-100 lines
- **Total Content**: ~3,400 lines of detailed role definitions
- **Tools Referenced**: 200+ tools and platforms across all domains
- **Example Tasks**: 238 concrete examples (7 per agent)
- **Anti-patterns**: 340 specific mistakes to avoid (10 per agent)

## Contributing

This collection is designed to evolve with the software development landscape. Contributions are welcome for:

- New agent definitions for emerging roles
- Updates to tools and technologies
- Additional example tasks and case studies
- Improved collaboration patterns
- Success metric refinements

## License

MIT License - feel free to use, modify, and distribute these agent definitions for your own projects.

---

**Built for modern software development studios** • **34 specialized agents** • **7 core categories** • **Comprehensive collaboration patterns**
