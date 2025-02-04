# Netflix Movie Recommendation System Using ChromaDB

## Overview
The Netflix Movie Recommendation System demonstrates how **vector databases** and **sentence embeddings** can power intelligent search and recommendation systems. By leveraging **ChromaDB** to store and query embeddings generated using **Sentence Transformers**, this project enables real-time personalized movie recommendations based on user queries.

The system processes Netflix movie metadata, encodes movie descriptions into vector representations, and stores them in ChromaDB. Users can query the system with natural language inputs (e.g., by describing their movie preferences or searching for similar titles), and the system retrieves top matching movies efficiently.

## Features
- **Search by Title or Description**: Users can search by entering a movie title or describing the type of content they are interested in.
- **Real-time Recommendations**: The system returns a list of top-matching movies based on semantic similarity.
- **Custom Embedding Generation**: Movie descriptions are encoded using the **all-MiniLM-L6-v2** model from Sentence Transformers.
- **Scalable Storage**: Uses ChromaDB for efficient storage and retrieval of embeddings.

---

## Architecture
The system architecture is designed to process, store, and retrieve embeddings efficiently for real-time recommendations.

### **1. Data Preparation**
   - Dataset: Netflix movie metadata with fields such as `title`, `description`, `cast`, and `rating`.
   - The `description` field is preprocessed to generate vector embeddings.
   - Embeddings are stored in ChromaDB along with movie metadata.

### **2. Embedding Generation**
   - Embedding Model: Uses **Sentence Transformers** (`all-MiniLM-L6-v2`) to encode the movie descriptions into 384-dimensional vector embeddings.
   - The embeddings capture the semantic meaning of the descriptions for similarity-based searches.

### **3. Vector Database Integration**
   - **ChromaDB**:
     - Acts as a persistent vector store for embeddings.
     - Efficiently queries stored embeddings using cosine similarity.

### **4. Query Processing**
   - User queries are converted into embeddings using the same Sentence Transformer model.
   - The query embedding is compared to stored embeddings in ChromaDB to retrieve the top `n` matching results.

### **5. Recommendation Output**
   - Results are filtered and displayed in tabular format, showing the title, cast, rating, and description of the recommended movies.

---

## Technology Stack
### **Core Technologies**
1. **ChromaDB**:
   - A lightweight and high-performance vector database.
   - Enables efficient storage and retrieval of high-dimensional embeddings.

2. **Sentence Transformers**:
   - Pretrained model (`all-MiniLM-L6-v2`) for generating embeddings.
   - Captures the semantic meaning of text for similarity-based tasks.

3. **Pandas**:
   - Used for data manipulation and preprocessing.

4. **Python**:
   - Core programming language for building the pipeline.

### **Additional Libraries**
- `numpy`: For numerical operations.
- `openai` (optional): For potential integration with LLMs.
- `BeautifulSoup`: For web scraping (optional for dynamic dataset expansion).

---

## Dataset
The dataset used for this project includes 1,000 Netflix titles with the following columns:
- **Title**: The name of the movie/show.
- **Description**: A brief description of the content.
- **Cast**: List of actors/actresses.
- **Rating**: Parental guidance rating (e.g., TV-MA, PG-13).

Dataset Path: `data/netflix_titles_1000.csv`

---

## Installation
1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd netflix-recommendation-system
