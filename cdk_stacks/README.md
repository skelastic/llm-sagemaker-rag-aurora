
# RAG Application CDK

![rag_with_pgvector_arch](./rag_with_pgvector_arch.svg)

The `cdk.json` file tells the CDK Toolkit how to execute your app.

This project is set up like a standard Python project.  The initialization
process also creates a virtualenv within this project, stored under the `.venv`
directory.  To create the virtualenv it assumes that there is a `python3`
(or `python` for Windows) executable in your path with access to the `venv`
package. If for any reason the automatic creation of the virtualenv fails,
you can create the virtualenv manually.

To manually create a virtualenv on MacOS and Linux:

```
$ python3 -m venv .venv
```

After the init process completes and the virtualenv is created, you can use the following
step to activate your virtualenv.

```
$ source .venv/bin/activate
```

Once the virtualenv is activated, you can install the required dependencies.

```
(.venv) $ pip install -r requirements.txt
```

To add additional dependencies, for example other CDK libraries, just add
them to your `setup.py` file and rerun the `pip install -r requirements.txt`
command.


Now this point you can now synthesize the CloudFormation template for this code.

```
(.venv) $ cdk bootstrap --profile AWS-1234567890123
(.venv) $ npx cdk deploy --profile AWS-1234567890123 --all
```

Or, we can provision each CDK stack one at a time like this:

#### Step 1: List all CDK Stacks

```
(.venv) $ cdk list
RAGVpcStack
RAGSageMakerStudioStack
RAGPgVectorStack
EmbeddingEndpointStack
LLMEndpointStack
```

#### Step 2: Create Aurora Postgresql cluster

```
(.venv) $ cdk deploy --require-approval never RAGVpcStack RAGPgVectorStack
```

#### Step 3: Create SageMaker Studio

```
(.venv) $ cdk deploy --require-approval never RAGSageMakerStudioStack
```

#### Step 4: Deploy LLM Embedding Endpoint

```
(.venv) $ cdk deploy --require-approval never EmbeddingEndpointStack
```

#### Step 5: Deploy Text Generation LLM Endpoint

```
(.venv) $ cdk deploy --require-approval never LLMEndpointStack
```

**Once all CDK stacks have been successfully created, proceed with the remaining steps of the [overall workflow](../README.md#overall-workflow).**


## Clean Up

Delete the CloudFormation stacks by running the below command.

```
(.venv) $ cdk destroy --all
```

## Useful commands

 * `cdk ls`          list all stacks in the app
 * `cdk synth`       emits the synthesized CloudFormation template
 * `cdk deploy`      deploy this stack to your default AWS account/region
 * `cdk diff`        compare deployed stack with current state
 * `cdk docs`        open CDK documentation