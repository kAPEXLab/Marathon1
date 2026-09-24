# Question 1: Delivery Trip Classification

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

A logistics platform records the duration of delivery trips in minutes. Each trip must be classified using lower and upper time limits.

Write a program that classifies trips and counts how many belong to each category.

---

## 3. Scenario

Two delivery-time limits are provided:

- `L`: Lower duration limit
- `H`: Upper duration limit

| Category | Classification Rule |
|---|---|
| Quick | Trip duration is strictly less than `L` |
| On Time | Trip duration is greater than or equal to `L` and less than or equal to `H` |
| Delayed | Trip duration is strictly greater than `H` |

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read the number of trips, `N`.
2. Read the lower duration limit, `L`.
3. Read the upper duration limit, `H`.
4. Read and store the durations of all `N` trips.
5. Classify every trip.
6. Count the Quick, On Time, and Delayed trips.
7. Display the category counts in the specified output format.

---

## 5. Function Details

Students must implement and use a function that classifies one trip duration.

* Function Name: `classifyTrip`
* Arguments: `tripDuration, lowerLimit, upperLimit`

This function should implement the logic to decide whether a single trip duration belongs to the Quick, On Time, or Delayed category using the lower and upper limits.

| Argument | Expected Type | Direction | Description |
|---|---|---|---|
| `tripDuration` | Integer | Input | Duration of the current trip in minutes |
| `lowerLimit` | Integer | Input | Lower classification limit, represented by `L` |
| `upperLimit` | Integer | Input | Upper classification limit, represented by `H` |

* Return type: `integer`
* Return Values

| Return Value | Category | Condition |
|---:|---|---|
| `0` | Quick | `tripDuration < lowerLimit` |
| `1` | On Time | `lowerLimit <= tripDuration <= upperLimit` |
| `2` | Delayed | `tripDuration > upperLimit` |

The function must not read input, print output, calculate counts, or modify its arguments.

---

## 6. Input Format

The first input contains three space-separated integers:

```text
N L H
```

The second input contains `N` space-separated integers:

```text
t1 t2 ... tN
```

---

## 7. Output Format

The program must print exactly:

```text
Quick: <quick_count>
On Time: <on_time_count>
Delayed: <delayed_count>
```

No additional prompts or explanatory messages may be printed.

---

## 8. Constraints and Assumptions

```text
1 <= N <= 1000
0 <= L <= H <= 100000
0 <= tripDuration <= 100000
```

- All input values are valid integers.
- Exactly `N` trip durations will be provided.
- Values equal to `L` or `H` are On Time.

---

## 9. Rules and Clarifications

* Rule 1 Lower Boundary: A trip duration equal to `L` must be classified as On Time.
* Rule 2 Upper Boundary: A trip duration equal to `H` must be classified as On Time.
* Rule 3 Mandatory Function Usage: `classifyTrip` must be called for every trip.

---

## 10. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Normal case containing all three categories | `8 50 100`<br>`45 60 120 75 40 100 140 55` | `Quick: 2`<br>`On Time: 4`<br>`Delayed: 2` |
| 2 | Duration values equal to both limits | `5 50 100`<br>`50 100 49 101 75` | `Quick: 1`<br>`On Time: 3`<br>`Delayed: 1` |
| 3 | All trips are Quick | `5 50 100`<br>`10 20 30 40 0` | `Quick: 5`<br>`On Time: 0`<br>`Delayed: 0` |
| 4 | All trips are Delayed | `4 10 20`<br>`25 30 35 40` | `Quick: 0`<br>`On Time: 0`<br>`Delayed: 4` |
| 5 | Boundary case with zero limits | `5 0 0`<br>`0 1 0 2 0` | `Quick: 0`<br>`On Time: 3`<br>`Delayed: 2` |
| 6 | Boundary case with one trip | `1 20 40`<br>`35` | `Quick: 0`<br>`On Time: 1`<br>`Delayed: 0` |

---

## 11. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must use the mandatory classification function.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
