# Creating and Deploying a Simple Agent with NEAR AI

## 1. Set up your environment

1.1. Install NEAR AI CLI:
```
pip install nearai
```

1.2. Login to NEAR AI:
```
nearai login
```

## 2. Create a new agent

2.1. Run the agent creation command:
```
nearai agent create
```

2.2. Follow the interactive prompts to set up your agent:
- Enter a name for your agent
- Provide a description
- Choose a framework (e.g., "minimal")

## 3. Define agent behavior

3.1. Navigate to your agent's directory:
```
cd <your_agent_name>/1.0.0
```

3.2. Open `agent.py` in your preferred text editor.

3.3. Define your agent's behavior. Here's a simple example:

```python
def run(env, task):
    env.add_reply("Hello! I'm a simple agent. You said: " + task)
    env.add_reply("I can perform basic tasks. What would you like me to do?")

    user_input = env.request_user_input()
    env.add_reply("You requested: " + user_input)
    env.add_reply("I'll do my best to help!")
```

## 4. Using tools

4.1. Add a tool to your agent:

```python
def calculate_sum(a: int, b: int) -> int:
    return a + b

env.get_tool_registry().register_tool(calculate_sum)
```

4.2. Use the tool in your agent's behavior:

```python
def run(env, task):
    env.add_reply("I can calculate sums. Give me two numbers.")
    user_input = env.request_user_input()
    numbers = user_input.split()
    if len(numbers) == 2:
        result = env.get_tool_registry().call_tool("calculate_sum", int(numbers[0]), int(numbers[1]))
        env.add_reply(f"The sum is: {result}")
    else:
        env.add_reply("Please provide exactly two numbers.")
```

## 5. Interacting with the environment

5.1. Reading files:
```python
file_content = env.read_file("example.txt")
env.add_reply(f"Contents of example.txt: {file_content}")
```

5.2. Writing files:
```python
env.write_file("output.txt", "This is some output.")
env.add_reply("I've written some content to output.txt")
```

5.3. Executing commands:
```python
result = env.exec_command("ls -l")
env.add_reply(f"Command output: {result['stdout']}")
```

## 6. Deploy your agent

6.1. Upload your agent to the NEAR AI registry:
```
nearai agent upload
```

6.2. Confirm the upload details when prompted.

## 7. Test your deployed agent

7.1. Run your agent interactively:
```
nearai agent interactive
```

7.2. Select your agent from the list and interact with it.

## 8. Use your agent in applications

8.1. You can now use your agent's identifier (e.g., `your_namespace/your_agent_name/1.0.0`) in other NEAR AI applications or services.

Remember to update your agent's version and re-upload when you make changes to its behavior or capabilities.