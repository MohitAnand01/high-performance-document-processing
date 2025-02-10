#  High-Performance Document Processing

## Overview
This Colab Notebook is designed to efficiently process large PDF documents (100+ pages) using **parallel processing** and **memory-efficient techniques**. It also integrates a **LLM-based QA system**, allowing users to extract insights from the document with citations.

## Features
- **Efficient PDF Processing**: Extracts text, images, and tables from PDFs.
- **Parallel Execution**: Uses async/multiprocessing for rapid data extraction.
- **Memory Optimization**: Ensures low GPU/CPU usage.
- **LLM Integration**: Uses `Llama-2-7b-chat-hf` model for answering queries.
- **Vector-Based Retrieval**: FAISS-powered document indexing for fast lookups.

## Installation & Setup
### **1. Open the Colab Notebook**
Click the link to open the notebook in Google Colab.
```markdown
[Open in Colab](https://colab.research.google.com/)
```

### **2. Install Dependencies**
Run the following commands in Colab:
```python
!pip install transformers==4.31.0 tokenizers==0.13.3
!pip install einops==0.6.1 xformers==0.0.22.post7
!pip install langchain==0.1.4 faiss-gpu==1.7.1.post3
!pip install sentence_transformers accelerate
!pip install --upgrade torch torchvision torchaudio
!pip install bitsandbytes pymupdf
```

### **3. Upload Your PDF File**
Execute the following cell in Colab to upload a PDF:
```python
from google.colab import files
uploaded = files.upload()
```

### **4. Run the Processing Pipeline**
Once the file is uploaded, run the notebook cells to:
- Extract text, tables, and images.
- Convert content into a **vector-based FAISS store**.
- Use LLM to answer questions based on the extracted content.

## How to Query the LLM
After processing, you can ask questions from the PDF:
```python
query = "What is the main topic of the document?"
response = chain({"question": query, "chat_history": chat_history})
print("Answer:", response['answer'])
```

## Performance Goals
| Metric               | Target Value  | Achieved Value |
|----------------------|--------------|---------------|
| Processing Speed    | <30s for 100 pages | XXs |
| Memory Usage       | <1GB | XX MB |
| Extraction Accuracy | >95% | XX% |

## Output
- Extracted text is stored in a structured format.
- Images are saved separately and displayed.
- Tables are converted into DataFrames.
- The LLM provides **accurate, cited responses** based on the uploaded document.


### **Developed by: Mohit Anand**

