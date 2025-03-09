# SQrL Chatbot built from scratch

A chatbot system leveraging singlestore's hybrid search and google api search to provide accurate responses from documentation sources.

## Project Overview

This repository provides an initial framework for a chatbot system that scrapes documentation, processes it into embeddings, and uses a hybrid search approach to deliver accurate answers. The system includes database persistence for maintaining conversation context and history.

## Components

The project consists of several key components:

1. **Documentation Scraping** - [s2_documentation_scraper.ipynb](/1.s2_documentation_scraper.ipynb)
   - Scrapes documentation from specified sources
   - Creates initial corpus of content for the chatbot knowledge base

2. **Content Cleaning** - [data_cleaning_md_content.ipynb](/2.data_cleaning_md_content.ipynb)
   - Processes the raw scraped markdown content
   - Normalizes and sanitizes text data for better processing

3. **Embedding Generation** - [gpu_embedding_chunker.ipynb](3.gpu_embedding_chunker.ipynb)
   - Utilizes GPU acceleration for embedding generation
   - Chunks content into appropriate sizes for vector representation

4. **Hybrid Search System** - [hybrid_Search_s2docs_all-MiniLM-L6-v2_cloudfunc.ipynb](4.hybrid_Search_s2docs_all-MiniLM-L6-v2_cloudfunc.ipynb)
   - Implements hybrid search combining traditional and semantic approaches
   - Uses the all-MiniLM-L6-v2 model for embedding generation
   - Deployed as cloud functions for scalability

5. **Database Persistence** - [sqrl_chatbot_db_persistence.ipynb](5.sqrl_chatbot_db_persistence.ipynb)
   - Manages conversation history and context
   - Stores embedded knowledge for quick retrieval

## Getting Started

### Prerequisites

- Python 3.10+
- Jupyter Notebook environment ( Works best within Singlestore portal )
- GPU container support (recommended for embedding generation)
- Access to cloud function service (for deployment)

### Installation

1. Clone this repository
2. Install required dependencies:

   ```bash

   pip install -r requirements.txt
   ```

3. Run the notebooks in the following order:
   - s2_documentation_scraper.ipynb
   - data_cleaning_md_content.ipynb
   - gpu_embedding_chunker.ipynb
   - hybrid_Search_s2docs_all-MiniLM-L6-v2_cloudfunc.ipynb
   - sqrl_chatbot_db_persistence.ipynb

## Usage

After completing the setup process, you can:

1. Use the chatbot locally through the provided interface
2. Deploy the chatbot as a service using the cloud function implementation
3. Integrate the chatbot into other applications using the API endpoints

## Architecture

```bash
Documentation Sources → Scraper → Content Cleaning → Embedding Generation → Vector Database
                                                                               ↓
                                      User Interface ← Response Generation ← Hybrid Search
```

## Future Improvements

- Implement user feedback mechanism to improve response quality
- Add support for more documentation sources
- Enhance context handling for multi-turn conversations
- Optimize embedding models for specific domains
