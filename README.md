# Customer Service Chatbot

## Overview

A customer service chatbot for an e-commerce platform built using OpenAI’s API. This project is part of Udacity’s Large Language Models (LLMs) and Retrieval Augmented Generation (RAG) course, within the [Generative AI Nanodegree program](https://www.udacity.com/course/generative-ai--nd608).

## Learning Objectives

- Initialize and configure the OpenAI API client
- Design effective system prompts that define bot behavior
- Maintain conversation history for contextual responses
- Classify customer intents using LLMs
- Generate natural, helpful customer service responses
- Implement conversation management features (reset, summary)

## Prerequisites

- Python 3.8 or higher
- OpenAI API key (Vocareum key is provided in the course)
- Basic understanding of APIs and Python classes

## Setup

### Install Dependencies

```bash
pip install openai
```

### Set Your API Key

First, create a file named `.env` in the `customer-service-bot` directory.

```env
OPENAI_API_KEY=your-key-here
```

### Alternative: Set the API key via environment variables

```bash
# For Vocareum keys (provided in course)
export OPENAI_API_KEY="voc-..."

# For standard OpenAI keys
export OPENAI_API_KEY="sk-..."
```

## Running the Code

```bash
python customer_service_bot.py
```

## Sample Interactions

Try these questions with your bot:

1. **Order Status**: "Where is my order? I placed it 3 days ago."
2. **Product Info**: "Do you have wireless headphones in stock?"
3. **Returns**: "What's your return policy?"
4. **Technical Support**: "I can't log into my account"
5. **General**: "Can you recommend a laptop for students?"

## Commands

While chatting with the bot:
- `quit` or `exit` - End the session
- `reset` - Start a new conversation (clears history)
- `summary` - Get a summary of the current conversation

## Key Concepts

### Conversation Context
LLMs are stateless - they don't remember previous messages unless you include them in each request. That's why maintaining conversation history is crucial.

### Temperature Parameter
- **0.0**: Deterministic, always picks the most likely token
- **0.7**: Balanced creativity and consistency (good for customer service)
- **1.0+**: More creative and varied (riskier for factual responses)

### Token Management
Each API call consumes tokens for:
- System prompt (every call)
- All conversation history (grows over time)
- New user message
- Generated response

Long conversations can get expensive! Consider truncating old history for production systems.

## Cost Considerations

**GPT-3.5-turbo pricing** (approximate):
- Input: $0.0005 per 1K tokens
- Output: $0.0015 per 1K tokens

A typical conversation turn:
- System prompt: ~100 tokens
- Conversation history: 200-1000 tokens (grows)
- User message: 10-50 tokens
- Response: 50-200 tokens

**Total**: ~$0.0002 - $0.002 per turn

## Learning Resources

- [OpenAI API Documentation](https://platform.openai.com/docs/api-reference)
- [Best Practices for Prompt Engineering](https://platform.openai.com/docs/guides/prompt-engineering)
- [Chat Completions Guide](https://platform.openai.com/docs/guides/chat)
