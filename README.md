# 🧠 GenAI Supply Chain Assistant

A Generative AI-powered assistant for supply chain teams to improve decision-making around supplier delays, quality issues, and restocking needs.

---

## 📌 Problem Statement

Supply chain decision-making is often hindered by scattered data across logistics documents, spreadsheets, and dashboards. Identifying critical issues like high defect rates, delayed shipments, or low inventory levels requires manual effort and domain expertise.

This project aims to automate this process using a **hybrid AI agent** that combines:
- 📄 Document understanding
- 🔍 Semantic search with vector databases (FAISS)
- 🧠 LLM-based reasoning (Flan-T5)
- 📊 Business logic and rule-based filtering

---

## ✅ Features

- Parses and summarizes structured supply chain data as delivery memos
- Embeds logistics texts using `SentenceTransformers` and stores in FAISS
- Enables **natural language search** over product delivery summaries
- Applies **rules + LLM reasoning** to:
  - Detect risks (e.g., long lead time, high defect rate)
  - Recommend actions (e.g., Reorder, Flag for Delay, Monitor)
- Outputs structured tables and visual summaries of flagged products

---

## 🛠️ How It Works

### Step 1: Load Dataset
Uses a sample dataset of 100 supply chain records (from Kaggle). Each record includes:
- SKU, product type, stock levels, lead times, defect rates, etc.

### Step 2: Convert Rows to Text
Each row is transformed into a natural-language logistics memo to simulate document-style input.

### Step 3: Embedding + FAISS Index
- Embeds each memo using `all-MiniLM-L6-v2` (from `sentence-transformers`)
- Stores the embeddings in a FAISS vector index
- Enables fast similarity search with a natural language query

### Step 4: Rule-Based Risk Detection
- Extracts numeric values from top matching documents
- Flags products with:
  - Lead time > 20 days
  - Defect rate > 3.5%
  - Stock < 10 units

### Step 5: LLM Recommendation (Flan-T5)
- Uses `Flan-T5` to generate a single recommendation and justification per product
- Example output:


### Step 6: Output Summary
- Creates a structured report as a Pandas DataFrame
- Visualizes flagged SKUs and recommendations using `matplotlib` + `seaborn`

---

## 🎯 Example Output

| SKU   | Stock | Lead Time | Defect Rate | LLM Suggestion |
|-------|-------|-----------|-------------|----------------|
| SKU27 | 47    | 25        | 2.86%       | Reorder        |
| SKU29 | 45    | 16        | 3.87%       | Reorder        |
| SKU33 | 4     | 1         | 3.54%       | Reorder        |

---

## 📊 Visualization

![LLM Suggestions by Lead Time](link-to-screenshot-if-needed)

---

## 🔄 What's Next

This prototype can be extended to:
- Live production systems with real-time supplier data
- Integration with ERP dashboards or procurement tools
- More complex multi-agent workflows (e.g., escalation or budget-aware recommendations)
- Cost-benefit optimization for supplier switching

---

## 📁 Folder Structure

📦 GenAI-SupplyChain-Assistant
┣ 📄 README.md
┣ 📓 supply_chain_assistant.ipynb
┣ 📁 data
┃ ┗ supply_chain_data.csv

---

## 📚 Dependencies

- Python 3.8+
- pandas
- numpy
- sentence-transformers
- faiss-cpu
- transformers
- seaborn
- matplotlib

Install via:

```bash
pip install -r requirements.txt

💡 Author

Farzam Nazari
Machine Learning Engineer | Supply Chain Optimization Enthusiast


