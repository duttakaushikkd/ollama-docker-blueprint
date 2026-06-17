## `The 3-Step Setup` 🛠️� 

`1. Spin up the Ollama Container` 

```
   Run this command to start Ollama in the background.
```

```
   We map port 11434 and use a persistent volume so our models aren't wiped when the container stops.
   docker run -d -v ollama_storage:/root/.ollama -p 11434:11434 --name ollama ollama/ollama

   (Tip: If you have an NVIDIA GPU, make sure to install the NVIDIA Container Toolkit and pass the --gpus=all flag for lightning-fast speeds!)
```

`2. Pull Your Model (The only step that needs internet) Exec into your container and download your model of choice (e.g., Llama 3.2, Mistral, or Qwen): 
      
      docker exec -it ollama ollama run llama3.2` 

```
3. Turn off your Wi-Fi and Code!
   Ollama spins up a local REST API out of the box.
   You can now point your Python, Node.js, or LangChain code directly to your localhost endpoint.
   Here is a quick curl test you can run completely offline:

   curl http://localhost:11434/api/generate -d '{
        "model": "llama3.2",
        "prompt": "Why is the sky blue?",
        "stream": false
    }'
```

```
💡 The Takeaway: Open-source AI has reached a point where localized
infrastructure is no longer a luxury—it’s a viable architecture choice. Whether
you are building private RAG pipelines, internal dev tools, or testing code on a
flight, local LLMs are a game-changer.
```

