# NEAR AI API Usage Guide

This guide provides instructions for using the NEAR AI API, including authentication, available endpoints, request/response formats, and example API calls.

## Authentication

To use the NEAR AI API, you need to authenticate your requests using an API key. Include your API key in the `Authorization` header of each request:

```
Authorization: Bearer YOUR_API_KEY
```

## Available Endpoints

The NEAR AI API provides the following main endpoints:

1. `/v1/threads` - Manage conversation threads
2. `/v1/threads/{thread_id}/messages` - Manage messages within threads
3. `/v1/threads/{thread_id}/runs` - Execute agent runs on threads

## Request/Response Formats

All requests and responses use JSON format. Here are some common request and response structures:

### Create Thread

Request:
```json
POST /v1/threads
{
  "messages": [
    {
      "role": "user",
      "content": "Hello, how can you help me today?"
    }
  ],
  "metadata": {
    "user_id": "12345"
  }
}
```

Response:
```json
{
  "id": "thread_abc123",
  "object": "thread",
  "created_at": 1698765432,
  "metadata": {
    "user_id": "12345"
  }
}
```

### Create Message

Request:
```json
POST /v1/threads/{thread_id}/messages
{
  "role": "user",
  "content": "What's the weather like today?"
}
```

Response:
```json
{
  "id": "msg_xyz789",
  "object": "message",
  "created_at": 1698765433,
  "thread_id": "thread_abc123",
  "role": "user",
  "content": "What's the weather like today?"
}
```

### Create Run

Request:
```json
POST /v1/threads/{thread_id}/runs
{
  "assistant_id": "asst_weather_bot",
  "instructions": "Provide a weather forecast for the user's location."
}
```

Response:
```json
{
  "id": "run_def456",
  "object": "run",
  "created_at": 1698765434,
  "thread_id": "thread_abc123",
  "assistant_id": "asst_weather_bot",
  "status": "queued"
}
```

## Example API Calls

### Using curl

Create a new thread:
```bash
curl -X POST https://api.near.ai/v1/threads \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"messages": [{"role": "user", "content": "Hello, how can you help me today?"}]}'
```

Create a message in a thread:
```bash
curl -X POST https://api.near.ai/v1/threads/thread_abc123/messages \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"role": "user", "content": "What's the weather like today?"}'
```

Create a run for a thread:
```bash
curl -X POST https://api.near.ai/v1/threads/thread_abc123/runs \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"assistant_id": "asst_weather_bot", "instructions": "Provide a weather forecast for the user's location."}'
```

### Using Python

```python
import requests

API_KEY = "YOUR_API_KEY"
BASE_URL = "https://api.near.ai/v1"

headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

# Create a new thread
thread_response = requests.post(f"{BASE_URL}/threads", headers=headers, json={
    "messages": [{"role": "user", "content": "Hello, how can you help me today?"}]
})
thread_id = thread_response.json()["id"]

# Create a message in the thread
message_response = requests.post(f"{BASE_URL}/threads/{thread_id}/messages", headers=headers, json={
    "role": "user",
    "content": "What's the weather like today?"
})

# Create a run for the thread
run_response = requests.post(f"{BASE_URL}/threads/{thread_id}/runs", headers=headers, json={
    "assistant_id": "asst_weather_bot",
    "instructions": "Provide a weather forecast for the user's location."
})

print(f"Run ID: {run_response.json()['id']}")
print(f"Run Status: {run_response.json()['status']}")
```

This guide covers the basics of using the NEAR AI API. For more detailed information on specific endpoints and features, please refer to the full API documentation.