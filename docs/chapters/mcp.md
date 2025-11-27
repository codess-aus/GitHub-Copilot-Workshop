# MCP (Model Context Protocol)

<div class="hero-container">
  <img src="../../assets/images/hero-mcp.svg" alt="Model Context Protocol - Extended AI Capabilities" class="hero-image">
</div>

The Model Context Protocol (MCP) is an open standard that enables AI assistants like GitHub Copilot to connect with external data sources and tools.

## What is MCP?

MCP provides a standardized way for AI models to:

- Access external data sources
- Interact with tools and services
- Maintain context across sessions
- Extend capabilities dynamically

Think of MCP as a "plugin system" for AI assistants.

## How MCP Works

```mermaid
graph LR
    A[GitHub Copilot] <-->|MCP Protocol| B[MCP Server]
    B <--> C[Database]
    B <--> D[API Services]
    B <--> E[File Systems]
    B <--> F[Custom Tools]
```

### Key Components

| Component | Description |
|-----------|-------------|
| **Host** | The AI application (Copilot) |
| **Server** | Provides resources and tools |
| **Client** | Connects host to servers |
| **Resources** | Data the AI can access |
| **Tools** | Actions the AI can perform |

## MCP Servers

### Available Servers

Common MCP servers include:

- **Database Servers**: PostgreSQL, MySQL, MongoDB
- **File System**: Local and remote file access
- **API Gateways**: REST and GraphQL APIs
- **Development Tools**: Git, Docker, Kubernetes
- **Cloud Services**: AWS, Azure, GCP

### Example: Database Server

```json
{
  "mcpServers": {
    "postgres": {
      "command": "mcp-server-postgres",
      "args": [
        "postgresql://user:pass@localhost/mydb"
      ]
    }
  }
}
```

With this configured, you can ask Copilot:

> "Show me all users who signed up last week"

Copilot can query the database directly!

## Setting Up MCP

### Configuration

Create a configuration file:

=== "VS Code"

    File: `.vscode/mcp.json`
    ```json
    {
      "servers": {
        "filesystem": {
          "command": "mcp-server-filesystem",
          "args": ["/path/to/project"]
        },
        "github": {
          "command": "mcp-server-github",
          "env": {
            "GITHUB_TOKEN": "${env:GITHUB_TOKEN}"
          }
        }
      }
    }
    ```

=== "Global Config"

    File: `~/.config/mcp/config.json`
    ```json
    {
      "servers": {
        "notes": {
          "command": "mcp-server-notes",
          "args": ["~/notes"]
        }
      }
    }
    ```

### Installing Servers

```bash
# Install from npm
npm install -g @modelcontextprotocol/server-filesystem
npm install -g @modelcontextprotocol/server-postgres

# Or use Docker
docker run -d modelcontextprotocol/server-github
```

## Using MCP with Copilot

### Accessing Resources

Once configured, ask Copilot about your resources:

> "What tables are in my database?"

> "Show me recent changes in the git log"

> "What files are in the src directory?"

### Using Tools

MCP tools enable actions:

> "Create a new database migration for adding an email column"

> "Run the test suite and show failed tests"

> "Deploy the latest version to staging"

## Creating Custom MCP Servers

### Server Structure

```python
from mcp import Server, Resource, Tool

server = Server("my-custom-server")

@server.resource("users")
async def get_users():
    """Get all users from the system"""
    return await fetch_users_from_api()

@server.tool("create_user")
async def create_user(name: str, email: str):
    """Create a new user"""
    return await api.create_user(name, email)

if __name__ == "__main__":
    server.run()
```

### Exposing Resources

```python
@server.resource("projects/{project_id}")
async def get_project(project_id: str):
    """Get project details by ID"""
    return {
        "id": project_id,
        "name": await db.get_project_name(project_id),
        "status": await db.get_project_status(project_id)
    }
```

### Implementing Tools

```python
@server.tool("deploy")
async def deploy_application(
    environment: str,
    version: str
) -> dict:
    """Deploy application to specified environment"""
    result = await deployment_service.deploy(
        env=environment,
        version=version
    )
    return {"status": "success", "url": result.url}
```

## MCP Best Practices

### Security

!!! warning "Security First"
    - Never expose sensitive credentials
    - Use environment variables for secrets
    - Implement proper authentication
    - Limit server permissions

### Resource Design

```python
# Good: Specific and scoped
@server.resource("users/{id}/orders")
async def get_user_orders(id: str):
    pass

# Avoid: Too broad
@server.resource("everything")
async def get_all_data():
    pass
```

### Error Handling

```python
@server.tool("risky_operation")
async def risky_operation():
    try:
        result = await perform_operation()
        return {"success": True, "data": result}
    except OperationError as e:
        return {"success": False, "error": str(e)}
```

## Common Use Cases

<div class="feature-list">
  <div class="feature-item">
    <span class="icon">🗄️</span>
    <div>
      <strong>Database Access</strong>
      <p>Query and modify databases naturally</p>
    </div>
  </div>
  <div class="feature-item">
    <span class="icon">📁</span>
    <div>
      <strong>File Management</strong>
      <p>Read, write, and organize files</p>
    </div>
  </div>
  <div class="feature-item">
    <span class="icon">🔧</span>
    <div>
      <strong>DevOps Tools</strong>
      <p>Deploy, monitor, and manage infrastructure</p>
    </div>
  </div>
  <div class="feature-item">
    <span class="icon">🔌</span>
    <div>
      <strong>API Integration</strong>
      <p>Connect to external services</p>
    </div>
  </div>
</div>

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Server won't start | Check command path and permissions |
| Connection timeout | Verify network settings |
| Auth failures | Check credentials and tokens |
| Missing resources | Ensure server is properly configured |

### Debugging

Enable verbose logging:

```json
{
  "servers": {
    "myserver": {
      "command": "mcp-server",
      "env": {
        "MCP_LOG_LEVEL": "debug"
      }
    }
  }
}
```

---

<div class="resource-links">
<h2>📚 Resources</h2>
<ul>
<li><a href="https://modelcontextprotocol.io/" target="_blank" rel="noopener">Model Context Protocol Official Site</a></li>
<li><a href="https://github.com/modelcontextprotocol" target="_blank" rel="noopener">MCP GitHub Organization</a></li>
<li><a href="https://docs.github.com/en/copilot" target="_blank" rel="noopener">GitHub Copilot Documentation</a></li>
<li><a href="https://github.blog/changelog/" target="_blank" rel="noopener">GitHub Changelog</a></li>
</ul>
</div>
