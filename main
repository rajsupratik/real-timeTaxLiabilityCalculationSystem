import threading
import time

class Transaction:
    def __init__(self, amount):
        self.amount = amount
        self.timestamp = time.time()

class TaxNinjaSamurai:
    def __init__(self, tax_rate):
        self.tax_rate = tax_rate
        self.transactions = []
        self.total_income = 0.0
        self.lock = threading.Lock()

    def add_transaction(self, amount):
        with self.lock:
            new_transaction = Transaction(amount)
            self.transactions.append(new_transaction)
            self.total_income += amount
            self.calculate_tax_liability()

    def calculate_tax_liability(self):
        tax_liability = self.total_income * self.tax_rate
        current_time = time.strftime('%Y-%m-%d %H:%M:%S', time.localtime())

        print(f"Real-time Tax Liability as of {current_time}")
        print(f"Total Income: ${self.total_income:.2f}")
        print(f"Tax Rate: {self.tax_rate * 100:.2f}%")
        print(f"Tax Liability: ${tax_liability:.2f}\n")

def simulate_transactions(tax_ninja):
    # Simulate financial transactions over time
    for amount in [5000.0, 10000.0, 7500.0]:
        tax_ninja.add_transaction(amount)
        time.sleep(2)

def main():
    # Create a Tax Ninja Samurai with a tax rate of 25%
    tax_ninja = TaxNinjaSamurai(0.25)

    # Simulate transactions in a separate thread
    transaction_thread = threading.Thread(target=simulate_transactions, args=(tax_ninja,))
    transaction_thread.start()

    # Continue with other tasks in the main thread
    for _ in range(5):
        time.sleep(3)
        print("Main thread doing other tasks...")

    # Wait for the transaction thread to finish
    transaction_thread.join()

if __name__ == "__main__":
    main()
