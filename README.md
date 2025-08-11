# LangChain - Chat with Search

A Streamlit-powered chatbot that can search across multiple sources including ArXiv, Wikipedia, and DuckDuckGo to provide comprehensive answers to your questions.

## Features

- **Multi-source search**: Integrates ArXiv (academic papers), Wikipedia (general knowledge), and DuckDuckGo (web search)
- **Real-time streaming**: Uses Groq's LLaMA3 model with streaming responses
- **Interactive interface**: Clean Streamlit chat interface with callback handlers
- **Intelligent agent**: Uses LangChain's ReAct agent for reasoning and tool selection

## Prerequisites

- Python 3.8+
- Groq API key (get one at [console.groq.com](https://console.groq.com/))

## Installation

1. **Clone the repository** (or create a new directory):
   ```bash
   mkdir Search_Engine_Gen_Ai_App
   cd Search_Engine_Gen_Ai_App
   ```

2. **Install required packages**:
   ```bash
   pip install streamlit langchain-groq langchain-community python-dotenv
   ```

3. **Create the main file**:
   Save the provided code as `app.py`

## Setup

### Option 1: Environment Variables (Recommended)
1. Create a `.env` file in your project directory:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

### Option 2: Manual Input
- Leave the `.env` file empty and enter your API key directly in the Streamlit sidebar

## Usage

1. **Run the application**:
   ```bash
   streamlit run app.py
   ```

2. **Enter your API key** in the sidebar (if not using environment variables)

3. **Start chatting**! Ask questions like:
   - "What is machine learning?"
   - "Find recent research on quantum computing"
   - "What happened in the news today?"
   - "Explain photosynthesis"

## How it Works

The chatbot uses a **ReAct agent** that can:

1. **Think**: Analyzes your question and decides which tools to use
2. **Act**: Searches appropriate sources (ArXiv, Wikipedia, or web)
3. **Observe**: Processes the search results
4. **Respond**: Provides a comprehensive answer based on found information

### Available Tools

- **ArXiv**: Searches academic papers and research publications
- **Wikipedia**: Provides general knowledge and encyclopedic information  
- **DuckDuckGo**: Performs web searches for current information

## Configuration

You can customize the following in the code:

```python
# Modify search result limits
arxiv_wrapper = ArxivAPIWrapper(top_k_results=1, doc_content_chars_max=200)
api_wrapper = WikipediaAPIWrapper(top_k_results=1, doc_content_chars_max=200)

# Change the model
llm = ChatGroq(groq_api_key=api_key, model_name="Llama3-8b-8192", streaming=True)
```

## Troubleshooting

### Common Issues

1. **API Key Error**: Make sure your Groq API key is valid and has sufficient credits

2. **Import Errors**: Install missing packages:
   ```bash
   pip install --upgrade langchain langchain-community langchain-groq
   ```

3. **Search Errors**: Some searches might fail due to network issues or API limits

### Dependencies

```
streamlit>=1.28.0
langchain-groq>=0.1.0
langchain-community>=0.0.20
python-dotenv>=1.0.0
langchain>=0.1.0
```

## Example Queries

- **Research**: "What are the latest developments in artificial intelligence?"
- **General Knowledge**: "Explain the theory of relativity"
- **Current Events**: "What's happening with climate change?"
- **Technical**: "How does blockchain technology work?"

## File Structure

```
Search_Engine_Gen_Ai_App/
├── app.py             
├── .env                
├── requirements.txt    
└── README.md          
```

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.


**Note**: This chatbot requires an internet connection for searching and API access. Make sure to keep your API keys secure and never commit them to version control.