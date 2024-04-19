import random

operations = ['+', '-', '*', '/']
num_questions = 5
num_range = (1, 20)  # Range of numbers for operands

score = 0

for _ in range(num_questions):
    operation = random.choice(operations)
    a = random.randint(*num_range)
    b = random.randint(*num_range)
    
    if operation == '+':
        correct_answer = a + b
    elif operation == '-':
        correct_answer = a - b
    elif operation == '*':
        correct_answer = a * b
    elif operation == '/':
        # Ensure the result is an integer for division
        b = random.randint(1, 10)  # Avoid division by zero
        a = b * random.randint(*num_range)
        correct_answer = a // b
    
    user_answer = input(f"What is {a} {operation} {b}? ")
    
    if user_answer.isdigit() and int(user_answer) == correct_answer:
        print("Correct!")
        score += 1
    else:
        print("Incorrect!")
        print(f"The correct answer is {correct_answer}")

print(f"You scored {score} out of {num_questions}")
