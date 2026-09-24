# Question 2: Delivery Time Analysis

## 1. Question Details

| Attribute | Details |
|---|---|
| Difficulty | Easy |
| Supported Languages | C, C++, or Python |
| Internet Access | Not allowed |
| AI Tools | Not allowed |
| Notes or Reference Material | Not allowed |

---

## 2. Introduction

A delivery service records the travel time of several packages in minutes. Write a program that generates a basic statistical summary of the recorded values.

---

## 3. Scenario

The delivery times are stored in their original order. The program must calculate the average, identify the maximum value, and report the first index at which the maximum occurs.

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read the number of package deliveries, `N`.
2. Read and store the `N` delivery times.
3. Calculate the average delivery time.
4. Find the maximum delivery time.
5. Find the index of the first occurrence of the maximum value.
6. Display the results in the specified output format.

---

## 5. Function Details

Students must implement and use the following functions:

* Function Name: `calculateAverage`
* Arguments: `deliveryTimes, size`
* Return type: `real number`

This function should implement the logic to compute the arithmetic mean of all delivery times in the array.

* Function Name: `findMaximum`
* Arguments: `deliveryTimes, size`
* Return type: `integer`

This function should implement the logic to scan the array and return the largest delivery time value.

* Function Name: `findMaximumIndex`
* Arguments: `deliveryTimes, size, maximumValue`
* Return type: `integer`

This function should implement the logic to return the first index where the maximum value occurs, preserving left-to-right order.

The functions must not read input, print output, or modify the stored delivery times. `findMaximumIndex` must return the first index where `maximumValue` occurs.

---

## 6. Input Format

The first input contains one integer:

```text
N
```

The second input contains `N` space-separated integers:

```text
t1 t2 ... tN
```

---

## 7. Output Format

The program must print exactly:

```text
Average: <average_value>
Maximum: <maximum_value>
Maximum index: <index>
```

The average must be displayed with exactly two digits after the decimal point. Zero-based indexing must be used.

---

## 8. Constraints and Assumptions

```text
1 <= N <= 1000
0 <= deliveryTime <= 100000
```

- All input values are valid integers.
- Exactly `N` delivery-time values will be provided.
- At least one delivery-time value will be provided.

---

## 9. Rules and Clarifications

* Rule 1 Average Calculation: The average must be calculated using all `N` delivery times.
* Rule 2 Floating-Point Result: The average calculation must produce a floating-point result.
* Rule 3 First Maximum Occurrence: If the maximum occurs more than once, report the smallest index.
* Rule 4 Mandatory Function Usage: All three required functions must be implemented and used.

---

## 10. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Normal delivery-time values | `8`<br>`45 60 120 75 40 100 140 55` | `Average: 79.38`<br>`Maximum: 140`<br>`Maximum index: 6` |
| 2 | Maximum value occurs multiple times | `6`<br>`20 80 45 80 30 25` | `Average: 46.67`<br>`Maximum: 80`<br>`Maximum index: 1` |
| 3 | Values are in increasing order | `5`<br>`10 20 30 40 50` | `Average: 30.00`<br>`Maximum: 50`<br>`Maximum index: 4` |
| 4 | Values are in decreasing order | `5`<br>`50 40 30 20 10` | `Average: 30.00`<br>`Maximum: 50`<br>`Maximum index: 0` |
| 5 | Boundary case with one delivery | `1`<br>`35` | `Average: 35.00`<br>`Maximum: 35`<br>`Maximum index: 0` |
| 6 | Boundary case with all values equal | `4`<br>`15 15 15 15` | `Average: 15.00`<br>`Maximum: 15`<br>`Maximum index: 0` |

---

## 11. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must store the delivery times.
- The original order of the delivery times must be preserved.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
