# RAG Architecture

RAG (Retrieval Augmented Generation) is a process of giving context to an LLM. With this we can use enterprise content as gounding data for the model. A simple RAG architecture will contain the following:
- a datastore where the enterprise data is indexed 
- a query prompt where the user inserts the query 
- a retrieval process where the datastore is searched 
- conext argumentation where retrieved data is added to model input
- LLM generation where the LLM answers the querywithin the context of the retrieved enterprise data. 


By grounding the LLM in specific, relevant data, RAG helps reduce error responses and ensures they are factually correct. But there are also some issues. Most of the new LLMs are general purpose models that still have the tendency to give answers that are not grounded in the provided data. We need to find some ways to improve this behaviour. 