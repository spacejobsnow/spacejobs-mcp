# SpaceJobs.Now MCP server

A hosted, read-only [Model Context Protocol](https://modelcontextprotocol.io) server for space and aerospace job search.
It answers from the open roles at about 200 space companies and agencies (SpaceX, Blue Origin, Rocket Lab, NASA JPL,
Lockheed Martin Space, ESA, Airbus and many startups), read each night from each employer's own careers site by
[SpaceJobs.Now](https://spacejobs.now), with the pay each posting states and its citizenship or security clearance rules.

- Endpoint: `https://spacejobs.now/api/mcp` (Streamable HTTP)
- Authentication: none, no API key
- Data and API docs: https://spacejobs.now/data

## Tools

| Tool | What it answers |
|---|---|
| `search_space_jobs` | Open roles by keywords, kind of work, place, internship or entry level, remote, clearance and citizenship rules |
| `get_space_jobs_pay` | The salaries open roles post, by kind of work, state or employer |
| `get_space_jobs_market` | Open roles, roles posted in the last 7 days and the weekly rate of new postings, by kind of work, state and employer |
| `get_space_jobs_by_state` | Open roles and employers per US state, with their posted pay and cities |
| `list_space_employers` | The employers read, most open roles first, with where each hires |
| `get_space_employer` | One employer: what it does, where it hires, its open roles and posted pay |

## Add it to your client

Claude Desktop, Cursor, Cline, Windsurf and other clients that take a remote server:

```json
{
  "mcpServers": {
    "spacejobs-now": {
      "url": "https://spacejobs.now/api/mcp"
    }
  }
}
```

Clients that only run local commands can bridge it with `mcp-remote`:

```json
{
  "mcpServers": {
    "spacejobs-now": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://spacejobs.now/api/mcp"]
    }
  }
}
```

Mistral Le Chat: Connectors > Add connector > Custom MCP connector, URL `https://spacejobs.now/api/mcp`, no authentication.

## Example questions

- "Which space companies have Summer 2027 propulsion internships open in California?"
- "What do entry-level GNC engineers get paid at space companies right now?"
- "Space jobs in Colorado that don't need a security clearance"

Also listed in the [official MCP registry](https://registry.modelcontextprotocol.io) and on [Glama](https://glama.ai/mcp/servers).
Lists of space internships and new grad jobs, rebuilt daily: [Summer2027-Space-Internships](https://github.com/spacejobsnow/Summer2027-Space-Internships), [New-Grad-Space-Jobs](https://github.com/spacejobsnow/New-Grad-Space-Jobs).
