# AGENTS.md -- Plugins Directory

<!-- markdownlint-disable MD013 -->

## Agent Roles

Within the Cogni AI agent ecosystem, these roles are strictly delineated by capability, knowledge depth, and delegation hierarchy, rather than general industry titles:

- **Coder** (`cogni-ai-coder`): Focuses on tactical code edits and general logic implementations using critical thinking. Lacks deep, framework-specific knowledge. Efficiently handles small, clearly defined coding tasks. Complex, language-specific feature implementations should involve a **Programmer**.
- **Programmer** (`cogni-ai-programmer`): Possesses deep syntax and manual-level knowledge of specific languages and frameworks (e.g., Python, React, Next.js). Solves technical problems by utilizing specific language features. Can decompose tasks and delegate smaller, routine coding work to **Coder** agents.
- **Developer** (`cogni-ai-developer`): Operates at a senior level with practical experience derived from actual software lifecycles, real-world challenges, and self-directed learning. Focuses on end-to-end functionality and delegates specific technical component implementations to **Programmer** agents.
- **Software Architect** (`cogni-ai-architect`): Maintains a high-level understanding of system components, interdependencies, and broad architectural patterns (software and cloud architecture). Assesses complex requirements to produce strategic diagrams, plans, and component designs before delegating implementation to **Developer** agents.
- **DevOps / SRE** (`cogni-ai-dev-ops`): Elite infrastructure and automation specialist. Focuses on CI/CD pipeline precision, infrastructure-as-code (IaC) scaling, and mitigating deployment blockers. Collaborates tangentially with Architects for cloud topology and supports Developers by ensuring resilient, zero-downtime integration and delivery.
- **Git Ops** (`cogni-ai-git-ops`): Autonomous version control specialist. Dedicated to safe repository management, complex rebasing, history rewriting, and atomic commit structuring without relying on remote platform workflows.
- **GitHub Ops** (`cogni-ai-github-ops`): Autonomous platform operations specialist. Focuses strictly on GitHub CLI/API interactions to manage pull requests, issues, actions, and Agentic Workflows (gh-aw) efficiently and securely.
- **Tester** (`cogni-ai-tester`): Elite test engineering kernel targeting software correctness. Prevents regressions by enforcing true behavioral logic coverage over superficial vanity metrics and strictly enforcing Test-Driven Development (TDD) mechanisms.

## What's Included: Commands (Slash Commands)

Slash commands are invoked via `/agent:skill` in the Copilot CLI or VS Code Chat.

| Command | Description |
| --- | --- |
| `/cogni-ai-coder:coding` | Load the coding skill -- workflow for implementing code from clear specifications with precision, syntax accuracy, and convention compliance |
| `/cogni-ai-coder:critical-thinking` | Load the critical-thinking skill -- a cognitive framework for deep analytical reasoning, deconstructing assumptions, applying Socratic questioning, and performing adversarial red-teaming to solve complex problems |
| `/cogni-ai-developer:development` | Load the development skill -- full-cycle software development workflow from requirements and system design through deployment, monitoring, and iteration |
| `/cogni-ai-developer:tdd` | Load the tdd skill -- commands, step-by-step procedures, and mechanical execution for test engineering, testability audits, and the TDD lifecycle |
| `/cogni-ai-developer:npm-cli` | Load the npm-cli skill -- reference and index of documentation pages for npm CLI commands and configurations |
| `/cogni-ai-developer:bun-llms` | Load the bun-llms skill -- reference and APIs for retrieving Bun documentation programmatically for LLMs |
| `/cogni-ai-tester:testing` | Load the testing skill -- elite autonomous test engineering and reliability kernel for proving correctness |
| `/cogni-ai-git-ops:git` | Load the git skill -- Guide for using git with non-interactive, safe operations. Includes references for reflog, bisecting, merges, rebase, cherry-picking, and recovery |
| `/cogni-ai-git-ops:git-docs` | Load the git-docs skill -- Official Git documentation index. Load this skill when searching for specific Git commands, configuration options, how-to guides, and technical references |
| `/cogni-ai-github-ops:gh` | Load the gh skill -- GitHub CLI (`gh`) operations for issues, PRs, and workflows |
| `/cogni-ai-github-ops:github` | Load the github skill -- Guidance on GitHub-specific features, pull requests viewing modes, and collaborative practices |
| `/cogni-ai-github-ops:github-actions` | Load the github-actions skill -- Diagnose GitHub Actions workflow failures by retrieving run statuses and logs |
| `/cogni-ai-github-ops:github-aw` | Load the github-aw skill -- Safely update existing GitHub Agentic Workflows (gh-aw) |
| `/cogni-ai-github-ops:dot-github` | Load the dot-github skill -- Standardize .github directory structure and agentic patterns |
| `/cogni-ai-github-ops:gh-api` | Load the gh-api skill -- Advanced GitHub API queries and mutations via REST or GraphQL |
| `/cogni-ai-github-ops:gh-issue` | Load the gh-issue skill -- GitHub issue management and operations |
| `/cogni-ai-github-ops:gh-pr` | Load the gh-pr skill -- GitHub pull request operations, reviews, and checks |
| `/cogni-ai-github-ops:gh-run` | Load the gh-run skill -- GitHub workflow run operations, jobs, logs, and attempts |
| `/cogni-ai-programmer:programming` | Load the programming skill -- expert workflow for solving technical problems with code: algorithm design, data structures, edge case handling, and code craftsmanship |
| `/cogni-ai-programmer:python` | Load the python skill -- expert Python language skill for writing, refactoring, and testing idiomatic Python 3 code (bundled with the programmer plugin) |
| `/cogni-ai-programmer:threejs-llms` | Load the threejs-llms skill -- expert guide for generating modern Three.js code using WebGL, WebGPU, and TSL (bundled with the programmer plugin) |
| `/cogni-ai-programmer:c-coding-standard` | Load the c-coding-standard skill -- C coding standard guidelines for names, formatting, documentation, complexity management, and miscellaneous resources |
| `/cogni-ai-programmer:cpp-coding-standard` | Load the cpp-coding-standard skill -- C++ coding standard guidelines for names, formatting, documentation, complexity management, miscellaneous resources, and object-oriented design |
| `/cogni-ai-architect:software-architecture` | Load the software-architecture skill -- expert-level workflow for software architecture design covering architectural styles, SOLID principles, design patterns, and ADRs |
| `/cogni-ai-dev-ops:devops` | Load the devops skill -- Core DevOps and Site Reliability Engineering workflow covering CI/CD, IaC, and observability |
| `/cogni-ai-dev-ops:apache-airflow-api` | Load the apache-airflow-api skill -- Execute Apache Airflow Stable REST API queries, manage DAGs, backfills, connections, variables, and assets |
| `/cogni-ai-dev-ops:apache-airflow-dags` | Load the apache-airflow-dags skill -- Expert-level guide for authoring Apache Airflow DAGs using the skeleton strategy and contract-driven logic |
| `/cogni-ai-dev-ops:astro-cli` | Load the astro-cli skill -- Expert-level guide for using the Astro CLI to manage Astronomer Airflow deployments and APIs |
| `/cogni-ai-dev-ops:astronomer-llms` | Load the astronomer-llms skill -- Read and navigate Astronomer documentation using llms.txt context |
| `/cogni-ai-dev-ops:ansible` | Load the ansible skill -- How to run and manage Ansible operations safely and prevent hangs |
| `/cogni-ai-dev-ops:molecule` | Load the molecule skill -- Molecule testing workflows for Ansible roles |
| `/cogni-ai-dev-ops:pulumi-cli` | Load the pulumi-cli skill -- Execute Pulumi CLI commands for stack management and infrastructure deployments |
| `/cogni-ai-dev-ops:docker` | Load the docker skill -- How to run, manage, and troubleshoot Docker containers, images, and networks safely |
