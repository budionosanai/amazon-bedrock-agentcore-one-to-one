## 📘 Overview

This repository explains AI agent implementation for candidate screening use case that can compare and match between job requirements and CV, create result to the next step of the recruitment process, create interview or rejection email and create interview questions (if candidate have more than 7 of 10) using **Langgraph**, **CrewAI** and **Google Gemini** then deploy AI agent to **AgentCore Runtime** and monitoring AI agent using **AgentCore Observability** and **CloudWatch Logs**.

## 📁 Repository Structure

| File / Notebook | Description |
| :--- | :--- |
| `crewai/CrewaiWithoutAgentcore.ipynb` | Notebook of AI agent implementation using **Google Gemini** and **CrewAI**. |
| `crewai/CrewaiWithAgentcore.ipynb` | Notebook of AI agent implementation using **Google Gemini** and **CrewAI** + deploy to **AgentCore Runtime**. |
| `langgraph/LanggraphWithoutAgentcore.ipynb` | Notebook of AI agent implementation using **Google Gemini** and **Langgraph**. |
| `langgraph/LanggraphWithAgentcore.ipynb` | Notebook of AI agent implementation using **Google Gemini** and **Langgraph** + deploy to **AgentCore Runtime**. |
| `Always Winner CV.pdf` and `Sonny Wawwak CV.pdf` | Sample PDF file used in all notebooks. |

## ✅ Prerequisites

1. **Amazon Web Services (AWS)**: Access to AWS services, you can sign up/sign in [here.](https://console.aws.amazon.com)
- **Amazon S3** : upload file from local to S3 and download file from S3 to AI agent processes.
- **AWS Secret Manager** : store Gemini API Key and LLM inference in AI agent.
- **AgentCore Runtime**, **AgentCore Observability** and **CloudWatch Logs**.
- **AgentCore Starter Toolkit** : quickly configure and deploy AI agent with several AWS services such as **Amazon ECR**, **AWS CodeBuild**, and **AWS IAM**.

2. **CrewAI** and **Langgraph**: Access to create AI agent application.

3. **Google Gemini**: Access to Gemini API key, you can sign up/sign in [here.](https://aistudio.google.com) 

## 🚀 Getting Started

1. If you don't have AWS credentials (AWS secret key and AWS access key), click this [getting started](https://github.com/budionosanai/amazon-bedrock-agentcore-one-to-one?tab=readme-ov-file#-getting-started---first-time-only) but if you already have AWS credentials, skip this getting started and go to second step.

2. Open, run and following this notebooks :

| Notebook | Using |
| :--- | :--- |
| **[Langgraph without AgentCore](./langgraph/LanggraphWithoutAgentcore.ipynb)** | **Google Colab**. |
| **[Langgraph with AgentCore](./langgraph/LanggraphWithAgentcore.ipynb)** | **Google Colab**. |
| **[CrewAI without AgentCore](./crewai/CrewaiWithoutAgentcore.ipynb)** | **Google Colab**. |
| **[CrewAI with AgentCore](./crewai/CrewaiWithAgentcore.ipynb)** | **Google Colab**. |

3. **(OPTIONAL)** Delete **AgentCore Runtime** and **Amazon ECR** repository in Langgraph and CrewAI with AgentCore notebook with this code :

```
import boto3
region = "us-west-2"

agentcore_control = boto3.client(
    'bedrock-agentcore-control',
    region_name=region
)

ecr = boto3.client(
    'ecr',
    region_name=region
)

runtime_delete_response = agentcore_control.delete_agent_runtime(
    agentRuntimeId=launch_result.agent_id
)

response = ecr.delete_repository(
    repositoryName=launch_result.ecr_uri.split('/')[1],
    force=True
)
```

## ⚠️ Warning

**Ensure securely API keys such as AWS credentials and Gemini API key — DO NOT HARDCORE them in notebooks.**

## 📚 Resources

* [Amazon Bedrock AgentCore documentation](https://docs.aws.amazon.com/bedrock-agentcore/)
* [CrewAI documentation](https://docs.crewai.com/)
* [Langgraph documentation](https://docs.langchain.com/oss/python/langgraph/)
* [Google Gemini documentation](https://ai.google.dev/gemini-api/docs/)

## Tutorial Blog

* https://dev.to/budionosan/amazon-bedrock-agentcore-runtime-with-langgraph-crewai-and-google-gemini-57l5

## 🙏 Acknowledgments

**Amazon Web Services, Google Gemini, CrewAI, Langgraph and Google Colab**