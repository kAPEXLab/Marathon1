# Question 2: Torque and Power Calculation

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

A mechanical system stores several force and radius values. The program must calculate torque, find the maximum torque, and display the average torque for all samples.

---

## 3. Scenario

Each sample stores a force value and a radius value. The torque for one sample is:

```text
torque = force * radius
```

The program must calculate the average torque, identify the maximum torque, and report the first index where the maximum occurs.

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read the number of samples, `N`.
2. Read and store the `N` force and radius pairs.
3. Calculate the torque for each sample.
4. Calculate the average torque.
5. Find the maximum torque.
6. Find the index of the first occurrence of the maximum value.
7. Display the results in the specified output format.

---

## 5. Function Details

Students must implement and use the following functions:

* Function Name: `calculateAverageTorque`
* Arguments: `torques, size`
* Return type: `real number`

* Function Name: `findMaximumTorque`
* Arguments: `torques, size`
* Return type: `real number`

* Function Name: `findMaximumIndex`
* Arguments: `torques, size, maximumTorque`
* Return type: `integer`

The functions must not read input, print output, or modify the stored torque values. `findMaximumIndex` must return the first index where `maximumTorque` occurs.

---

## 6. Input Format

The first input contains one integer:

```text
N
```

The next `N` lines contain two space-separated numbers:

```text
force radius
```

---

## 7. Output Format

The program must print exactly:

```text
Average torque: <average_torque>
Maximum torque: <maximum_torque>
Maximum index: <index>
```

The average must be displayed with exactly two digits after the decimal point. Zero-based indexing must be used.

---

## 8. Constraints and Assumptions

```text
1 <= N <= 1000
0 <= force <= 1000
0 <= radius <= 1000
```

- All input values are valid integers.
- Exactly `N` torque values will be calculated.
- At least one sample will be provided.

---

## 9. Rules and Clarifications

* Rule 1 Torque Calculation: `torque = force * radius`.
* Rule 2 Average Calculation: The average is calculated using all `N` torque values.
* Rule 3 First Maximum Occurrence: If the maximum occurs more than once, report the smallest index.
* Rule 4 Mandatory Function Usage: All three required functions must be implemented and used.

---

## 10. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Normal torque values | `4`<br>`10 2`<br>`5 4`<br>`8 3`<br>`6 5` | `Average torque: 23.50`<br>`Maximum torque: 30`<br>`Maximum index: 3` |
| 2 | Maximum torque occurs multiple times | `5`<br>`3 5`<br>`2 10`<br>`4 5`<br>`1 20`<br>`6 5` | `Average torque: 21.00`<br>`Maximum torque: 30`<br>`Maximum index: 4` |
| 3 | Values increase uniformly | `5`<br>`1 1`<br>`2 2`<br>`3 3`<br>`4 4`<br>`5 5` | `Average torque: 11.00`<br>`Maximum torque: 25`<br>`Maximum index: 4` |
| 4 | Boundary case with one sample | `1`<br>`7 9` | `Average torque: 63.00`<br>`Maximum torque: 63`<br>`Maximum index: 0` |
| 5 | All values equal | `4`<br>`4 4`<br>`4 4`<br>`4 4`<br>`4 4` | `Average torque: 16.00`<br>`Maximum torque: 16`<br>`Maximum index: 0` |
| 6 | Mixed positive values | `3`<br>`10 1`<br>`20 2`<br>`30 3` | `Average torque: 46.67`<br>`Maximum torque: 90`<br>`Maximum index: 2` |

---

## 11. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must store the torque values.
- The original order of the samples must be preserved.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
