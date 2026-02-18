# Python Assessment

## Overview

This assessment consists of 10 functions covering data processing, recursion, string manipulation, and input validation. Your goal is to implement each function in `final_destination.py` until all tests in `test_final_destination.py` pass.

To run the tests:
```bash
pytest test_final_destination.py
```

---

## Question 1 — `inventory_report_generator`

**As a warehouse manager**, I want to feed in a flat list of stock entries and get back a summary per category, so I can quickly see the total stock and value of each product group without manually adding things up.

```python
inventory_report_generator([
    {"category": "Electronics", "unit_cost": 200, "stock_count": 5},
    {"category": "Books",       "unit_cost": 15,  "stock_count": 10},
    {"category": "Electronics", "unit_cost": 200, "stock_count": 3},
])

# Returns:
{
    "Electronics": {"total_value": 1600, "total_stock": 8},
    "Books":        {"total_value": 150,  "total_stock": 10},
}
```

```python
inventory_report_generator([])
# Returns: {}
```

---

## Question 2 — `rainfall_analyzer`

**As a meteorologist**, I want to check a batch of rainfall readings against a safety threshold and immediately see how many readings are problematic and what the average rainfall was, so I can decide whether to issue a weather warning.

```python
rainfall_analyzer([10, 15, 8, 12], threshold=20)
# Prints:
# All readings within threshold
# Average: 11.25

rainfall_analyzer([5, 25, 8, 30], threshold=20)
# Prints:
# Warning: 2 readings above 20
# Average: 17.00

rainfall_analyzer([], threshold=20)
# Prints:
# No rainfall data
```

---

## Question 3 — `username_validator_with_retry`

**As a system administrator**, I want users to be given a limited number of attempts to enter a valid username, so that bots and careless entries are rejected without permanently locking the interface after a single mistake.

A valid username is **5–15 characters**, contains only **letters, digits, or underscores**, and **starts with a letter**.

```python
username_validator_with_retry(max_attempts=3)

# User types: "ab"
# Prints: Invalid username. Try again.
# User types: "1invalid"
# Prints: Invalid username. Try again.
# User types: "good_user1"
# Prints: Username accepted!

# ---

# User types: "bad" three times
# Prints: Maximum attempts reached. Access denied.
```

---

## Question 4 — `employee_performance_processor`

**As an HR analyst**, I want to take a list of employees and their review scores and split them into high performers and those who need improvement, so I can target development programs at the right people.

An employee with an average score **≥ 80** is a high performer; below 80 goes into needs improvement.

```python
employee_performance_processor([
    {"name": "Alice", "scores": [90, 85, 88]},
    {"name": "Bob",   "scores": [70, 65, 75]},
])

# Returns:
{
    "high_performers":   [{"name": "Alice", "average": 87.67}],
    "needs_improvement": [{"name": "Bob",   "average": 70.0}],
}
```

```python
employee_performance_processor([])
# Returns: {"high_performers": [], "needs_improvement": []}
```

---

## Question 5 — `order_batcher`

**As a logistics coordinator**, I want to split a large queue of orders into fixed-size batches, so each fulfilment team receives a manageable chunk to process rather than the entire queue at once.

```python
order_batcher(["O1", "O2", "O3", "O4", "O5"], batch_size=2)
# Returns: [["O1", "O2"], ["O3", "O4"], ["O5"]]

order_batcher(["A", "B", "C"], batch_size=3)
# Returns: [["A", "B", "C"]]

order_batcher([], batch_size=4)
# Returns: []
```

---

## Question 6 — `social_network_analyzer`

**As a social media analyst**, I want to inspect a network of follow relationships and find out the total number of follows, who is the most followed user, and which users have no followers at all, so I can identify influencers and dormant accounts.

```python
social_network_analyzer({
    "Alice": ["Bob", "Carol"],
    "Bob":   ["Carol"],
    "Carol": [],
})

# Returns:
{
    "total_follows":  3,
    "most_followed":  "Carol",
    "no_followers":   ["Alice"],
}
```

```python
social_network_analyzer({})
# Returns: {"total_follows": 0, "most_followed": None, "no_followers": []}
```

---

## Question 7 — `count_vowels`

**As a linguistics student**, I want a function that counts how many vowels are in any string so I can run it across a large corpus of words — and I want it implemented recursively so I can study recursive string traversal.

> ⚠️ This function **must** be implemented using recursion. An iterative solution will fail the tests.

```python
count_vowels("hello")    # Returns: 2
count_vowels("AEIOU")    # Returns: 5
count_vowels("rhythm")   # Returns: 0
count_vowels("")         # Returns: 0
```

---

## Question 8 — `text_pipeline_processor`

**As a data engineer**, I want to apply a chain of named text transformations to a list of strings in a single call, so I can clean and normalise raw text data with a flexible, composable pipeline instead of writing one-off loops.

Available transformations: `"uppercase"`, `"strip"`, `"remove_empty"`, `"reverse"`.

```python
text_pipeline_processor(["hello", "world"], ["uppercase"])
# Returns: ["HELLO", "WORLD"]

text_pipeline_processor(["  hi  ", "  "], ["strip", "remove_empty", "uppercase"])
# Returns: ["HI"]

text_pipeline_processor(["abc"], ["reverse", "uppercase"])
# Returns: ["CBA"]

text_pipeline_processor(["a", "b"], [])
# Returns: ["a", "b"]
```

---

## Question 9 — `score_ranker`

**As a tournament organiser**, I want to take a list of competitors and their scores and produce a ranked leaderboard where tied players share a rank and the next rank reflects the number of players above them, so the standings are always fair and unambiguous.

```python
score_ranker([("Alice", 100), ("Bob", 150), ("Charlie", 120)])
# Returns: [("Bob", 150, 1), ("Charlie", 120, 2), ("Alice", 100, 3)]

score_ranker([("A", 100), ("B", 100), ("C", 90)])
# Returns: [("A", 100, 1), ("B", 100, 1), ("C", 90, 3)]
#           ↑ both tied at rank 1, next rank jumps to 3

score_ranker([])
# Returns: []
```

---

## Question 10 — `fibonacci`

**As a computer science student**, I want a recursive implementation of the Fibonacci sequence so I can observe how the call stack grows with each level of recursion and use it as a reference when studying divide-and-conquer algorithms.

> ⚠️ This function **must** be implemented using recursion. An iterative solution will fail the tests.

```python
fibonacci(0)   # Returns: 0
fibonacci(1)   # Returns: 1
fibonacci(5)   # Returns: 5
fibonacci(10)  # Returns: 55
```