import math

class Calculator:
    def add(self, a, b):
        return a + b

    def subtract(self, a, b):
        return a - b

    def multiply(self, a, b):
        return a * b

    def divide(self, a, b):
        return "Error: Division by zero" if b == 0 else a / b

    def power(self, a):
        return a ** 2

    def square_root(self, a):
        return "Error: Cannot take square root of a negative number" if a < 0 else math.sqrt(a)

    def run(self):
        operations = {
            '1': (self.add, "Addition"),
            '2': (self.subtract, "Subtraction"),
            '3': (self.multiply, "Multiplication"),
            '4': (self.divide, "Division"),
            '5': (self.power, "Second Power"),
            '6': (self.square_root, "Square Root")
        }

        while True:
            print("\nSelect operation:")
            for key, (_, name) in operations.items():
                print(f"{key}. {name}")
            print("7. Exit")
            
            choice = input("Enter choice (1-7): ")
            if choice == '7':
                print("Exiting calculator. Goodbye!")
                break
            
            if choice in ['1', '2', '3', '4']:
                try:
                    num1 = float(input("Enter first number: "))
                    num2 = float(input("Enter second number: "))
                    result = operations[choice][0](num1, num2)
                except ValueError:
                    result = "Error: Invalid input"
                
            elif choice in ['5', '6']:
                try:
                    num = float(input("Enter a number: "))
                    result = operations[choice][0](num)
                except ValueError:
                    result = "Error: Invalid input"
            
            else:
                result = "Invalid input. Please try again."
            
            print("Result:", result)

if __name__ == "__main__":
    Calculator().run()
