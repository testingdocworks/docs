# Getting Started with NEAR AI

This guide will help you get up and running with NEAR AI, a distributed system for building, deploying, and managing AI agents. Follow these steps to install NEAR AI, understand its basic usage, and familiarize yourself with key concepts.

## Installation

### Requirements

- Python 3.11 (3.12+ currently not supported)
- Git
- Docker (for local agent testing)

### Steps

1. Install NEAR AI using pip:

```bash
python3 -m pip install nearai
```

2. Verify the installation:

```bash
nearai version
```

## Basic Usage

### Logging In

Before using NEAR AI, you need to log in with your NEAR Account. If you don't have one, create it at [NEAR Wallet](https://wallet.near.org/).

```bash
nearai login
```

### Creating an Agent

1. Create a new agent:

```bash
nearai agent create
```

2. Follow the interactive prompts to set up your agent.

### Running an Agent Locally

To test your agent locally:

```bash
nearai agent interactive
```

### Deploying an Agent

Deploy your agent to the NEAR AI Developer Hub:

```bash
nearai registry upload <path-to-agent>
```

## Key Concepts

1. **Agents**: AI-powered entities that can perform tasks and interact with users.

2. **Registry**: A central repository for storing and managing agents and models.

3. **Hub**: The NEAR AI Developer Hub where agents are deployed and can be accessed.

4. **Benchmarks**: Tools for evaluating agent performance.

5. **Fine-tuning**: Capability to customize language models for specific tasks.

6. **Workers**: Distributed job execution system for running agent tasks.

## Additional Resources

- [Official Documentation](https://docs.near.ai)
- [Agent Development Guide](https://docs.near.ai/agents/quickstart)
- [NEAR AI GitHub Repository](https://github.com/nearai/nearai)

For more detailed information on NEAR AI components and advanced usage, refer to the official documentation.