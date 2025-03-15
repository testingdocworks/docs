# NEAR AI Registry Usage Guide

The NEAR AI registry system allows you to search for agents, upload custom agents, and manage agent versions. This guide will walk you through the main operations you can perform with the registry.

## Searching for Agents

To search for agents in the registry, use the `nearai registry list` command. This command allows you to filter and display available items in the registry.

```bash
nearai registry list [OPTIONS]
```

Options:
- `--namespace`: Filter by namespace
- `--category`: Filter by category (e.g., "agent", "model")
- `--tags`: Filter by tags (comma-separated)
- `--total`: Maximum number of items to display (default: 32)
- `--offset`: Number of items to skip (for pagination)
- `--show-all`: Include hidden entries
- `--show-latest-version`: Show only the latest version of each entry

Example:
```bash
nearai registry list --category agent --tags "summarization,text"
```

## Uploading Custom Agents

To upload a custom agent to the registry, use the `nearai registry upload` command. This command allows you to upload an agent from a local directory to the NEAR AI registry.

```bash
nearai registry upload [OPTIONS] [LOCAL_PATH]
```

Options:
- `--bump`: Automatically increment patch version if it already exists
- `--minor-bump`: Bump with minor version increment (e.g., 0.1.0 → 0.2.0)
- `--major-bump`: Bump with major version increment (e.g., 0.1.0 → 1.0.0)

Example:
```bash
nearai registry upload ./my_agent --bump
```

Before uploading, ensure your agent directory contains a `metadata.json` file with the required information.

## Managing Agent Versions

The NEAR AI registry system supports semantic versioning for agents. When uploading a new version of an existing agent, you can use the version bump options to automatically increment the version number.

1. Patch update (e.g., 1.0.0 → 1.0.1):
```bash
nearai registry upload ./my_agent --bump
```

2. Minor update (e.g., 1.0.0 → 1.1.0):
```bash
nearai registry upload ./my_agent --minor-bump
```

3. Major update (e.g., 1.0.0 → 2.0.0):
```bash
nearai registry upload ./my_agent --major-bump
```

## Downloading Agents

To download an agent from the registry, use the `nearai registry download` command.

```bash
nearai registry download ENTRY_LOCATION [OPTIONS]
```

Options:
- `--force`: Overwrite existing files if the agent is already downloaded

Example:
```bash
nearai registry download namespace/agent_name/1.0.0
```

## Viewing Agent Information

To view detailed information about a specific agent in the registry, use the `nearai registry info` command.

```bash
nearai registry info ENTRY_LOCATION
```

Example:
```bash
nearai registry info namespace/agent_name/1.0.0
```

This command will display the metadata associated with the specified agent, including its description, category, tags, and other relevant information.

Remember to log in with `nearai login` before performing operations that require authentication, such as uploading agents or accessing private entries in the registry.