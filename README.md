## Overview

Building a basic rag pipeline  which

- **Index Documents:** Process and break documents into smaller, manageable chunks.
- **Store & Retrieve Information:** Save document embeddings in a vector database (using LanceDB) and search using similarity.
- **Generate Responses:** Use an AI model (via the OpenAI API) to provide concise answers based on the retrieved context.
- **Evaluate Responses:** Compare the generated response against expected answers and view the reasoning behind the evaluation.

Started with a file based db since this is just a test project.
  
## Installation

#### Install Dependencies

```bash
pip install -r requirements.txt
```

#### Configure Environment Variables

I used OpenAI for the LLM (you can modify/replace it in `invoke_ai.py` if you use other free APIs). 

You will also need a Cohere key for the re-ranking feature used in `src/impl/retriever.py`. 


#### Run the Full Pipeline

This command resets the datastore, indexes documents, and evaluates the model.

```bash
python main.py run
```

#### Add Documents

Index and embed documents. You can specify a file or directory path.

```bash
python main.py add -p "sample_data/source/"
```

#### Query the Database

Search for information using a query string.

```bash
python main.py query "What is the opening year of The Lagoon Breeze Hotel?"
```

#### Evaluate the Model

Use a JSON file (with question/answer pairs) to evaluate the response quality.

```bash
python main.py evaluate -f "sample_data/eval/sample_questions.json"
```
