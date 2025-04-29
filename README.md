import random

def generate_list(target, length):
    if length < 2:
        raise ValueError("Length must be at least 2")

    pairs = [(a, target - a) for a in range(10) if 0 <= target - a <= 9]
    if not pairs:
        raise ValueError(f"No digits found that sum to {target}")

    first, second = random.choice(pairs)
    remaining = [random.randint(0, 9) for _ in range(length - 2)]

    return [first, second] + remaining

print("Case#1 Output:", *generate_list(7, 3))

print("Case#2 Output:", *generate_list(10, 3))




This Python script generates a list of random digits, with a little twist! The first two numbers in the list always add up to a target value that you specify. The rest of the numbers in the list are totally random, ranging from 0 to 9.

How it works:
Input Validation:
The function generate_list(target, length) ensures that the length of the list is at least 2 (since we need two numbers to sum to something). If you try to give a length smaller than 2, it raises an error.

Generating Valid Pairs:
It generates all possible pairs of single-digit numbers that add up to the target. For example, if the target is 7, the valid pairs could be (0,7), (1,6), (2,5), and so on.

Random Pair Selection:
Once it has a list of valid pairs, it randomly picks one to use as the first two numbers in the list.

Filling the Rest of the List:
After choosing the first two numbers, it fills the rest of the list with random digits, ensuring the list matches the length you requested.

Output:
The final list is printed out, showing how the first two digits sum up to the target, and the remaining digits are randomly selected.

Example:
If you call generate_list(7, 3), the function might output:

bash
Copy
Edit
Case#1 Output: 5 2 8
In this case, 5 + 2 = 7, and the third number is randomly chosen as 8.
