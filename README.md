# Retrieval Augmented Generation with GPT and Langchain

Ever since ChatGPT came out, people have been building a personalized ChatGPT for their data. The desire and demand for this highlights an important limitation of ChatGPT - it doesn't know about YOUR data, and most people would find it more useful if it did. So how do you go about building a chatbot that knows about your data?

In this process, rather than just passing a user question directly to a language model, the system "retrieves" any documents that could be relevant in answering the question, and then passes those documents (along with the original question) to the language model for a "generation" step.

The main way most people - including us at LangChain - have been doing retrieval is by using semantic search. In this process, a numerical vector (an embedding) is calculated for all documents, and those vectors are then stored in a vector database (a database optimized for storing and querying vectors). Incoming queries are then vectorized as well, and the documents retrieved are those who are closest to the query in embedding space. 

![image-1](https://github.com/alexdni/retrieval_augmented_generation/assets/13934326/05b1a72d-8d18-496c-88c6-847b1d80d4f0)

This little proof of concept works in a way that is straight forward: 

Here's the [YouTube Video](https://youtu.be/9AXP7tCI9PI) where i got the initial repo from.

## Installation

Install [Langchain](https://github.com/hwchase17/langchain) and other required packages.
```
pip install langchain openai chromadb tiktoken unstructured
```
Modify `constants.py.default` to use your own [OpenAI API key](https://platform.openai.com/account/api-keys), and rename it to `constants.py`.

Place your own data into `data/data.txt`.

## Example usage
Test reading `data/data.txt` file. I used a news article about Threads - to ensure that we are demonstrating learning from the local file, not from the pre-generated LLM (OpenAI) knowledge.
```
> python chatgpt.py "what is Threads"
Threads is Meta's new social media platform released to rival Twitter.
```
Try this out. 
