# Professor Q&A Chatbot 🤖

A Streamlit-based chatbot application that provides interactive Q&A about professors using TRACE survey data. Built with RAG (Retrieval-Augmented Generation) architecture for accurate, context-aware responses.

## Features

- 📚 **Interactive Chat Interface**: Clean, modern chat UI powered by Streamlit
- 👩‍🏫 **Professor Selection**: Dropdown to select specific professors
- 🧠 **Conversational Memory**: Maintains chat history for contextual responses
- 🔍 **RAG Integration**: Connects to backend RAG API for intelligent responses
- ⚡ **Real-time Responses**: Animated typing effect for better user experience
- 📊 **Memory Insights**: Optional display of context summaries used for responses

## Prerequisites

- Python 3.8+
- Docker (for containerized deployment)
- RAG API service running and accessible
- Jenkins (for CI/CD pipeline)

## Installation

### Local Development

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   Create a `.env` file in the root directory:

   ```env
   RAG_API_BASE_URL=http://your-rag-api-url:port
   ```

4. **Run the application**
   ```bash
   streamlit run app.py
   ```

The app will be available at `http://localhost:8501`

### Docker Deployment

The repository includes Jenkinsfiles for automated Docker image building:

```bash
# Build Docker image
docker build -t professor-chatbot .

# Run container
docker run -p 8501:8501 --env-file .env professor-chatbot
```

## Usage

1. **Select Professor**: Use the dropdown to choose a professor
2. **Ask Questions**: Type your question about the selected professor
3. **View Responses**: Chat interface displays both your questions and bot responses
4. **Context Insights**: Expand the "Memory Summary" section to see what context was used

### Key Components

- **Streamlit Frontend**: Interactive chat interface with professor selection
- **Session State Management**: Maintains conversation history across interactions
- **RAG API Integration**: Communicates with backend service for intelligent responses
- **Error Handling**: Graceful handling of API failures and network issues

## CI/CD Pipeline

The repository includes Jenkins pipeline configuration for:

- Docker image building
- Container registry publishing

## Troubleshooting

### Common Issues

1. **"Failed to load professor list"**

   - Check if RAG API service is running
   - Verify `RAG_API_BASE_URL` in `.env` file
   - Ensure network connectivity to API service

2. **"Error: Connection timeout"**

   - Increase timeout value in `requests.post()` call
   - Check API service health and response times

3. **Empty responses**
   - Verify API response format matches expected structure
   - Check API logs for processing errors
