This post-class practice helps you reinforce the core NumPy skills we used:

- Creating and inspecting arrays  
- Indexing, slicing, and boolean filtering  
- Aggregations over rows/columns  
- Reshaping and simple matrix operations

You can work through these in the same environment you used in class (Colab or VS Code).

---

## 1. Warm-up: Rebuild the basics

**Goal:** Make array creation and inspection feel automatic.

1. Create each of the following arrays and print its `shape`, `ndim`, and `dtype`:
   - A 1D array of integers from 10 to 19  
   - A 2D array of shape `(4, 3)` filled with 1.5  
   - A 3D array of zeros with shape `(2, 2, 3)`

2. Convert the `(4, 3)` float array to integers using `.astype(int)`.  
3. Write down (in a markdown cell) when you would prefer `float` vs `int` in real analyst work (e.g., prices vs counts).

---

## 2. Sales table drill: Indexing and slicing

**Scenario:** You have quarterly sales numbers for 4 regions (rows) over 5 quarters (columns).

```python
import numpy as np

sales = np.array([
    ,  # Region A
    ,  # Region B
    ,  # Region C
       # Region D
])
regions = np.array(["A", "B", "C", "D"])
quarters = np.array(["Q1", "Q2", "Q3", "Q4", "Q5"])
````

Do the following:

1. Select all quarters for **Region B** as a 1D array.  
2. Select **Q2 to Q4** (inclusive) for all regions as a 2D subarray.  
3. Select **Q5** sales for **Regions A and D only** (use slicing or fancy indexing).  
4. Compute the **shape** of each result and add a brief comment: “Is this 1D or 2D, and why?”

---

## 3\. Boolean masks: Work with targets

**Scenario:** You have campaign response data.

```py
names = np.array(["Ana", "Ben", "Chen", "Dana", "Eli", "Fatima", "George", "Hui"])
spend = np.array([200, 150, 300, 120, 180, 220, 160, 310])      # marketing spend
revenue = np.array([400, 180, 500, 100, 220, 260, 150, 600])   # revenue
```

1. Compute the **ROI** for each person: `roi = revenue / spend`.  
2. Create a boolean mask for customers with `roi >= 2.0`.  
3. Use the mask to:  
   - List their names  
   - List their spend and revenue  
4. Create a second mask for customers with `spend >= 200`.  
5. Combine the two masks to find customers who have **roi \>= 2.0 AND spend \>= 200**.  
6. In a markdown cell, answer: *“What business insight do you get from this filtered group?”*

---

## 4\. Gradebook: Aggregations and broadcasting

Reuse the “Gradebook” idea from class and extend it.

```py
students = np.array(["S1", "S2", "S3", "S4", "S5"])
subjects = np.array(["Math", "Stats", "Python"])

scores = np.array([
    [75, 80, 85],
    [60, 65, 70],
    [90, 88, 92],
    [82, 79, 84],
    [70, 72, 78]
])
```

1. Compute each student’s **average score** (per row).  
2. Compute each subject’s **average score** (per column).  
3. Create `scores_centered` by subtracting the **subject mean** from each column (broadcasting).  
4. For `scores_centered`, compute per-student averages again.  
5. Compare which student looks best by **raw average** vs **centered average**.  
6. In a markdown cell, explain briefly why centered scores might give a fairer comparison.

---

## 5\. Reshape and flatten: From daily to weekly

**Scenario:** You have 30 days of daily website visits, and you want to summarize them by week.

```py
daily_visits = np.array([
    120, 130, 125, 140, 150,
    160, 170, 155, 145, 135,
    128, 132, 138, 142, 148,
    152, 158, 162, 168, 172,
    180, 190, 185, 175, 165,
    155, 145, 135, 125, 115
])
```

1. Reshape `daily_visits` into a `(6, 5)` array representing **6 weeks × 5 days**.  
2. Compute **total visits per week**.  
3. Compute **average visits per day of the week** (e.g., all “day 1 of week” together, all “day 2 of week” together, etc.).  
4. Flatten the reshaped array back to 1D and confirm it matches the original `daily_visits`.

Hint: Pay attention to how reshaping groups the data; mention any assumptions you’re making about which days belong to which week.

---

## 6\. Mini-project: Simple scoring model

This mirrors the tiny matrix multiply example from class, but with more features.

```py
# Each row: [page_views, time_on_site (minutes), past_purchases]
X = np.array([
    [10,  3.5,  0],
    [25,  5.0,  1],
    [40,  2.0,  0],
    [15, 10.0,  3],
    [30,  4.0,  2]
])

customers = np.array(["C1", "C2", "C3", "C4", "C5"])
```

1. Choose a weight vector `w = [w_views, w_time, w_purchases]` (for example `[0.1, 0.5, 1.0]`).  
2. Compute a **score** for each customer using `scores = X @ w`.  
3. Rank customers by score (highest first).  
4. Change the weights to emphasize **past\_purchases** more than other features, and recompute.  
5. In a markdown cell, answer:  
   - Which customer is top-ranked before vs after changing weights?  
   - In what real-world situation might you prefer each weighting?

---

## 7\. Stretch ideas (optional)

If you’re comfortable with the above, try:

- Generate 1,000 random test scores with `np.random.randn`, scale them to have mean 70 and standard deviation 10, then:  
  - Clip scores to the range `[0, 100]`  
  - Compute min, max, mean, and standard deviation  
- Simulate a small A/B test:  
  - Two groups of 20 users each  
  - Randomly generate conversions (0 or 1\) for each group  
  - Compute conversion rate per group using pure NumPy operations

---

## How to get help

If you get stuck:

- Add a markdown cell describing what you tried and what you expected vs what happened.  
- Bring your notebook to the next session or share it in Discord for feedback.

Practicing these patterns now will make later topics (like Pandas and modeling) feel much more natural.

