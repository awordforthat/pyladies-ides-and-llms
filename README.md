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


## Integrating Ollama with VSCode

I use an extension called Continue to link VSCode and Ollama. You can think of Continue as a free, open source version of GitHub Copilot (https://github.com/features/copilot)[https://github.com/features/copilot]. You can install Continue from the VSCode extensions manager: ![image](https://github.com/user-attachments/assets/b3c96127-303b-4d8a-a1cd-18bdc342f1c0). 

Continue comes with a free trial of a few premium models, but we're standing up for the tired, the free, and the open source! We'll link one of the models we're running via Ollama to Continue so we can use it for things like code completion. 

Continue lets you control a few different interactions, and you can route queries for each to different models. That lets you match the model to the application it's best suited for. The tasks we'll talk about today are:
- code completion
- code embedding
- local chat

For this demo, I'm going to use llama 3 for local chat, deepseek for code completion, and nomic-embed-text for code embeddings. To accomplish this, first install and run the three models:

```
ollama run deepseek-coder:6.7b-base
ollama run llama3.2:latest
ollama pull nomic-embed-text
```

Then open up your Continue config:
![image](https://github.com/user-attachments/assets/72ce6f1b-fef9-47c6-b694-5e1878572e59) click the Continue icon here
and then the gear icon in the bottom of the side panel: 
![image](https://github.com/user-attachments/assets/17c0afaf-38a0-4364-8e57-c13ff32fa768)

This should bring up a JSON file that you can configure. Paste this in:
```
{
  "models": [
    {
      "title": "Llama 3.2",
      "provider": "ollama",
      "model": "llama3.2",
      "apiBase": "http://localhost:11434/"
    }
  ],
  "tabAutocompleteModel": {
    "title": "DeepSeek Coder 6.7B",
    "provider": "ollama",
    "model": "deepseek-coder:6.7b-base",
    "apiBase": "http://localhost:11434/"
  },
  "embeddingsProvider": {
    "provider": "ollama",
    "model": "nomic-embed-text"
  }
}
```

This maps each of the models to the type of prompts discussed above. 

Now open up a blank file. Type in a docstring for the function you'd like the LLM to write, like:
`# function that computes the first N digits of the fibonacci sequence`

Then depending on how powerful your computer is, we wait! The tab completion model should start to give you responses:
![image](https://github.com/user-attachments/assets/9ee1d68a-bbad-4552-99aa-cc6b97e5ab71)
![image](https://github.com/user-attachments/assets/f795d849-fa3c-438d-be01-df62aac85d2e)
![image](https://github.com/user-attachments/assets/725141d7-f1f7-4f88-902c-cd76a0c26410)
![image](https://github.com/user-attachments/assets/90743149-244d-4d9e-99b9-d71abb8be2be)

You can also highlight some code and ask llama3.2 to tell you about it:
![image](https://github.com/user-attachments/assets/308404ac-d98d-4196-a7fa-745bc668dc49)

![image](https://github.com/user-attachments/assets/c145ffe4-8825-4972-9c79-9ce52dc647e2)

There's lots more to configure here! But I haven't gone that far down the rabbit hole yet :). 
If you have questions on this readme, feel free to send me a message!









