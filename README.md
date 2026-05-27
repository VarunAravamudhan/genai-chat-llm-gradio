## Development and Deployment of a 'Chat with LLM' Application Using the Gradio Blocks Framework

### AIM:
To design and deploy a "Chat with LLM" application by leveraging the Gradio Blocks UI framework to create an interactive interface for seamless user interaction with a large language model.

### PROBLEM STATEMENT:
Develop a user-friendly chatbot application using a large language model (LLM) to assist users with queries and generate conversational responses. The application should feature a responsive design, real-time text exchange, and customizable settings for response quality.

### DESIGN STEPS:

#### STEP 1: Set Up the Environment Install the necessary libraries (openai, gradio) and verify API access to the LLM. 

#### STEP 2: Create the Chat Functionality Write a function to interact with the LLM using OpenAI's API (or another preferred LLM provider).

#### STEP 3: Design the Gradio Blocks Interface Use Gradio Blocks to build a structured, multi-component UI with features like: A text box for user input. A chat history display. A clear button to reset the conversation. 

#### STEP 4:  Deploy and Test Host the Gradio app locally or on a server. Test with diverse inputs to ensure robust performance.

### PROGRAM:
```
import os, gradio as gr
from dotenv import load_dotenv
from text_generation import Client

load_dotenv()

client = Client(
    os.getenv("HF_API_FALCOM_BASE"),
    headers={"Authorization": f"Basic {os.getenv('HF_API_KEY')}"},
    timeout=120
)

def bot(msg, chat):
    reply = client.generate(msg, max_new_tokens=500).generated_text
    chat.append((msg, reply))
    return "", chat

with gr.Blocks() as demo:
    c = gr.Chatbot()
    t = gr.Textbox()

    t.submit(bot, [t, c], [t, c])

demo.launch()
```
### OUTPUT:

<img width="998" height="664" alt="image" src="https://github.com/user-attachments/assets/d6d21aec-b15b-4bb4-8c3b-6c1073ce782e" />


 
### RESULT:

The "Chat with LLM" application successfully enables interactive text-based communication with a large language model, offering a streamlined and visually appealing interface for users.
