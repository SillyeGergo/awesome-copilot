---
agent: 'agent'
description: 'Search for prompts in the awesome-copilot repository by keyword, title, or description and display matching results with installation links.'
tools: ['fetch', 'githubRepo', 'search']
---
# Search Awesome Copilot Prompts

Search for prompts in the [GitHub awesome-copilot repository](https://github.com/github/awesome-copilot/blob/main/docs/README.prompts.md) by keyword, title, or description. Returns a list of matching prompts with descriptions and installation links.

## Usage

Provide search keywords or describe what you're looking for:
- "dotnet" - Find all .NET related prompts
- "testing" - Find prompts related to testing
- "documentation" - Find documentation-related prompts
- "mcp server" - Find MCP server generation prompts

## Process

1. **Fetch Available Prompts**: Retrieve the complete list of prompts from [awesome-copilot README.prompts.md](https://github.com/github/awesome-copilot/blob/main/docs/README.prompts.md) using the `#fetch` tool
2. **Parse Search Query**: Analyze the user's search keywords or description
3. **Filter Results**: Match prompts against search criteria by:
   - Checking prompt titles for keyword matches
   - Checking prompt descriptions for keyword matches
   - Using case-insensitive matching
   - Supporting partial matches
4. **Rank Results**: Sort results by relevance (exact matches first, then partial matches)
5. **Format Output**: Display results in a structured table with:
   - Prompt title
   - Description
   - Installation links for VS Code and VS Code Insiders
   - Direct link to the prompt file in the repository

## Output Format

Display search results in a structured table:

| Prompt | Description | Install |
|--------|-------------|---------|
| [Prompt Name](https://github.com/github/awesome-copilot/blob/main/prompts/prompt-file.prompt.md) | Brief description of what the prompt does | [![VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF)](link) [![VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-Install-24bfa5)](link) |

**Showing X results for: [search query]**

If no results are found, suggest alternative search terms or recommend browsing the full list at [README.prompts.md](https://github.com/github/awesome-copilot/blob/main/docs/README.prompts.md).

## Requirements

- Use `fetch` or `githubRepo` tool to retrieve content from awesome-copilot repository
- Support case-insensitive search across prompt titles and descriptions
- Display results sorted by relevance
- Include installation links for both VS Code and VS Code Insiders
- Provide clear feedback when no results are found
- Limit results to top 10 most relevant matches if more than 10 results are found
- Include a note indicating if results are truncated

## Search Tips for Users

- Use specific keywords related to your technology stack (e.g., "python", "java", "dotnet")
- Search by task type (e.g., "testing", "documentation", "refactoring")
- Search by framework name (e.g., "spring boot", "react", "azure")
- Try both full words and abbreviations (e.g., "entity framework" or "ef")
- If too many results, add more specific keywords to narrow down
