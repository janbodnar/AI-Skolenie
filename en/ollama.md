# Ollama – Running large language models locally

**Ollama** is an open-source tool designed to run, manage, and interact with large  
language models (LLMs) directly on your computer. It enables developers,  
researchers, and hobbyists to deploy powerful AI models without relying on cloud  
services, giving them full control over data privacy and usage.

Ollama simplifies the complexity of running LLMs by automatically handling model  
downloads, memory management, and inference through a simple command-line  
interface. Whether you want to experiment with popular models like **LLaMA**,  
**Mistral**, or your own fine-tuned models, Ollama provides a seamless  
environment.

## Why developers use Ollama

| Advantage | Description |
|-----------|-------------|
| **Privacy and control** | Models run locally, data never leaves your computer |
| **Cost savings** | No monthly fees for cloud APIs |
| **Experimentation** | Easy testing of different models and configurations |
| **Offline access** | AI features available even without internet |
| **Customization** | Custom models created using Modelfiles |

---

## Supported platforms

Ollama is available for all major operating systems:

- **macOS** (Apple Silicon and Intel)
- **Windows** (Windows 10 and newer)
- **Linux** (Ubuntu, Debian, Fedora, and other distributions)

### Local vs. Cloud mode

Ollama is primarily designed for **local execution**, meaning LLMs run directly  
on your hardware. However, it also supports deployment in cloud environments  
when you need to scale performance or share access with a team. The REST API  
enables integration with any application, whether running locally or in the  
cloud.

## Installing Ollama

### System requirements

Before installation, ensure your system meets these requirements:

| Component | Requirement |
|-----------|-------------|
| **RAM** | Minimum 8 GB (16 GB+ recommended for larger models) |
| **Disk** | Minimum 10 GB for the application and models |
| **GPU** | Optional: NVIDIA GPU with CUDA support for faster inference |

### Installation on macOS

**Official installer:**
1. Download the installer from [ollama.com/download](https://ollama.com/download)
2. Open the downloaded `.dmg` file
3. Drag Ollama to the Applications folder
4. Launch Ollama from Applications

**Using Homebrew:**
```bash
brew install ollama
```

**Verify installation:**
```bash
ollama --version
```

### Installation on Windows

1. Download the installer from [ollama.com/download](https://ollama.com/download)
2. Run the `.exe` installer
3. Follow the installation wizard
4. Ollama will automatically start as a background service

**Verify installation (PowerShell or Command Prompt):**
```bash
ollama --version
```

### Installation on Linux

**Using the installation script:**
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

This script downloads and installs Ollama, sets up the service, and configures  
the necessary permissions.

**Start the service:**
```bash
systemctl start ollama
```

**Verify installation:**
```bash
ollama --version
```

> **Tip for Linux:** For GPU support, ensure you have NVIDIA drivers and the  
> CUDA toolkit installed. Ollama automatically detects and utilizes them.

---

## Basic Ollama commands

Ollama provides a simple CLI (Command Line Interface) for managing models and  
running inference.

| Command | Description |
|---------|-------------|
| `ollama run <model>` | Run a model interactively |
| `ollama list` | List all available models |
| `ollama pull <model>` | Download a model from the Ollama registry |
| `ollama ps` | Show running models and processes |
| `ollama stop <model>` | Stop a running model |
| `ollama create <model>` | Create a new model from a Modelfile |
| `ollama delete <model>` | Remove a model from local storage |

### Usage examples

**Run a model interactively:**
```bash
ollama run llama2
```

**Download a model from the registry:**
```bash
ollama pull mistral
```

**List installed models:**
```bash
ollama list
```

**Delete a model:**
```bash
ollama delete llama2
```

---

## Integration with Python

Ollama exposes a REST API at `http://localhost:11434`, which you can use for  
integration with Python applications.

### REST API Example

```python
import requests

response = requests.post(
    "http://localhost:11434/api/generate",
    json={"model": "llama2", "prompt": "Hello there!"}
)

for line in response.iter_lines():
    if line:
        print(line.decode("utf-8"))
```

The `/api/generate` endpoint accepts a JSON payload with the model name and  
prompt. The response is streamed line by line.

### Non-Streaming Request

```python
import requests
import json

response = requests.post(
    "http://localhost:11434/api/generate",
    json={
        "model": "llama2",
        "prompt": "What is the capital of France?",
        "stream": False
    }
)

data = response.json()
print(data["response"])
```

### Chat Endpoint Example

```python
import requests
import json

messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "What is the capital of France?"}
]

response = requests.post(
    "http://localhost:11434/api/chat",
    json={
        "model": "phi4-mini",
        "messages": messages,
        "stream": False
    }
)

data = response.json()
print(data["message"]["content"])
```

### Streaming Chat Response

```python
import requests
import json

messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "What is the capital of France? Answer in one sentence."}
]

response = requests.post(
    "http://localhost:11434/api/chat",
    json={
        "model": "phi4-mini",
        "messages": messages,
        "stream": True
    },
    stream=True
)

for line in response.iter_lines():
    if line:
        data = json.loads(line)
        if "message" in data and "content" in data["message"]:
            print(data["message"]["content"], end="", flush=True)
print()
```

### List available models via API

```python
import requests

response = requests.get("http://localhost:11434/api/tags")
data = response.json()

for model in data["models"]:
    print(f"Model: {model['name']}, Size: {model['size']}")
```

---

## Using the OpenAI library with Ollama

Ollama provides an OpenAI-compatible API endpoint at `http://localhost:11434/v1`.  
This allows you to use the official OpenAI Python library to interact with local  
models.

### Simple Chat

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:11434/v1",
    api_key="ollama"
)

response = client.chat.completions.create(
    model="llama2",
    messages=[
        {"role": "user", "content": "Hello there!"}
    ]
)

print(response.choices[0].message.content)
```

### Chat with System Prompt

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:11434/v1",
    api_key="ollama"
)

messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "What is the capital of France?"}
]

response = client.chat.completions.create(
    model="llama2",
    messages=messages
)

print(response.choices[0].message.content)
```

### Streaming Response

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:11434/v1",
    api_key="ollama"
)

stream = client.chat.completions.create(
    model="llama2",
    messages=[
        {"role": "user", "content": "Tell me a short story."}
    ],
    stream=True
)

for chunk in stream:
    if chunk.choices[0].delta.content is not None:
        print(chunk.choices[0].delta.content, end="", flush=True)
print()
```

### Temperature and Other Parameters

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:11434/v1",
    api_key="ollama"
)

response = client.chat.completions.create(
    model="llama2",
    messages=[
        {"role": "user", "content": "Write a creative poem about the moon."}
    ],
    temperature=0.9,
    max_tokens=200
)

print(response.choices[0].message.content)
```

| Parameter | Description |
|-----------|-------------|
| `temperature` | Controls randomness (0.2 = deterministic, 0.9 = creative) |
| `max_tokens` | Limits the response length |
| `top_p` | Alternative to temperature for sampling |

---

## Structured Output

Structured output is a mechanism that forces the AI model to provide responses  
in a specific, predictable format – typically JSON – rather than plain  
conversational text.

It ensures the output adheres to a strict **schema** (a blueprint of keys and  
data types), making the data immediately machine-readable for automation,  
databases, or application integration.

```python
from ollama import chat

text = """
Extract information about people mentioned in the following text. For each
person, provide their name, age, and city of residence in a structured JSON
format. John Doe is a software engineer living in New York. He
is 30 years old and enjoys hiking and photography. Jane Smith is a graphic
designer based in San Francisco. She is 28 years old and loves painting and
traveling."""

response = chat(
    model='ministral-3:3b',
    messages=[{'role': 'user', 'content': text}],
    format='json'
)

print(response.message.content)
```

This code demonstrates the use of structured output with a local LLM. Instead  
of a verbose paragraph, the `format='json'` parameter forces the model to  
return data that your code can immediately process.

## Summary

| Topic | Key points |
|-------|------------|
| **What is Ollama** | A tool for running LLM models locally |
| **Advantages** | Privacy, cost savings, offline access |
| **Installation** | Available for macOS, Windows, Linux |
| **Commands** | `run`, `pull`, `list`, `create`, `delete` |
| **Python integration** | REST API and OpenAI-compatible endpoint |
| **Structured output** | JSON format for automation |

## Questions & discussion
