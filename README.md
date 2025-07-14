# AI-Driven Infrastructure Mission Framework

This project defines a unified strategy for enabling AI to autonomously manage complex system tasks,  
including network device operations, hardware management, server provisioning, and related areas where Infrastructure as Code (IaC) principles may apply.

With the **MCP framework**, we provide AI with structured specifications (`resources`), actionable instructions (`prompts`),  
and executable tools (`tools`). Combined with **pty-mcp-server**, the AI can interact with real systems  
through terminal interfaces—executing remote commands, applying IaC templates, and managing hardware or configuration states.  
This document outlines how these components work together to support a modular and scalable mission execution model.


## Strategy Overview

| Level                | Description                                              | Provided by             | MCP Component                         | Example |
|----------------------|----------------------------------------------------------|-------------------------|----------------------------------------|---------|
| **Strategy (Mission)** | What should be achieved (goal, context, constraints)     | User                    | `prompts`                | "Collect and summarize the number of HTTP 500 errors from all web server logs." |
| **Tactics**          | Which commands to run on which hosts                     | Determined autonomously by AI | `prompts`,`resources` | `ssh web01 "grep 500 /var/log/nginx/access.log"` |
| **Execution**        | Command execution, output handling, and response generation | AI + `pty-mcp-server`   | `tools`,`resources`           | AI interacts through virtual terminal prompts |


## MCP Components

| MCP Component | Description                                      | Relation to `mission`            |
|---------------|--------------------------------------------------|----------------------------------|
| `resources/`  | Required data, specifications, environment info  | Provides context and assumptions |
| `prompts/`    | Task instructions in natural or structured form  | Represents sub-tasks or specific operations derived from the mission |
| `tools/`      | Usable commands, execution interfaces            | Provides execution mechanisms    |



## Directory Structure
```
missions/
  └─ system_monitoring/
       ├─ pty-mcp-server.yaml
       ├─ logs/
       ├─ resources/
       │    ├─ resources-list.yaml     # List of resource files to be loaded
       │    ├─ mission.yaml            # Overall mission description (goal, constraints)
       │    ├─ hosts.yaml              # Server list
       │    ├─ log_paths.yaml          # Log file locations
       │    └─ specs.yaml              # Policy or system specs
       ├─ tools/
       │    ├─ tools-list.yaml         # List of executable tools for the AI
       │    └─ kubectl.yaml            # Kubernetes CLI access (optional)
       └─ prompts/
            ├─ prompts-list.yaml       # List of prompt files to be loaded
            ├─ disk_check.yaml         # Sub-mission: disk usage check
            └─ service_status.yaml     # Sub-mission: service status check
```

## mcp.json

```json
{
  "servers": {
    "system_monitoring-mcp-server": {
      "type": "stdio",
      "command": "pty-mcp-server",
      "args": ["-y", "/path/to/missions/system_monitoring/pty-mcp-server.yaml"]
    }
  }
}
```
