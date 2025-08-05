## ChatDB – Natural Language to SQL/NoSQL Query Interface

1. Overview
-----------
ChatDB is an innovative tool that bridges the gap between natural language processing (NLP) and database systems. 
It allows users to interact with SQL and NoSQL databases using plain English, without needing deep knowledge of query syntax.

Key Features:
- Upload CSV datasets and store them in either MySQL (SQL) or MongoDB (NoSQL).
- Generate sample queries dynamically based on dataset metadata.
- Translate natural language queries into SQL or NoSQL commands.
- Execute translated queries and display results directly in the browser.
- User-friendly web interface built with HTML, Bootstrap, and JavaScript.

Tech Stack:
- Backend: Python (Flask), SQLAlchemy, PyMongo, regex
- Databases: MySQL (SQL), MongoDB (NoSQL)
- Frontend: HTML, CSS (Bootstrap 5.3), JavaScript
- Data Handling: pandas

2. Project Structure
--------------------
app.py                -> Main Flask backend application  
utils.py              -> Utility functions for dataset handling, query generation, and translation  
data/                 -> Sample datasets (CSV files: sales.csv, products.csv, customers.csv)  
sql/                  -> SQL scripts (DDL/DML)  
templates/index.html  -> HTML front-end interface  
docs/                 -> Project reports (PDF, DOCX)  
requirements.txt      -> Python dependencies  

3. Installation & Setup
------------------------
Prerequisites:
- Python 3.x installed
- MySQL server running (for SQL mode)
- MongoDB server running (for NoSQL mode)

Steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/Chunduri-Aditya/ChatDB.git
   cd ChatDB
   ```

2. (Optional) Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate   # Mac/Linux
   venv\Scripts\activate      # Windows
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Place your CSV files in the `data` directory or the project root.

5. Run the app:
   ```bash
   python app.py
   ```

6. Open your browser and go to:
   ```
   http://127.0.0.1:5000/
   ```

4. Usage Instructions
---------------------
1) **Dataset Loading & DB Type Selection:**
   - Select "SQL" or "NoSQL" using the radio buttons.
   - Enter dataset filenames (comma-separated), e.g.:
     ```
     sales.csv,products.csv,customers.csv
     ```
   - Click **Load Dataset**.
   - The datasets will be pushed to the selected database and a sample preview will be shown.

2) **Sample Query Generation:**
   - In the "Enter Natural Language query" box, type:
     ```
     Give me sample query with group by
     ```
     OR
     ```
     Give me sample queries
     ```
   - A random sample query will be generated using dataset metadata.

3) **Natural Language to SQL/NoSQL Translation:**
   - Type your query in plain English, e.g.:
     ```
     Show me average quantity by sale date where sale date is after 2021-01-01
     ```
   - The system will:
     a) Parse your query using regex.  
     b) Translate it into SQL or MongoDB syntax.  
     c) Execute the query and display results in the browser.

5. Example Queries
------------------
**SQL:**
```
"Show me total sales by region"
→ SELECT region, SUM(sales) AS total_sales FROM sales GROUP BY region;
```

**MongoDB:**
```
"Show me average quantity for each product"
→ db.sales.aggregate([{ $group: { _id: "$product", avg_quantity: { $avg: "$quantity" }}}]);
```

6. Future Enhancements
----------------------
- Support for nested and advanced queries (subqueries, joins in MongoDB).
- Cloud deployment for scalability and remote access.
- Data visualization for query results.
- Enhanced NLP model for better query understanding.
