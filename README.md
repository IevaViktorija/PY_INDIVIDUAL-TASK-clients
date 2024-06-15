# PY_INDIVIDUAL-TASK-clients
clients, names, transactions, bought items

```py
class Client:
    number_of_clients = 0

    def __init__(self, client_id, name):
        self.client_id = client_id
        self.name = name
        self.transactions = []
        Client.number_of_clients += 1

    def add_transaction(self, transaction):
        self.transactions.append(transaction)

class Item:
    def __init__(self, item_id, name, price):
        self.item_id = item_id
        self.name = name
        self.price = price

    def display_info(self):
        formatted_price = f"EUR {self.price:,.2f}"
        return f"Item ID: {self.item_id}, Name: {self.name}, Price: {formatted_price}"

class Transaction:
    def __init__(self, transaction_id, client, items):
        self.transaction_id = transaction_id
        self.client = client
        self.items = items

    def display_details(self):
        item_list = "\n".join([item.display_info() for item in self.items])
        return f"Transaction ID: {self.transaction_id}\nItems:\n{item_list}"

clients = [
    Client(1, "Agnese"),
    Client(2, "Baiba"),
    Client(3, "Andris")
]

items = [
    Item(1, "BMW", 110000.00),
    Item(2, "Mercedes-Benz", 120000.00),
    Item(3, "Audi", 80000.00)
]

transactions = [
    Transaction(1, clients[0], [items[0], items[2]]),  
    Transaction(2, clients[1], [items[1]]),           
    Transaction(3, clients[2], [items[0]])            
]

clients[0].add_transaction(transactions[0])
clients[1].add_transaction(transactions[1])
clients[2].add_transaction(transactions[2])  

print("All Clients:")
for client in clients:
    print(f"Client ID: {client.client_id}, Name: \033[1m{client.name}\033[0m:")
    print("Transactions:")
    for transaction in client.transactions:
        print(transaction.display_details())
        print("Items Purchased:")
        for item in transaction.items:
            print(f"\t{item.display_info()}")
        print()
```
