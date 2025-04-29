Hey there! 👋
This is a simple, beginner-friendly Python program I made that generates a list of random single-digit numbers. But here’s the cool part — the first two numbers in the list always add up to a number you choose (called the target). The rest of the numbers? Completely random from 0 to 9.

It's a fun little exercise to practice working with lists, random numbers, and making sure your program handles invalid inputs nicely.

✳️ How It Works
The program has a function called generate_list(target, length).
You tell it two things:

target — what the sum of the first two numbers should be.

length — how long the final list should be (at least 2 numbers, obviously, because we need two numbers to sum up to something).

If the input is invalid (like a length less than 2, or an impossible target sum), the program raises a friendly error message instead of crashing.

Once it finds a valid pair of numbers that adds up to your target, it randomly picks them and then fills the rest of the list with random numbers between 0 and 9. Finally, it prints the list.

📜 Here’s the Full Code:
python
Copy
Edit
import random

def generate_list(target, length):
    if length < 2:
        raise ValueError("Length must be at least 2")

    # Create possible pairs of digits that add up to the target
    pairs = [(a, target - a) for a in range(10) if 0 <= target - a <= 9]
    if not pairs:
        raise ValueError(f"No digits found that sum to {target}")

    # Pick a random valid pair
    first, second = random.choice(pairs)

    # Generate the rest of the list with random digits
    remaining = [random.randint(0, 9) for _ in range(length - 2)]

    return [first, second] + remaining

# Test Cases
print("Case#1 Output:", *generate_list(7, 3))
print("Case#2 Output:", *generate_list(10, 3))
📝 Example Output:
bash
Copy
Edit
Case#1 Output: 5 2 9
Case#2 Output: 6 4 3
In both cases, notice how the first two numbers add up to the target (like 5+2=7 and 6+4=10) and the third number is just random.

📌 Why I Made This
I built this to brush up on:

List comprehensions ✅

Random number generation ✅

Simple error handling ✅
