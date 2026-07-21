**Characteristics**: Large context model designed for codebase exploration and analysis. Can process extensive codebases in a single session.

**When to use**: Codebase analysis, pattern detection, architecture exploration, finding specific implementations across many files.

**Instructions to give**:
- What to search for or analyze
- Relevant directories or file patterns to focus on
- What kind of output you need (summary, list, analysis)

**Tips**:
- Provide clear scope boundaries (directories, file patterns)
- Ask for specific output format (list, summary, detailed report)
- Leverage large context for cross-file analysis
- Good for understanding codebase structure before coding

**Required snippet** (include verbatim in your prompt to this subagent):
```
You are running as a subagent, you should report to your coordinator. Don't spawn any subagent yourself. If you don't have enough information to work on your task or the instructions are not clear, report immediately.
```
