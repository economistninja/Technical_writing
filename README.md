# Technical_writing

## Sample Calculator Code

Here's a simple Python implementation that matches this README:

```python
# calculator.py
from operations import add, subtract, multiply, divide
from history import CalculationHistory

def main():
    history = CalculationHistory()
    
    while True:
        print("\nCalculator App")
        print("-------------")
        print("Select operation:")
        print("1. Add")
        print("2. Subtract")
        print("3. Multiply")
        print("4. Divide")
        print("5. Show History")
        print("6. Exit")
        
        choice = input("Enter choice (1-6): ")
        
        if choice == '6':
            break
            
        if choice == '5':
            history.display()
            continue
            
        if choice in ('1', '2', '3', '4'):
            try:
                num1 = float(input("Enter first number: "))
                num2 = float(input("Enter second number: "))
                
                if choice == '1':
                    result = add(num1, num2)
                    print(f"Result: {num1} + {num2} = {result}")
                elif choice == '2':
                    result = subtract(num1, num2)
                    print(f"Result: {num1} - {num2} = {result}")
                elif choice == '3':
                    result = multiply(num1, num2)
                    print(f"Result: {num1} * {num2} = {result}")
                elif choice == '4':
                    result = divide(num1, num2)
                    print(f"Result: {num1} / {num2} = {result}")
                    
                history.add_entry(f"{num1} {['+','-','*','/'][int(choice)-1]} {num2} = {result}")
                
            except ValueError:
                print("Please enter valid numbers!")
            except ZeroDivisionError:
                print("Cannot divide by zero!")
        else:
            print("Invalid input. Please enter a number between 1-6.")

if __name__ == "__main__":
    main()
