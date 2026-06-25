# MCP Directory -- Tool to MCP Status Lookup

This reference maps common business tools to their MCP/automation availability in Hermes Agent.

## How to Use

When building an Operating System Map, look up each tool here to determine its automation tier:

| Tier | Meaning | Implementation |
|------|---------|---------------|
| **Native** | Hermes has built-in support | Direct tool use |
| **MCP Available** | MCP server exists for this tool | Install via Hermes MCP config |
| **API Available** | REST/GraphQL API exists | Build a script or skill |
| **Manual** | No automation path | Manual bridge required |

## Common Tools

### Communication
| Tool | Tier | Notes |
|------|------|-------|
| Gmail | MCP | Google Workspace skill |
| Slack | MCP | Community MCP server |
| Discord | MCP | Built-in Discord tools |
| Telegram | Native | Hermes Telegram gateway |
| Teams | API | Microsoft Graph API |

### Project Management
| Tool | Tier | Notes |
|------|------|-------|
| Linear | MCP | Linear MCP server |
| Notion | MCP | Notion MCP server |
| GitHub | Native | gh CLI + Hermes skills |
| Jira | MCP | Community MCP server |
| Airtable | MCP | Airtable MCP server |

### Content & Marketing
| Tool | Tier | Notes |
|------|------|-------|
| YouTube | MCP | YouTube transcript tools |
| WordPress | API | REST API |
| Canva | MCP | Canva MCP server |
| Buffer/Hootsuite | API | REST APIs |

### CRM & Sales
| Tool | Tier | Notes |
|------|------|-------|
| HubSpot | MCP | Community MCP server |
| Salesforce | API | REST/SOAP API |
| Pipedrive | API | REST API |

### Data & Analytics
| Tool | Tier | Notes |
|------|------|-------|
| Google Sheets | MCP | Google Workspace skill |
| PostgreSQL | Native | Terminal psql |
| SQLite | Native | Terminal sqlite3 |
| Airtable | MCP | Airtable MCP server |

### AI & Automation
| Tool | Tier | Notes |
|------|------|-------|
| OpenAI API | Native | Hermes provider |
| Anthropic API | Native | Hermes provider |
| Hugging Face | MCP | HF Hub MCP server |
| ComfyUI | Native | ComfyUI skill |

## Finding New MCPs

Search for MCP servers:
- NPM: `@modelcontextprotocol/*`
- GitHub: "MCP server [tool-name]"
- Directories: mcpservers.org, glama.ai/mcp

## Adding MCPs to Hermes

```bash
# Via Hermes config
hermes config set mcp.servers.<name> '{"command":"...","args":[...]}'

# Or edit ~/.hermes/config.yaml directly
```
