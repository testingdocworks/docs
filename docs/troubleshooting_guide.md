# NEAR AI Troubleshooting Guide

This guide addresses common issues users might encounter when using NEAR AI, including error messages, configuration problems, and performance issues.

## Table of Contents
1. [Authentication Issues](#authentication-issues)
2. [Configuration Problems](#configuration-problems)
3. [CLI Command Errors](#cli-command-errors)
4. [Agent Execution Issues](#agent-execution-issues)
5. [Performance Problems](#performance-problems)

## Authentication Issues

### Error: "Please login with `nearai login`"
- **Cause**: You are not authenticated or your authentication has expired.
- **Solution**: Run `nearai login` to authenticate your NEAR account.

### Error: "Auth data does not exist"
- **Cause**: Your authentication data is missing or corrupted.
- **Solution**: Run `nearai login` to re-authenticate your account.

## Configuration Problems

### Error: "Config file not found" or "Invalid config file"
- **Cause**: The NEAR AI configuration file is missing or corrupted.
- **Solution**: 
  1. Check if the config file exists in the default location (usually `~/.nearai/config.json`).
  2. If it's missing or corrupted, run `nearai config set key value` to recreate the config with proper values.

### Error: "Invalid API URL"
- **Cause**: The API URL in your configuration is incorrect.
- **Solution**: Run `nearai config set api_url https://correct-api-url.com` to set the correct API URL.

## CLI Command Errors

### Error: "Command not found" or "Unrecognized command"
- **Cause**: You might be using an outdated version of NEAR AI CLI or trying to use a non-existent command.
- **Solution**: 
  1. Update NEAR AI CLI: `pip install --upgrade nearai`
  2. Check the documentation for the correct command syntax.

### Error: "Invalid arguments" or "Missing required argument"
- **Cause**: Incorrect command syntax or missing required parameters.
- **Solution**: Review the command documentation and ensure all required arguments are provided.

## Agent Execution Issues

### Error: "Agent not found" or "Invalid agent ID"
- **Cause**: The specified agent does not exist or you don't have access to it.
- **Solution**: 
  1. Check if the agent ID is correct.
  2. Ensure you have the necessary permissions to access the agent.
  3. Use `nearai registry list` to see available agents.

### Error: "Execution timed out"
- **Cause**: The agent execution exceeded the maximum allowed time.
- **Solution**: 
  1. Check if your agent has any infinite loops or long-running tasks.
  2. Consider optimizing your agent's code for faster execution.
  3. If necessary, contact support to request a longer timeout for your use case.

## Performance Problems

### Slow CLI Response Times
- **Cause**: Network latency, server load, or local system resources.
- **Solution**: 
  1. Check your internet connection.
  2. Ensure you're using the latest version of NEAR AI CLI.
  3. Close unnecessary applications to free up system resources.

### High Memory Usage
- **Cause**: Large datasets or memory-intensive operations in your agents.
- **Solution**: 
  1. Optimize your agent code to use less memory.
  2. Consider using streaming or batching for large data processing.
  3. Upgrade to a higher-tier service plan if available.

If you encounter any issues not covered in this guide or need further assistance, please contact NEAR AI support or consult the official documentation for more detailed information.