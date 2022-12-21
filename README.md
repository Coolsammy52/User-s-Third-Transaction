# User-s-Third-Transaction
User's Third Transaction

SELECT 
  user_id,
  spend,
  transaction_date
FROM (
  SELECT
    user_id,
    spend,
    transaction_date,
    row_number() OVER (
      PARTITION BY user_id ORDER BY transaction_date) AS row_num
  FROM transactions) AS trans_num
  WHERE row_num = 3;
