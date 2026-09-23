# Question 4: Temperature Trend Analysis

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

A machine monitor records temperature readings over time. The program must calculate the average temperature, identify the hottest reading, and count how many readings exceed a warning threshold.

---

## 3. Scenario

The system records `N` temperature values. The program must:

1. Calculate the average temperature.
2. Find the maximum temperature.
3. Count the number of readings above a threshold temperature.

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read the number of readings, `N`.
2. Read the warning threshold, `T`.
3. Read and store the `N` temperature values.
4. Calculate the average temperature.
5. Find the maximum temperature.
6. Count how many temperature values are greater than `T`.
7. Display the result in the specified output format.

---

## 5. Function Details

Students must implement and use the following functions:

* Function Name: `calculateAverageTemperature`
* Arguments: `temperatures, size`
* Return type: `real number`

* Function Name: `findMaximumTemperature`
* Arguments: `temperatures, size`
* Return type: `real number`

* Function Name: `countHotReadings`
* Arguments: `temperatures, size, threshold`
* Return type: `Integer`

The functions must not read input, print output, or modify the stored temperature values.

---

## 6. Input Format

The first input contains two integers:

```text
N T
```

The second input contains `N` space-separated integers:

```text
t1 t2 ... tN
```

---

## 7. Output Format

The program must print exactly:

```text
Average temperature: <average_temperature>
Maximum temperature: <maximum_temperature>
Hot readings: <hot_count>
```

The average must be displayed with exactly two digits after the decimal point.

---

## 8. Constraints and Assumptions

```text
1 <= N <= 1000
0 <= threshold <= 1000
0 <= temperature <= 1000
```

- All input values are valid integers.
- Exactly `N` temperature values will be provided.
- At least one reading will be provided.

---

## 9. Rules and Clarifications

* Rule 1 Average Temperature: Use all `N` readings in the calculation.
* Rule 2 Hot Reading: A reading is counted when `temperature > threshold`.
* Rule 3 Maximum Temperature: The largest reading among all `N` values is selected.
* Rule 4 Mandatory Function Usage: All three required functions must be implemented and used.

---

## 10. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Normal temperature trend | `6 40`<br>`20 35 50 45 60 30` | `Average temperature: 40.00`<br>`Maximum temperature: 60`<br>`Hot readings: 2` |
| 2 | All readings are below threshold | `5 80`<br>`20 30 25 40 50` | `Average temperature: 33.00`<br>`Maximum temperature: 50`<br>`Hot readings: 0` |
| 3 | All readings are above threshold | `4 10`<br>`25 30 40 50` | `Average temperature: 36.25`<br>`Maximum temperature: 50`<br>`Hot readings: 4` |
| 4 | Boundary case with threshold equal to a reading | `5 35`<br>`10 35 30 40 35` | `Average temperature: 30.00`<br>`Maximum temperature: 40`<br>`Hot readings: 1` |
| 5 | Boundary case with one reading | `1 20`<br>`25` | `Average temperature: 25.00`<br>`Maximum temperature: 25`<br>`Hot readings: 1` |
| 6 | Mixed values with repeated maximum | `6 50`<br>`45 50 60 50 40 30` | `Average temperature: 45.83`<br>`Maximum temperature: 60`<br>`Hot readings: 1` |

---

## 11. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must store the temperature readings.
- The original order of the readings must be preserved.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
