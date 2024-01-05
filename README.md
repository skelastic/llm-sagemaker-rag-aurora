# Knowledge Base LLM powered Q&A application running on SageMaker with Aurora PostgreSQL for RAG (Retrieval Augmented Generation)

This project is a Knowledge Base LLM powered Q&A application running on SageMaker with Aurora PostgreSQL using [pgvector](https://github.com/pgvector/pgvector) for RAG (Retrieval Augmented Generation).

An application using RAG (Retrieval Augmented Generation) retrieves information most relevant to a user inpute/query from the a text based knowledge base by bundling it as context (vector embeddings) along with a user input/query request and then sends it to an LLM to receive a GenAI response.

In this project, Amazon Aurora Postgresql with pgvector is used for knowledge base.

### Workflow

1. Deploy the cdk stacks (For more information, see [here](./cdk_stacks/README.md)).
   - A SageMaker Studio in a VPC.
   - A SageMaker Endpoint for text generation.
   - A SageMaker Endpoint for generating embeddings.
   - An Amazon Aurora Postgresql cluster for storing embeddings.
2. Open SageMaker Studio and then open a new **System terminal** under SageMaker Studio Classic
3. Run the following commands on the terminal to clone the code repository for this project:

   ```
   git clone https://github.com/skelastic/llm-sagemaker-rag-aurora.git
   ```

4. Open the `data_ingestion_to_pgvector.ipynb` notebook.
5. Run Streamlit application

### References

  * [Leverage pgvector and Amazon Aurora PostgreSQL for Natural Language Processing, Chatbots and Sentiment Analysis (2023-07-13)](https://aws.amazon.com/blogs/database/leverage-pgvector-and-amazon-aurora-postgresql-for-natural-language-processing-chatbots-and-sentiment-analysis/)
  * [Building AI-powered search in PostgreSQL using Amazon SageMaker and pgvector (2023-05-03)](https://aws.amazon.com/blogs/database/building-ai-powered-search-in-postgresql-using-amazon-sagemaker-and-pgvector/)
  * [Build Streamlit apps in Amazon SageMaker Studio (2023-04-11)](https://aws.amazon.com/blogs/machine-learning/build-streamlit-apps-in-amazon-sagemaker-studio/)
  * [Quickly build high-accuracy Generative AI applications on enterprise data using Amazon Kendra, LangChain, and large language models (2023-05-03)](https://aws.amazon.com/blogs/machine-learning/quickly-build-high-accuracy-generative-ai-applications-on-enterprise-data-using-amazon-kendra-langchain-and-large-language-models/)
  * [Question answering using Retrieval Augmented Generation with foundation models in Amazon SageMaker JumpStart (2023-05-02)](https://aws.amazon.com/blogs/machine-learning/question-answering-using-retrieval-augmented-generation-with-foundation-models-in-amazon-sagemaker-jumpstart/)
  * [Use proprietary foundation models from Amazon SageMaker JumpStart in Amazon SageMaker Studio (2023-06-27)](https://aws.amazon.com/blogs/machine-learning/use-proprietary-foundation-models-from-amazon-sagemaker-jumpstart-in-amazon-sagemaker-studio/)
  * [LangChain](https://python.langchain.com/docs/get_started/introduction.html) - A framework for developing applications powered by language models.
  * [Streamlit](https://streamlit.io/) - A faster way to build and share data apps
  * [Pgvector changelog](https://github.com/pgvector/pgvector/blob/master/CHANGELOG.md#040-2023-01-11)
