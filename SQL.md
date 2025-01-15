## Exploring a New Database and Finding the latset Transaction

### SQL Query to Find Transactions from the Last 2 Days

When connecting to a new database, it’s essential to get familiarize with its structure and data. If the task is to find all transactions from the last 2 days, here’s a professional approach:

1. **Understand the Schema**:
   - Use commands like `SHOW TABLES;` or `SELECT table_name FROM information_schema.tables WHERE table_schema = 'main_database';` to identify the available tables.
   - Investigate relevant columns using `DESCRIBE table_name;` or querying `information_schema.columns`.

2. **Query Transactions**:
   Assuming the table storing transactions is called `transactions` and it has a `transaction_date` column:

   ```sql
   SELECT *
   FROM transactions
   WHERE transaction_date >= DATE(NOW() - INTERVAL 2 DAY);
   ```
   If  column stores timestamps, use this:
   
   ```sql
   SELECT *
   FROM transactions
   WHERE transaction_date >= DATE(NOW() - INTERVAL 2 DAY) 
     AND transaction_date < NOW();
   ```
   
This query retrieves all rows where the transaction date is within the last 48 hours.

