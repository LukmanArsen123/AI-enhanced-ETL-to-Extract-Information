Objective
To design and implement an intelligent agent that automatically extracts structured financial facts and contextual comments from the Amazon 2024 Annual Report (PDF) using an AI-enhanced ETL (Extract–Transform–Load) pipeline.
Input:
Document: Amazon-2024-Annual-Report.pdf
Query Type: Natural language 
Method
1)	Intelligent Agent (Crawler + LLM):
A Python-based agent is developed to: Parse the PDF page-by-page using pdfplumber; Split extracted text into sentence-based chunks (max 10 sentences per chunk); Send each chunk to a large language model (qwen-turbo via Alibaba Cloud DashScope API) with a structured prompt ; 
Enforce strict JSON output containing: metric name, numeric value, unit, currency, topic, period, evidence snippet, grounded comment, and source page number ; 
The LLM is guided by a system prompt that emphasizes factual accuracy, numerical grounding, and non-speculative commentary.
Data Transformation:
Post-process LLM responses to:
Normalize units
Validate and standardize fields
Filter results by relevant topics if specified.
Concurrently extract tabular data using pdfplumber’s table detection for complementary structured content.
Output:
output.csv: Clean, structured list of AI-extracted financial facts with metadata.
tables.csv: Raw tables detected in the PDF (for validation or augmentation).

