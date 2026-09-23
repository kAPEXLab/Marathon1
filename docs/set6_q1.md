# Question 1: Shaft Speed Classification

## 1. Question Details

| Attribute | Details |
|---|---|
| Difficulty | Very Easy |
| Supported Languages | C, C++, or Python |
| Internet Access | Not allowed |
| AI Tools | Not allowed |
| Notes or Reference Material | Not allowed |

---

## 2. Introduction

A machine shop records shaft speeds in revolutions per minute (RPM). The program must classify each shaft speed as low, normal, or high based on the given lower and upper limits.

---

## 3. Scenario

Two speed limits are provided:

- `L`: Lower speed limit
- `H`: Upper speed limit

| Category | Classification Rule |
|---|---|
| Low | Speed is strictly less than `L` |
| Normal | Speed is greater than or equal to `L` and less than or equal to `H` |
| High | Speed is strictly greater than `H` |

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read the number of shaft speeds, `N`.
2. Read the lower limit, `L`.
3. Read the upper limit, `H`.
4. Read and store the `N` shaft speeds.
5. Classify every speed.
6. Count the Low, Normal, and High speeds.
7. Display the category counts in the specified output format.

---

## 5. Function Details

Students must implement and use a function that classifies one shaft speed.

* Function Name: `classifySpeed`
* Arguments: `speed, lowerLimit, upperLimit`

| Argument | Expected Type | Direction | Description |
|---|---|---|---|
| `speed` | Integer | Input | Shaft speed in RPM |
| `lowerLimit` | Integer | Input | Lower classification limit, represented by `L` |
| `upperLimit` | Integer | Input | Upper classification limit, represented by `H` |

* Return type: `integer`
* Return Values

| Return Value | Category | Condition |
|---:|---|---|
| `0` | Low | `speed < lowerLimit` |
| `1` | Normal | `lowerLimit <= speed <= upperLimit` |
| `2` | High | `speed > upperLimit` |

The function must not read input, print output, calculate counts, or modify its arguments.

---

## 6. Input Format

The first input contains three space-separated integers:

```text
N L H
```

The second input contains `N` space-separated integers:

```text
s1 s2 ... sN
```

---

## 7. Output Format

The program must print exactly:

```text
Low: <low_count>
Normal: <normal_count>
High: <high_count>
```

No additional prompts or explanatory messages may be printed.

---

## 8. Constraints and Assumptions

```text
1 <= N <= 1000
0 <= L <= H <= 50000
0 <= speed <= 50000
```

- All input values are valid integers.
- Exactly `N` shaft speeds will be provided.
- Values equal to `L` or `H` are considered Normal.

---

## 9. Rules and Clarifications

* Rule 1 Speed Classification: Use the exact lower and upper limit rules.
* Rule 2 Boundary Values: Values equal to `L` or `H` belong to the Normal category.
* Rule 3 Mandatory Function Usage: The required classification function must be implemented and used.

---

## 10. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Normal mixture of low, normal, and high speeds | `6 1000 2000`<br>`500 1200 2600 1800 2200 900` | `Low: 2`<br>`Normal: 2`<br>`High: 2` |
| 2 | All speeds are normal | `4 500 700`<br>`500 650 700 600` | `Low: 0`<br>`Normal: 4`<br>`High: 0` |
| 3 | All speeds are low | `5 2000 3000`<br>`100 500 1500 1999 10` | `Low: 5`<br>`Normal: 0`<br>`High: 0` |
| 4 | All speeds are high | `5 100 300`<br>`350 500 600 800 1000` | `Low: 0`<br>`Normal: 0`<br>`High: 5` |
| 5 | Boundary case with one value at lower limit | `1 200 500`<br>`200` | `Low: 0`<br>`Normal: 1`<br>`High: 0` |
| 6 | Boundary case with one value at upper limit | `1 200 500`<br>`500` | `Low: 0`<br>`Normal: 1`<br>`High: 0` |

---

## 11. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must store the shaft speeds.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
