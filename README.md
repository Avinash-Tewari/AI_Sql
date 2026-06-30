<!-- <div align="center">

<img src="assets/banner.png" alt="AI SQL Banner" width="100%" />

<br/> -->

# 🧠 AI SQL — Natural Language to SQL Engine

### _Talk to your database like you talk to a human._

[![Python](https://img.shields.io/badge/Python-3.14+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--5.4--Mini-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)


<br/>

**AI SQL** is an intelligent, interactive SQL query engine that converts plain English questions into optimized PostgreSQL queries, executes them against a live Supabase database, and displays beautifully formatted results — all inside a Jupyter Notebook.

<br/>


</div>

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🗣️ Natural Language Queries
Ask questions in plain English — no SQL knowledge required. The AI understands context, relationships, and business logic.

### 🤖 GPT-5.4-Mini Powered
Leverages OpenAI's latest model for accurate, optimized SQL generation with minimal hallucination.

### 🎨 Rich Terminal Output
Beautiful formatted tables, syntax-highlighted SQL, and colorful panels using the Rich library.

</td>
<td width="50%">

### ⚡ Live Database Execution
Queries run against a real Supabase PostgreSQL database in real-time via secure RPC calls.

### 🏭 Synthetic Data Generator
Built-in Faker-powered data generator creates realistic e-commerce data (customers, products, orders, reviews).

### 🔄 Interactive REPL Mode
Continuous query loop — ask as many questions as you want without re-running cells.

</td>
</tr>
</table>

---

## 🏗️ Architecture

```mermaid
flowchart LR
    A["🗣️ Natural Language\nQuestion"] --> B["🤖 GPT-5.4-Mini\n(OpenAI API)"]
    B --> C["📝 Generated SQL\nQuery"]
    C --> D["⚡ Supabase RPC\n(execute_sql)"]
    D --> E["📊 PostgreSQL\nDatabase"]
    E --> F["🎨 Rich Formatted\nResults"]
    
    style A fill:#1a1a2e,stroke:#00d4ff,color:#fff
    style B fill:#1a1a2e,stroke:#a855f7,color:#fff
    style C fill:#1a1a2e,stroke:#22c55e,color:#fff
    style D fill:#1a1a2e,stroke:#3ecf8e,color:#fff
    style E fill:#1a1a2e,stroke:#f59e0b,color:#fff
    style F fill:#1a1a2e,stroke:#06b6d4,color:#fff
```

---

## 📊 Database Schema

The project uses a fully relational e-commerce database with 5 interconnected tables:

<img width="1228" height="860" alt="Screenshot 2026-06-30 173101" src="https://github.com/user-attachments/assets/75fa9a1c-362d-4c9a-81ce-ed4cc919d4b3" />




---

## 🧪 Example Queries

Here are some questions you can ask the AI SQL engine. Just call `ask()` with any natural language question:

<table>
<tr>
<th>🏷️ Category</th>
<th>💬 Question</th>
<th>🔍 What It Does</th>
</tr>
<tr>
<td><b>🛒 Sales</b></td>
<td><code>ask("Show me the top 5 customers who spent the most money")</code></td>
<td>Aggregates order totals per customer, ranks by spend</td>
</tr>
<tr>
<td><b>⭐ Reviews</b></td>
<td><code>ask("What is the average rating for each product category?")</code></td>
<td>Joins products + reviews, groups by category</td>
</tr>
<tr>
<td><b>📦 Inventory</b></td>
<td><code>ask("List all products that have never been ordered")</code></td>
<td>LEFT JOIN with NULL check to find unordered products</td>
</tr>
<tr>
<td><b>📈 Trends</b></td>
<td><code>ask("Show monthly revenue for the last 3 months")</code></td>
<td>Date truncation + aggregation with interval filtering</td>
</tr>
<tr>
<td><b>👤 Customers</b></td>
<td><code>ask("Which customers have placed more than 5 orders?")</code></td>
<td>HAVING clause on COUNT aggregation</td>
</tr>
<tr>
<td><b>🏪 Products</b></td>
<td><code>ask("What are the most expensive products in each category?")</code></td>
<td>Window functions or subquery with MAX</td>
</tr>
<tr>
<td><b>📊 Analytics</b></td>
<td><code>ask("Show the order status distribution")</code></td>
<td>GROUP BY with COUNT and percentage calculation</td>
</tr>
<tr>
<td><b>🔗 Complex</b></td>
<td><code>ask("Find customers who bought products they also reviewed")</code></td>
<td>Multi-table JOIN across orders, items, and reviews</td>
</tr>
</table>

---

## 📸 Screenshots

<img width="1649" height="931" alt="Screenshot 2026-06-30 172830" src="https://github.com/user-attachments/assets/d0de9ed0-cc68-4d5b-9da2-0aa1cebc2dfb" />
<img width="1234" height="926" alt="Screenshot 2026-06-30 172933" src="https://github.com/user-attachments/assets/dae81a11-c764-4add-9c9a-e70b7ad00d8b" />


<br/>

The notebook generates SQL from your question, executes it, and displays formatted results:

**Question:** _"Show me the top 5 customers who spent the most money"_

The AI generates a `SELECT` with `JOIN`, `GROUP BY`, `ORDER BY DESC`, and `LIMIT 5` — then displays results in a beautifully formatted Rich table with customer IDs, names, emails, and total spend amounts.





<br/>

The project includes a fully relational schema with 5 tables: `customers`, `products`, `orders`, `order_items`, and `reviews` — connected via foreign keys for a realistic e-commerce data model.

</details>

---

## 🧩 How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│                        NOTEBOOK CELLS                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Cell 1  │ 🔧 Initialize clients (Supabase + OpenAI)          │
│  Cell 2  │ 📊 Define database schema context                  │
│  Cell 3  │ 🏭 Generate & insert fake data (Faker)             │
│  Cell 4  │ ✅ Verify data with summary table                  │
│  Cell 5  │ 🤖 Define AI SQL engine functions                  │
│  Cell 6+ │ 💬 Run queries with ask("your question")           │
│  Last    │ 🔄 Interactive REPL loop                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Core Functions

| Function | Description |
|:---------|:------------|
| `nl_to_sql(question)` | Sends the question + schema to GPT-5.4-Mini, returns raw SQL |
| `run_query(sql)` | Executes SQL via Supabase `execute_sql` RPC function |
| `display_results(data)` | Renders results as a Rich formatted table |
| `ask(question)` | **Main function** — combines all three above into one call |

### AI Prompt Engineering

The system prompt includes:
- ✅ Full database schema with column types and constraints
- ✅ Valid enum values for `category` and `status` fields
- ✅ Rules for proper JOINs, aliases, and result limits
- ✅ Instructions to return **only** raw SQL (no markdown, no explanations)

---

## 📁 Project Structure

```
AI_Sql/
├── 📓 main.ipynb          # Main Jupyter notebook (all logic lives here)
├── 🐍 main.py             # Entry point placeholder
├── 📋 requirements.txt    # Python dependencies
├── ⚙️ pyproject.toml       # Project metadata
├── 🔒 .env                # API keys (not committed)
├── 🚫 .gitignore          # Git ignore rules
├── 📖 README.md           # You are here!

```

---

## 🔒 Security Notes

> [!IMPORTANT]
> The `execute_sql` RPC function uses `SECURITY DEFINER` — ensure your Supabase RLS policies are properly configured for production use.

---

## 🛠️ Tech Stack

<div align="center">

| Layer | Technology | Role |
|:------|:-----------|:-----|
| 🧠 AI | OpenAI GPT-5.4-Mini | Natural language → SQL translation |
| 🗄️ Database | Supabase (PostgreSQL) | Data storage + query execution |
| 📓 Interface | Jupyter Notebook | Interactive development environment |
| 🎨 Display | Rich + Pandas | Beautiful terminal output |
| 🏭 Data Gen | Faker | Synthetic e-commerce data |
| 🐍 Language | Python 3.14+ | Core runtime |

</div>

---
