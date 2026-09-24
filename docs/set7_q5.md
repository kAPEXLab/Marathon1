# Question 5: Delivery Order Performance Analyzer

## 1. Question Details

| Attribute | Details |
|---|---|
| Difficulty | Difficult |
| Supported Languages | C, C++, or Python |
| Internet Access | Not allowed |
| AI Tools | Not allowed |
| Notes or Reference Material | Not allowed |

---

## 2. Introduction

Logistics organizations maintain digital records of delivery orders. These records help teams compare planned and actual completion times, monitor customer issues, and evaluate delivery performance.

Write a modular program that processes multiple delivery-order records and generates a performance summary.

The program must use structures or classes to represent the orders and functions to process individual records and collections of records.

---

## 3. Scenario

Each completed delivery order contains the following input information:

| Field | Description |
|---|---|
| Order ID | Unique identification number of the delivery order |
| Planned Time | Planned number of minutes required to complete the delivery |
| Actual Time | Actual number of minutes taken to complete the delivery |
| Issue Count | Number of customer issues reported after completion |

The program must calculate and store the following additional information for every order:

| Field | Description |
|---|---|
| Performance Score | Calculated score in the range `0` to `100` |
| Category | Performance category assigned using the calculated score |
| Validity | Indicates whether the order record is valid |

### Valid Delivery Order

A delivery-order record is valid when all the following conditions are satisfied:

```text
orderId > 0
plannedTime > 0
actualTime > 0
issueCount >= 0
```

If any of these conditions is not satisfied, the delivery-order record is invalid.

### Performance Score Calculation

For every valid delivery-order record, calculate:

```text
timeScore = (plannedTime / actualTime) * 80

issuePenalty = issueCount * 5

performanceScore = timeScore - issuePenalty
```

The calculated performance score must be limited to the range `0` to `100`.

```text
If performanceScore > 100:
    performanceScore = 100

If performanceScore < 0:
    performanceScore = 0
```

### Performance Categories

| Performance Score | Category Code | Category |
|---:|:---:|---|
| `85` to `100` | `E` | Excellent |
| `70` to less than `85` | `G` | Good |
| `50` to less than `70` | `S` | Satisfactory |
| Less than `50` | `N` | Needs Improvement |
| Invalid record | `I` | Invalid |

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read the number of delivery orders, `N`.
2. Read the details of all `N` delivery orders.
3. Store the orders in an array, vector, or list of structures or objects.
4. Validate every delivery-order record.
5. Calculate the performance score of every valid order.
6. Limit each calculated performance score to the range `0` to `100`.
7. Assign a performance category to every valid order.
8. Assign category code `I` to every invalid order.
9. Update the calculated fields of every order record.
10. Count the total number of valid orders.
11. Count the total number of invalid orders.
12. Count the orders in each performance category.
13. Calculate the average performance score of all valid orders.
14. Find the best-performing valid delivery order.
15. Apply the specified tie-breaking rule when multiple orders have the same highest score.
16. Display the overall performance summary in the specified output format.
17. Organize the program using the mandatory functions described below.

---

## 5. Data Model

Each order must be represented using a single structure, class, or object.

### Order Fields

| Field | Expected Type | Input or Calculated | Description |
|---|---|---|---|
| `orderId` | Integer | Input | Unique identification number of the delivery order |
| `plannedTime` | Real Number | Input | Planned completion time in minutes |
| `actualTime` | Real Number | Input | Actual completion time in minutes |
| `issueCount` | Integer | Input | Number of issues reported |
| `performanceScore` | Real Number | Calculated | Performance score in the range `0` to `100` |
| `category` | Character | Calculated | Category code `E`, `G`, `S`, `N`, or `I` |
| `isValid` | Boolean | Calculated | Indicates whether the record is valid |

### Language-Specific Data Representation

| Selected Language | Required Data Representation |
|---|---|
| C | Structure |
| C++ | Structure or class |
| Python | Class |

Only basic structure or class concepts are required.

---

## 6. Function Details

Students must implement and use the following six functions to create a modular program.

### 6.1 Function 1: Validate an Order

This function determines whether one delivery-order record contains valid input data.

- **Function Name:** `isValidOrder`
- **Arguments:** `order`
- **Return Type:** Boolean

This function should implement the logic to check whether an order is valid by verifying that the Order ID, Planned Time, Actual Time, and Issue Count satisfy the required conditions. It must return `true` only when all conditions are valid; otherwise it must return `false`.

The function must:

1. Receive one order record.
2. Check the Order ID, Planned Time, Actual Time, and Issue Count.
3. Return `true` when all validation conditions are satisfied.
4. Return `false` when at least one validation condition fails.
5. Not read any input.
6. Not print any output.
7. Not modify the order record.

### 6.2 Function 2: Calculate Performance Score

This function calculates the performance score of one valid order.

- **Function Name:** `calculatePerformanceScore`
- **Arguments:** `order`
- **Return Type:** Real Number

This function should implement the formula for `timeScore`, `issuePenalty`, and final `performanceScore`, and then clamp the result into the range `0` to `100` before returning it.

The function must:

1. Receive one valid order record.
2. Calculate the time score.
3. Calculate the issue penalty.
4. Calculate the performance score.
5. Limit the score to the range `0` to `100`.
6. Return the final performance score.
7. Not modify the order record.
8. Not read input or print output.

### 6.3 Function 3: Process All Orders

This function processes all stored order records.

- **Function Name:** `processAllOrders`
- **Arguments:** `orders, size`
- **Return Type:** None or Void

This function should implement the complete processing pass over the order list, validate each record, calculate score for valid records, assign the category, and mark invalid records with category `I` and score `0`.

The function must:

1. Receive the collection of order records.
2. Receive the number of records.
3. Traverse all order records.
4. Call `isValidOrder` for every record.
5. For valid records, call `calculatePerformanceScore` and assign the category using the documented score boundaries.
6. For invalid records, set `performanceScore` to `0` and `category` to `I`.
7. Ensure that the calculated fields of every record are updated.
8. Not read any input.
9. Not print any output.

### 6.4 Function 4: Find the Best Order

This function finds the best-performing valid order.

- **Function Name:** `findBestOrder`
- **Arguments:** `orders, size`
- **Return Type:** Integer

This function should implement the logic to search the valid orders, select the one with the highest performance score, and break ties by choosing the smaller Order ID. It must return the index of the chosen order or `-1` if none are valid.

The function must:

1. Examine only valid orders.
2. Select the order having the highest performance score.
3. If multiple valid orders have the same highest score, select the order having the smaller Order ID.
4. Return the array, vector, or list index of the selected order.
5. Return `-1` when no valid order exists.
6. Not modify the collection.
7. Not read input or print output.

### 6.5 Function 5: Count Orders by Category

This function counts orders belonging to a specified category.

- **Function Name:** `countByCategory`
- **Arguments:** `orders, size, categoryCode`
- **Return Type:** Integer

This function should implement the logic to traverse the order list and count how many records have exactly the given category code.

The function must:

1. Receive the collection of order records.
2. Examine all records.
3. Count how many orders have exactly the given category code.
4. Return the count.
5. Not read input or print output.

### 6.6 Function 6: Calculate Average Score

This function calculates the average performance score of valid orders.

- **Function Name:** `calculateAverageScore`
- **Arguments:** `orders, size`
- **Return Type:** Real Number

This function should implement the logic to sum the performance scores of all valid orders and divide by the number of valid orders; if there are no valid orders, it must return `0.0`.

The function must:

1. Receive the collection of order records.
2. Consider only valid orders.
3. Return the arithmetic mean of all valid performance scores.
4. Return `0.0` when no valid order exists.
5. Not read input or print output.

### 6.7 Responsibilities of the Main Program

The main program must:

1. Read the number of orders.
2. Read all order records.
3. Call `processAllOrders`.
4. Count valid and invalid orders.
5. Count the number of valid orders in each category.
6. Call `calculateAverageScore` for valid orders.
7. Call `findBestOrder` and print details of the best order when one exists.
8. If the total number of valid orders is zero, print exactly `No valid orders` and stop.
9. Otherwise display the full performance summary in the required format.

---

## 7. Input Format

The first input contains one integer:

```text
N
```

The next `N` lines each contain four values:

```text
orderId plannedTime actualTime issueCount
```

---

## 8. Output Format

If at least one valid order exists, the program must print exactly:

```text
Valid orders: <valid_count>
Invalid orders: <invalid_count>
Excellent: <excellent_count>
Good: <good_count>
Satisfactory: <satisfactory_count>
Needs Improvement: <needs_improvement_count>
Average score: <average_value>
Best order: <best_order_id>
```

The average score must be displayed with exactly two digits after the decimal point.

If no valid order exists, print exactly:

```text
No valid orders
```

In the zero-valid case, none of the summary lines above should be printed.

---

## 9. Constraints and Assumptions

```text
1 <= N <= 1000
orderId > 0
plannedTime > 0
actualTime > 0
issueCount >= 0
```

- Every input value is valid as a number.
- Some orders may be invalid and must still be processed.
- The best order is selected among valid orders only.

---

## 10. Rules and Clarifications

* Rule 1 Valid Order: A record is valid only if all input fields satisfy the listed conditions.
* Rule 2 Score Clamp: Performance scores must be clamped to the range `0` to `100`.
* Rule 3 Category Assignment: Categories are assigned using the score intervals exactly as described.
* Rule 4 Best Order Tie-Break: If two valid orders have the same highest score, choose the smaller Order ID.
* Rule 5 Invalid Record Handling: Invalid records are counted but not used in score calculations.
* Rule 6 Mandatory Function Usage: All six required functions must be implemented and used.

---

## 11. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Mixed valid and invalid orders | `5`<br>`101 10 8 1`<br>`102 12 14 2`<br>`-1 8 6 0`<br>`103 9 10 0`<br>`104 20 25 3` | `Valid orders: 4`<br>`Invalid orders: 1`<br>`Excellent: 1`<br>`Good: 1`<br>`Satisfactory: 1`<br>`Needs Improvement: 1`<br>`Average score: 68.64`<br>`Best order: 101` |
| 2 | All orders valid | `3`<br>`201 5 5 0`<br>`202 10 8 1`<br>`203 8 10 0` | `Valid orders: 3`<br>`Invalid orders: 0`<br>`Excellent: 1`<br>`Good: 1`<br>`Satisfactory: 1`<br>`Needs Improvement: 0`<br>`Average score: 79.67`<br>`Best order: 202` |
| 3 | No valid orders | `3`<br>`0 8 6 0`<br>`302 0 5 0`<br>`303 7 -2 1` | `No valid orders` |
| 4 | Same best score selects smaller Order ID | `4`<br>`401 10 8 0`<br>`402 20 16 0`<br>`403 8 6 1`<br>`404 5 5 10` | `Valid orders: 4`<br>`Invalid orders: 0`<br>`Excellent: 3`<br>`Good: 0`<br>`Satisfactory: 1`<br>`Needs Improvement: 0`<br>`Average score: 87.50`<br>`Best order: 401` |
| 5 | Score clamp to zero and one hundred | `3`<br>`501 100 1 20`<br>`502 1 100 0`<br>`503 50 50 0` | `Valid orders: 3`<br>`Invalid orders: 0`<br>`Excellent: 0`<br>`Good: 1`<br>`Satisfactory: 0`<br>`Needs Improvement: 2`<br>`Average score: 26.93`<br>`Best order: 503` |
| 6 | Boundary case with one valid order | `1`<br>`601 10 10 0` | `Valid orders: 1`<br>`Invalid orders: 0`<br>`Excellent: 0`<br>`Good: 1`<br>`Satisfactory: 0`<br>`Needs Improvement: 0`<br>`Average score: 80.00`<br>`Best order: 601` |

---

## 12. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must store the orders in a structured form.
- The program should remain modular by using the required functions.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
