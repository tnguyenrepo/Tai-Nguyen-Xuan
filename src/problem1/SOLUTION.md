My CLI command here:

grep '"symbol": "TSLA".*"side": "sell"' transaction-log.txt | sed -E 's/.*"order_id": "([^"]+)".*/https:\/\/example.com\/api\/\1/' > output.txt

![image](https://github.com/user-attachments/assets/6b58028d-0e8d-47e6-9f0d-b1e22956f102)

The result should be like this:
https://example.com/api/12346
https://example.com/api/12362
