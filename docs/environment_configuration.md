# Environment Configuration

This guide provides instructions for configuring the NEAR AI environment, including setting up API keys, customizing agent behavior, and managing resources.

## API Key Setup

1. Login to your NEAR account:

```
nearai login
```

2. Verify your login status:

```  
nearai login status
```

3. The API key will be automatically configured after logging in.

## Customizing Agent Behavior

You can customize agent behavior by modifying the following settings:

- Model: Set the AI model to use
- Temperature: Control randomness of outputs  
- Max tokens: Limit response length

Example configuration in metadata.json:

```json
{
  "details": {
    "agent": {
      "defaults": {
        "model": "gpt-3.5-turbo",
        "model_temperature": 0.7,
        "model_max_tokens": 500
      }
    }
  }
}
```

## Managing Resources

### Vector Stores

Create a vector store:

```python
vector_store = env.create_vector_store(
  name="my_store",
  file_ids=["file1", "file2"],  
  chunking_strategy=ChunkingStrategy.AUTO
)
```

Query a vector store:

```python
results = env.query_vector_store(
  vector_store_id="store_id",
  query="search query"
)
```

### File Management  

Upload a file:

```python
file = env.upload_file(
  file_content="file contents",
  file_name="example.txt"
)
```

Read a file:

```python
content = env.read_file("example.txt")
```

## Environment Variables

Set environment variables to configure the runtime:

```python
env_vars = {
  "DEBUG": "true",
  "MAX_RETRIES": "3"
}
```

Pass these when initializing the environment.

## Tool Registration

Register custom tools:

```python
env.get_tool_registry().register_tool(my_custom_tool)
```

## Logging

Configure logging:

```python
env.add_system_log("Log message", logging.INFO)
```

This provides the core instructions for configuring the NEAR AI environment. Refer to the full documentation for additional options and advanced usage.