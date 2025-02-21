grep '"symbol": "TSLA".*"side": "sell"' transaction-log.txt | sed -E 's/.*"order_id": "([^"]+)".*/https:\/\/example.com\/api\/\1/' > output.txt

