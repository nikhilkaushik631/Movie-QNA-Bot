# Movie Bot Analysis Report

## Overview
The Movie Bot notebook creates a conversational agent that answers questions about movies and TV series using up-to-date information from web searches. It combines large language models with search capabilities to provide helpful responses.

## Technologies Used
- **Language Models**: 
  - Llama3 (70B) via Groq API
  - Gemini 2.0 Flash via Google's API
- **Frameworks**:
  - LangChain - for building AI applications
  - LangGraph - for creating a workflow of AI operations
- **Search Tool**:
  - Tavily Search API - for retrieving current information from the web

## Code Structure
The notebook is organized around a workflow with these main components:

1. **Setup & Configuration**: Imports libraries and sets up API credentials
2. **State Management**: Defines a `MovieQueryState` class to track information through the workflow
3. **Agent Nodes**: Creates specialized functions for each step of the process
4. **Workflow Definition**: Connects the agents into a directed graph
5. **Query Processing**: Handles user interactions and conversation history

## How It Works

1. **Query Validation**: First checks if the question is actually about movies/TV using Gemini
2. **Web Search**: Uses Tavily to search the web for relevant information
3. **Content Extraction**: Gemini selects and cleans the most relevant 1-2 paragraphs from search results
4. **Response Synthesis**: Llama3 creates a natural-sounding, comprehensive response
5. **Conversation Memory**: Tracks previous exchanges to maintain context

For follow-up questions, there's a special rewriting step that converts context-dependent questions (like "Who directed it?") into complete questions (like "Who directed The Godfather?").

### Agents Used
- **Web Search Agent**:  
  Uses the Tavily Search API to perform real‐time web searches for the user’s query, fetching top‐ranked pages and raw content snippets for downstream processing.

- **Content Extraction Agent**:  
  Leverages Gemini 2.0 Flash to parse the search results, identify the most relevant 1–2 paragraphs, clean out ads or boilerplate, and produce concise, fact‐focused text blocks.

- **Response Synthesis Agent**:  
  Calls Llama3 (70B) to take the cleaned content and conversation context, then craft a fluent, natural‐language response tailored to the user’s question style and intent.```

## Key Features

- **Contextual Awareness**: Maintains conversation history to understand follow-ups
- **Topic Filtering**: Only processes movie/TV related questions
- **Fresh Information**: Uses web search rather than relying on the LLM's built-in knowledge
- **Smart Response Generation**: Adapts response style based on question type (factual, plot, opinion, analysis)

## User Interface
The notebook includes a simple command-line interface where users can ask movie and tv series related questions


This approach combines the knowledge capabilities of large language models with real-time information from the web, creating a more accurate and helpful movie information assistant.
