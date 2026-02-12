# AI-RAG-DOCUMENT-ASSISTANT

## 📄 Intelligent Document Q&A System

An AI-powered Retrieval-Augmented Generation (RAG) assistant built on **n8n** that allows you to upload PDF documents and chat with them. The system processes PDFs, stores embeddings in Pinecone vector space, and uses LLMs to provide accurate answers based on your documents.

## 🚀 Features

- **📁 PDF Upload & Processing**: Upload PDF documents, automatically extract and chunk text
- **🧠 Vector Embeddings**: Cohere embeddings for semantic understanding
- **🎯 Pinecone Vector Storage**: Efficient similarity search and retrieval
- **💬 Intelligent Chat**: Meta Llama 3 8B Instruct via OpenRouter for contextual responses
- **🎨 Clean HTML Frontend**: Simple, responsive chat interface
- **⚡ n8n Workflow**: Fully automated, no-code backend logic

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| **Workflow Automation** | n8n |
| **Vector Database** | Pinecone |
| **Embeddings** | Cohere |
| **LLM** | Meta Llama 3 8B Instruct (via OpenRouter) |
| **Trigger** | Chat Node |
| **Frontend** | HTML, CSS, JavaScript |
| **File Processing** | PDF parsing, text chunking |

## 📋 Prerequisites

- [n8n](https://n8n.io/) instance (self-hosted or cloud)
- [Pinecone](https://www.pinecone.io/) account and API key
- [Cohere](https://cohere.com/) API key
- [OpenRouter](https://openrouter.ai/) API key
- Basic understanding of RAG architecture

## 🔧 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/AIMANTAHIR04/AI-RAG-DOCUMENT-ASSISSTANT.git
cd AI-RAG-DOCUMENT-ASSISSTANT
```

### 2. Import n8n Workflow
1. Open your n8n instance
2. Go to **Workflows** → **Import from File**
3. Upload the workflow JSON file (`My workflow.json`)
4. Click **Save** and **Activate**

### 3. Configure Credentials in n8n

Set up the following credentials:

- **Pinecone**:
  - API Key
  - Environment
  - Index Name

- **Cohere**:
  - API Key

- **OpenRouter**:
  - API Key
  - Model: `meta-llama/llama-3-8b-instruct`

### 4. Set Up Pinecone Index
Create a Pinecone index with:
- Dimension: `1024` (for Cohere embeddings)
- Metric: `cosine`
- Pod type: `starter` or higher

### 5. Frontend Setup
The HTML frontend (`index.html`) is ready to use:
- Open directly in browser
- Configure the webhook URL to point to your n8n webhook endpoint

## 📁 Workflow Structure

### **PDF Ingestion Pipeline:**
```
Chat Trigger (Upload) → PDF Processor → Text Chunker → Cohere Embeddings → Pinecone Upsert
```

### **Query Pipeline:**
```
Chat Trigger (Question) → Cohere Embeddings → Pinecone Similarity Search → Context Assembly → 
OpenRouter (Llama 3) → Response Formatting → Return to Chat
```

## 🎯 Usage

### Upload Documents:
1. Open the chat interface
2. Click on upload area or drag & drop PDF
3. System processes and indexes the document

### Ask Questions:
1. Type your question in the chat
2. System retrieves relevant context
3. Llama 3 generates accurate answer based on your documents
4. Response appears in the chat

## 🌐 Frontend Preview

The HTML interface features:
- Clean, modern chat UI
- File upload with drag & drop
- Real-time message streaming
- Responsive design (mobile-friendly)
- Typing indicators
- Message history

## 🔒 Environment Variables

Create `.env` file for local development:
```env
PINECONE_API_KEY=your_key
PINECONE_ENVIRONMENT=your_env
PINECONE_INDEX=your_index
COHERE_API_KEY=your_key
OPENROUTER_API_KEY=your_key
N8N_WEBHOOK_URL=your_webhook_url
```

## 🧪 Testing

1. **Upload Test**: Try uploading a sample PDF
2. **Query Test**: Ask questions about the uploaded content
3. **Accuracy Test**: Verify responses match document content
4. **Performance Test**: Check response times

## 🚨 Troubleshooting

| Issue | Solution |
|-------|----------|
| PDF not processing | Check file size, ensure PDF is readable |
| No embeddings | Verify Cohere API key and quota |
| No search results | Check Pinecone index dimension matches Cohere (768) |
| LLM not responding | Verify OpenRouter API key and credits |
| Webhook errors | Confirm n8n workflow is active and URL is correct |

## 📊 Performance Optimization

- **Chunk Size**: Adjust text chunk size in workflow (recommended: 500-1000 characters)
- **Top-K Retrieval**: Configure number of similar documents to fetch (default: 3-5)
- **Temperature**: Adjust LLM temperature (0.1-0.7 for factual answers)
- **Index Optimization**: Use appropriate Pinecone pod size for your document volume

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License.

## 👩‍💻 Author

**Aiman Tahir**
- GitHub: [@AIMANTAHIR04](https://github.com/AIMANTAHIR04)


## 🙏 Acknowledgments

- n8n for the amazing workflow automation platform
- Pinecone for vector database
- Cohere for embeddings
- OpenRouter for LLM access
- Meta for Llama 3

---

**⭐ If you found this project helpful, please consider giving it a star on GitHub!**
