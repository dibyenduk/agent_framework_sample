# AgentFrameworkSample

Sample workspace for experimenting with **Microsoft Agent Framework** and **Azure AI Foundry Agents** using:
- a .NET console project (`src/AgentFrameworkSample.csproj`)
- a C# notebook with end-to-end scenarios (`src/AgentFrameworkFoundry.ipynb`)

## What this project demonstrates

The notebook contains practical examples for:
1. Basic agent creation and invocation
2. Streaming responses from an agent
3. Function/tool calling with local C# functions
4. MCP tool integration (GitHub Copilot MCP endpoint)

## Project structure

```text
AgentFrameworkSample.sln
README.md
src/
	AgentFrameworkSample.csproj
	AgentFrameworkFoundry.ipynb
```

## Prerequisites

- Windows/macOS/Linux with **.NET SDK 10 (preview)** or newer that supports `net10.0`
- Visual Studio Code
- VS Code extensions:
	- .NET / C# support
	- Polyglot Notebooks (for `.ipynb` with C#)
- Access to an Azure AI Foundry project and model deployment (example uses `gpt-4o`)

## NuGet packages used

Defined in `src/AgentFrameworkSample.csproj`:
- `Azure.AI.Projects` (`1.2.0-beta.5`)
- `Azure.AI.OpenAI` (`2.8.0-beta.1`)
- `Microsoft.Agents.AI` (`1.0.0-rc1`)
- `Microsoft.Agents.AI.AzureAI` (`1.0.0-rc1`)
- `Microsoft.Agents.AI.Workflows` (`1.0.0-rc1`)
- `Azure.Core` (`1.50.0`)
- `Azure.Identity` (`1.18.0-beta.2`)
- `ModelContextProtocol` (`0.4.1-preview.1`)

## Environment variables

Set these before running notebook or app code:

### PowerShell

```powershell
$env:AZURE_FOUNDRY_PROJECT_ENDPOINT = "https://<your-project>.services.ai.azure.com/api/projects/<your-project-name>"
$env:AZURE_FOUNDRY_PROJECT_API_KEY = "<your-api-key>"
$env:GITHUBTOKEN = "Bearer <your-github-token>"
```

> Note: Notebook error messages reference `GITHUB_TOKEN`, but code reads `GITHUBTOKEN`. Set `GITHUBTOKEN` unless you update the notebook.

## Running the notebook samples

1. Open `src/AgentFrameworkFoundry.ipynb` in VS Code.
2. Select a C# notebook kernel.
3. Run cells top-to-bottom.

The notebook scenarios include:
- Basic prompt/response agent flow
- Streaming output with `RunStreamingAsync`
- Local tools (`GetCurrentDateAndTime`, `GetCurrentTimeZone`)
- MCP tools from `https://api.githubcopilot.com/mcp`

## Building the .NET project

From repository root:

```powershell
dotnet restore
dotnet build .\AgentFrameworkSample.sln
```

## Important notes

- The notebook currently includes a hardcoded tenant ID in `DefaultAzureCredentialOptions`.
	- Replace it with your tenant, or remove explicit `TenantId` to use default identity behavior.
- This repository currently has project configuration and notebook samples; add your own `Program.cs` if you want a runnable console entry point.

## Next steps

- Add a console sample in `src/Program.cs` mirroring one notebook scenario.
- Move secrets to a secure local store (for example: user secrets, key vault, or environment manager).
- Pin package versions after validating compatibility with your target environment.
