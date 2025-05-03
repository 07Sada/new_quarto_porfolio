

## 1. Accessing Ollama in Free Google Colab Session

### Step-by-Step Setup
#### Enable Terminal Access in Colab
1. **Install `colab-xterm` package:**
    ```python
    !pip install colab-xterm
    ```
    
2. **Load the xterm extension:**
    ```python
    %load_ext colabxterm
    ```
    
3. **Open a terminal window:**
    ```python
    %xterm
    ```

#### Install and Run Ollama from Terminal

4. **In the terminal, run the following to install Ollama:**
    ```bash
    curl -fsSL https://ollama.com/install.sh | sh
    ```
    
5. **Then run the following command in terminal to pull the model from ollma model repository and host it on google colab:**
    ```bash
    ollama serve & ollma pull llama3.2
    ```

---
## 2. Creating Payload and Inference via Local URL
### Sample Payload Format
```python
MODEL = "llama3.2"
OLLAMA_API = "http://localhost:11434/api/chat"
HEADERS = {"Content-Type": "application/json"}

messages = [
    {"role": "user", "content": "Describe some of the business applications of Generative AI"}
]

payload = {
    "model": MODEL,
    "messages": messages,
    "stream": False
}
```

### Sending Payload via `requests`
```python
import requests
response = requests.post(OLLAMA_API, json=payload, headers=HEADERS)
print(response.json()["message"]["content"])
```

---

## 3. Using the Python `ollama` Library
### Installation (if needed)
```bash
!pip install ollama
```
### Inference Example
```python
import ollama
response = ollama.chat(model=MODEL, messages=messages)
print(response["message"]["content"])
```

---
## 4. Using the `openai` Library for Inference with Ollama
### Installation
```bash
!pip install openai
```

### Set API Key and Base URL (Ollama emulates OpenAI API)
```python
from openai import OpenAI

client = OpenAI(base_url="http://localhost:11434/v1", api_key="ollama")

response = client.chat.completions.create(
    model="llama3.2",
    messages=[{"role": "user", "content": "What is Artificial Intelligence?"}]
)

print(response.choices[0].message.content)
```

---
## 5. Pulling and Using DeepSeek Model
### Pull DeepSeek Model
```bash
!ollama pull deepseek-coder:6.7b-instruct
```
### Inference with DeepSeek Model
```python
response = requests.post("http://localhost:11434/api/generate", json={
    "model": "deepseek-coder:6.7b-instruct",
    "prompt": "Write a Python function to compute factorial."
})
print(response.json()["response"])
```

Or using Python `ollama` package:

```python
response = ollama.chat(model="deepseek-coder:6.7b-instruct", messages=[
    {"role": "user", "content": "Explain decorators in Python"}
])
print(response["message"]["content"])
```