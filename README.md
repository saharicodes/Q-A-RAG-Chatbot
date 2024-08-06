# QA LLM RAG Chatbot With LangChain

The app is a comprehensive project that builds an LLM RAG Chatbot using LangChain and Neo4j. This chatbot is designed to answer questions about a synthetic hospital system by leveraging both structured and unstructured data. 

## Key Features:
1. The chatbot can answer questions about patient experiences based on their reviews. Patient reviews are embedded using OpenAI embedding models and stored in a Neo4j vector index.
2. The chatbot can answer questions about structured hospital system data stored in a Neo4j graph database.
3. The chatbot agent is served as an asynchronous FastAPI endpoint.
4. The chatbot features a user-friendly chat interface created with Streamlit.

## Project Structure
```
├── chatbot_api
├── chatbot_frontend
├── data
├── hospital_neo4j_etl
└── tests
```

## Setup

Create a `.env` file in the root directory and add the following environment variables:

```.env
OPENAI_API_KEY=<YOUR_OPENAI_API_KEY>

NEO4J_URI=<YOUR_NEO4J_URI>
NEO4J_USERNAME=<YOUR_NEO4J_USERNAME>
NEO4J_PASSWORD=<YOUR_NEO4J_PASSWORD>

HOSPITALS_CSV_PATH=data/hospitals.csv
PAYERS_CSV_PATH=data/payers.csv
PHYSICIANS_CSV_PATH=data/physicians.csv
PATIENTS_CSV_PATH=data/patients.csv
VISITS_CSV_PATH=https:data/visits.csv
REVIEWS_CSV_PATH=data/reviews.csv

HOSPITAL_AGENT_MODEL=gpt-3.5-turbo-1106
HOSPITAL_CYPHER_MODEL=gpt-3.5-turbo-1106
HOSPITAL_QA_MODEL=gpt-3.5-turbo-0125

CHATBOT_URL=http://host.docker.internal:8000/hospital-rag-agent
```

The chatbot uses OpenAI LLMs, so you'll need to create an OpenAI API key and store it as `OPENAI_API_KEY`. 

The three `NEO4J_` variables are used to connect to your Neo4j AuraDB instance. Follow the directions [here](https://neo4j.com/cloud/platform/aura-graph-database/?ref=docs-nav-get-started) to create a free instance.

Once you have a running Neo4j instance, and have filled out all the environment variables in `.env`, you can run the entire project with [Docker Compose](https://docs.docker.com/compose/). You can install Docker Compose by following [these directions](https://docs.docker.com/compose/install/).

Once you've filled in all of the environment variables, set up a Neo4j AuraDB instance, and installed Docker Compose, open a terminal and run:

```console
$ docker-compose up --build
```

After each container finishes building, you'll be able to access the chatbot API at `http://localhost:8000/docs` and the Streamlit app at `http://localhost:8501/`.
