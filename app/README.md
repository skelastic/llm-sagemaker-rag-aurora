## Run the Streamlit application in Studio

SageMaker Studio provides a convenient platform to host the Streamlit web application. The following steps describes how to run the Streamlit app on SageMaker Studio.

1. Open Studio and then open a new **System terminal**.
2. Run the following commands on the terminal to clone the code repository and install the Python packages needed by the application:
   ```
   git clone https://github.com/skelastic/llm-sagemaker-rag-aurora.git
   cd llm-sagemaker-rag-aurora/app
   python -m venv .env
   source .env/bin/activate
   pip install -r requirements.txt
   ```
3. In the shell, set the following environment variables with the values that are available from the CloudFormation stack output.
   ```
   export AWS_REGION=us-west-2
   export PGVECTOR_SECRET_ID="INSERT_DB_SECRET_ID"
   export COLLECTION_NAME="INSERT_COLLECTION_NAME"
   export EMBEDDING_ENDPOINT_NAME="INSERT_EMBEDDING_ENDPOINT_NAME"
   export TEXT2TEXT_ENDPOINT_NAME="INSERT_TEXT2TEXT_ENDPOINT_NAME"
   ```
4. When the application runs successfully, you’ll see an output similar to the following (the IP addresses you will see will be different from the ones shown in this example). Note the port number (typically `8501`) from the output to use as part of the URL for app in the next step.
   ```
   sagemaker-user@studio$ streamlit run app.py

   Collecting usage statistics. To deactivate, set browser.gatherUsageStats to False.

   You can now view your Streamlit app in your browser.

   Network URL: http://169.255.255.2:8501
   External URL: http://52.4.240.77:8501
   ```
5. You can access the app in a new browser tab using a URL that is similar to your Studio domain URL. For example, if your Studio URL is `https://d-randomidentifier.studio.us-west-2.sagemaker.aws/jupyter/default/lab?` then the URL for your Streamlit app will be `https://d-randomidentifier.studio.us-west-2.sagemaker.aws/jupyter/default/proxy/8501/app` (notice that `lab` is replaced with `proxy/8501/app`). If the port number noted in the previous step is different from `8501` then use that instead of `8501` in the URL for the Streamlit app.

## References

  * [Leverage pgvector and Amazon Aurora PostgreSQL for Natural Language Processing, Chatbots and Sentiment Analysis](https://aws.amazon.com/blogs/database/leverage-pgvector-and-amazon-aurora-postgresql-for-natural-language-processing-chatbots-and-sentiment-analysis/)
  * [Building AI-powered search in PostgreSQL using Amazon SageMaker and pgvector](https://aws.amazon.com/blogs/database/building-ai-powered-search-in-postgresql-using-amazon-sagemaker-and-pgvector/)
  * [Use proprietary foundation models from Amazon SageMaker JumpStart in Amazon SageMaker Studio](https://aws.amazon.com/blogs/machine-learning/use-proprietary-foundation-models-from-amazon-sagemaker-jumpstart-in-amazon-sagemaker-studio/)
  * [Build Streamlit apps in Amazon SageMaker Studio ](https://aws.amazon.com/blogs/machine-learning/build-streamlit-apps-in-amazon-sagemaker-studio/)
  * [LangChain](https://python.langchain.com/docs/get_started/introduction.html) - A framework for developing applications powered by language models.
  * [Streamlit](https://streamlit.io/) - A faster way to build and share data apps
