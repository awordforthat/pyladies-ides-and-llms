# Ollama and VSCode

Disclaimer: I don't have very broad experience with LLMs. This is what works for me! 

## Ollama 
Ollama is a tool that lets you run LLMs locally.

![image](https://github.com/user-attachments/assets/d7f7a8c7-66d5-4200-8c4f-7ed447450ee3)


### Installation

- For Linux users, run `bash curl -fsSL https://ollama.com/install.sh | sh`
- For Windows users, download the binary from here: (https://ollama.com/download/OllamaSetup.exe)[https://ollama.com/download/OllamaSetup.exe]
- For Mac users, download the binary from here: (https://ollama.com/download/Ollama-darwin.zip)[https://ollama.com/download/Ollama-darwin.zip]

### Intro/Usage
You can use it just like many people use OpenAI's (ChatGPT)[https://openai.com/chatgpt/overview/] and just type questions at it:

![image](https://github.com/user-attachments/assets/03bb531e-1862-48e1-b58a-adb99737f1f8)
(Ignore the first line of the screen cap above)

In my experience, this is pretty slow on your average laptop. The free version of ChatGPT is faster and better. But if you need to use a model that is specifically trained on something, this is a way to host it locally. Also, data security!

### Switching models
As mentioned above, you can download and host many models on your local machine. Ollama makes it really easy to switch between them:

You can look at which models you have installed with `ollama list`:
![image](https://github.com/user-attachments/assets/da0d445a-3dd7-4c8d-9ff3-b21d7c2abd7c)

And choose one to run (after starting the ollama server) with `ollama run`:
![image](https://github.com/user-attachments/assets/7d9bc940-5f2d-4100-861e-bcb0b7592b3e)

### Adding models

1. You can see what models are available here: (https://ollama.com/library)[https://ollama.com/library]. There are plenty of tutorials out there on how to download models on the various platforms, so I won't cover that here.
2. Once you know what model you want, run `ollama pull <model_name>`: ![image](https://github.com/user-attachments/assets/b71e326e-dca8-4c84-a10f-c58325c36e78)

You can also add your own home-grown models, but I have not explored that option :)

I'll leave a reference to an Ollama cheat sheet (here)[https://secretdatascientist.com/ollama-cheatsheet/].



