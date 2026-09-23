# Question 5: Equipment Inspection Summary

## 1. Question Details

| Attribute | Details |
|---|---|
| Difficulty | Easy to Medium |
| Supported Languages | C, C++, or Python |
| Internet Access | Not allowed |
| AI Tools | Not allowed |
| Notes or Reference Material | Not allowed |

---

## 2. Introduction

A workshop maintains inspection records for machines. Each record contains basic operating values and a summary status. The program must validate each record, calculate a simple condition score, and report the inspection summary.

---

## 3. Scenario

Each inspection record contains:

| Field | Description |
|---|---|
| Machine ID | Unique machine number |
| Temperature | Machine temperature in degrees Celsius |
| Vibration | Vibration level |
| Pressure | Operating pressure |

A record is valid when:

```text
machineId > 0
temperature >= 0
vibration >= 0
pressure > 0
```

For every valid record, calculate:

```text
departure = 0, when temperature <= 70
           (temperature - 70) * 2, when temperature > 70

vibrationPenalty = vibration * 5
pressureBonus = 0, when pressure >= 20
                (20 - pressure) * 1.5, when pressure < 20

conditionScore = 100 - departure - vibrationPenalty - pressureBonus
```

The score must be limited to the range `0` to `100`.

| Score | Category |
|---:|---|
| `70` to `100` | Good |
| Less than `70` | Service |
| Invalid record | Invalid |

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read and store all machine inspection records.
2. Validate every record.
3. Calculate and store the condition score and category.
4. Count valid and invalid records.
5. Count records in each category.
6. Calculate the average condition score of valid records.
7. Find the valid record with the lowest score.
8. Display the summary in the specified output format.

---

## 5. Function Details

Students must implement and use the following functions:

* Function Name: `isValidInspection`
* Arguments: `record`
* Return type: `Boolean`

* Function Name: `calculateConditionScore`
* Arguments: `record`
* Return type: `Real Number`

* Function Name: `processAllInspections`
* Arguments: `records, size`
* Return type: None or Void

* Function Name: `countByCategory`
* Arguments: `records, size, requiredCategory`
* Return type: `Integer`

* Function Name: `findWorstInspection`
* Arguments: `records, size`
* Return type: `Integer`

* Function Name: `calculateAverageScore`
* Arguments: `records, size`
* Return type: `Real Number`

The functions must not read input or print output.

---

## 6. Input Format

The first input contains one integer:

```text
N
```

The next `N` lines contain:

```text
machineId temperature vibration pressure
```

---

## 7. Output Format

When at least one valid record exists, print exactly:

```text
Valid records: <valid_count>
Invalid records: <invalid_count>
Good: <good_count>
Service: <service_count>
Average score: <average_score>
Worst machine ID: <machine_id>
Worst score: <score>
```

When no valid record exists, print exactly:

```text
Valid records: 0
Invalid records: <invalid_count>
Good: 0
Service: 0
Average score: 0.00
No valid record
```

The average must have exactly two digits after the decimal point.

---

## 8. Constraints and Assumptions

```text
1 <= N <= 1000
1 <= machineId <= 100000
0 <= temperature <= 200
0 <= vibration <= 50
1 <= pressure <= 100
```

- All input values are valid real numbers where needed.
- Exactly `N` machine inspection records will be provided.
- The candidate may use a structure or class for each record.

---

## 9. Rules and Clarifications

* Rule 1 Valid Record: A record is valid only when all required fields satisfy the validity rule.
* Rule 2 Score Limit: The final condition score must be clamped between `0` and `100`.
* Rule 3 Category: Good is used for `score >= 70`; otherwise the record is Service.
* Rule 4 Worst Record: The record with the lowest valid score is selected. If there is a tie, use the smaller Machine ID.
* Rule 5 Mandatory Function Usage: All required functions must be implemented and used.

---

## 10. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Mixed valid and invalid records | `4`<br>`101 60 2 20`<br>`102 80 5 25`<br>`103 90 4 15`<br>`104 -1 0 10` | `Valid records: 3`<br>`Invalid records: 1`<br>`Good: 1`<br>`Service: 2`<br>`Average score: 59.17`<br>`Worst machine ID: 103`<br>`Worst score: 32.50` |
| 2 | Equal lowest scores use smaller Machine ID | `3`<br>`201 75 3 20`<br>`199 75 3 20`<br>`205 60 1 15` | `Valid records: 3`<br>`Invalid records: 0`<br>`Good: 3`<br>`Service: 0`<br>`Average score: 79.17`<br>`Worst machine ID: 199`<br>`Worst score: 75.00` |
| 3 | All records are invalid | `3`<br>`-1 50 0 15`<br>`302 0 0 0`<br>`303 70 -1 20` | `Valid records: 0`<br>`Invalid records: 3`<br>`Good: 0`<br>`Service: 0`<br>`Average score: 0.00`<br>`No valid record` |
| 4 | Score reaches the lower clamp | `2`<br>`401 100 20 5`<br>`402 0 0 20` | `Valid records: 2`<br>`Invalid records: 0`<br>`Good: 1`<br>`Service: 1`<br>`Average score: 50.00`<br>`Worst machine ID: 401`<br>`Worst score: 0.00` |
| 5 | Exact boundary value | `3`<br>`501 70 0 20`<br>`502 65 0 20`<br>`503 80 0 20` | `Valid records: 3`<br>`Invalid records: 0`<br>`Good: 3`<br>`Service: 0`<br>`Average score: 100.00`<br>`Worst machine ID: 501`<br>`Worst score: 100.00` |
| 6 | Boundary case with one valid record | `1`<br>`600 50 0 20` | `Valid records: 1`<br>`Invalid records: 0`<br>`Good: 1`<br>`Service: 0`<br>`Average score: 100.00`<br>`Worst machine ID: 600`<br>`Worst score: 100.00` |

---

## 11. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must store the machine inspection records.
- A structure or class may be used for the record data.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
