**Characteristics**: Specialized for browser automation. Very small, cheap, fast. Good at following specific instructions.

**When to use**: Browser automation, E2E testing, UI interaction, screenshot capture.

**Instructions to give** (use Gherkin-like syntax):
```gherkin
GIVEN I am on page [URL]
WHEN I click [element description/selector]
AND I fill [field] with [value]
THEN I should see [expected element/text]
AND capture screenshot of [element/full page]
```

**Must specify**:
- What to do exactly
- How to do it (what to click, what page to visit, element selectors)
- What to capture (screenshots, evidence, text content)
- How to handle potential errors

**Required snippet** (include verbatim in your prompt to this subagent):
```
Use browser tools strictly follow the instructions given. If you encounter a blocking problem/error, don't try to solve it, immediately report it. Do not deviate from the given instructions. Save all screenshots and browser assets inside the ".playwright-mcp" directory in the project root.
```
