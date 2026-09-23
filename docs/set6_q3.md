# Question 3: Material Safety Check

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

A manufacturing unit checks material stress values against the allowed stress limit. The program must identify whether each sample is safe or unsafe and summarize the results.

---

## 3. Scenario

The program reads a list of material stress values and an allowable stress limit.

A material sample is safe when:

```text
stress <= allowableStress
```

Otherwise, the sample is unsafe.

---

## 4. Tasks to Implement

The program must perform the following tasks:

1. Read the number of material samples, `N`.
2. Read the allowable stress limit, `L`.
3. Read and store the `N` stress values.
4. Count the number of safe samples.
5. Count the number of unsafe samples.
6. Find the maximum stress value.
7. Display the summary in the specified output format.

---

## 5. Function Details

Students must implement and use the following functions:

* Function Name: `isSafeMaterial`
* Arguments: `stress, limit`
* Return type: `Boolean`

* Function Name: `countSafeMaterials`
* Arguments: `stresses, size, limit`
* Return type: `Integer`

* Function Name: `findMaximumStress`
* Arguments: `stresses, size`
* Return type: `Integer`

The functions must not read input, print output, or modify the stored stress values.

---

## 6. Input Format

The first input contains two integers:

```text
N L
```

The second input contains `N` space-separated integers:

```text
s1 s2 ... sN
```

---

## 7. Output Format

The program must print exactly:

```text
Safe: <safe_count>
Unsafe: <unsafe_count>
Maximum stress: <maximum_stress>
```

---

## 8. Constraints and Assumptions

```text
1 <= N <= 1000
0 <= allowableStress <= 100000
0 <= stress <= 100000
```

- All input values are valid integers.
- Exactly `N` stress values will be provided.
- At least one sample will be provided.

---

## 9. Rules and Clarifications

* Rule 1 Safety Check: A sample is safe when `stress <= allowableStress`.
* Rule 2 Unsafe Check: A sample is unsafe when `stress > allowableStress`.
* Rule 3 Maximum Stress: The maximum value is selected among all `N` samples.
* Rule 4 Mandatory Function Usage: All three required functions must be implemented and used.

---

## 10. Test Cases

| Test Case | Purpose | Exact Input | Exact Expected Output |
|---:|---|---|---|
| 1 | Mixed safe and unsafe values | `6 50`<br>`20 45 55 48 70 30` | `Safe: 4`<br>`Unsafe: 2`<br>`Maximum stress: 70` |
| 2 | All values are safe | `4 100`<br>`10 20 30 40` | `Safe: 4`<br>`Unsafe: 0`<br>`Maximum stress: 40` |
| 3 | All values are unsafe | `5 10`<br>`20 35 50 15 12` | `Safe: 0`<br>`Unsafe: 5`<br>`Maximum stress: 50` |
| 4 | Boundary value exactly equal to limit | `4 25`<br>`10 25 24 25` | `Safe: 4`<br>`Unsafe: 0`<br>`Maximum stress: 25` |
| 5 | Boundary case with one sample | `1 40`<br>`40` | `Safe: 1`<br>`Unsafe: 0`<br>`Maximum stress: 40` |
| 6 | Zero value at the boundary is safe | `3 15`<br>`0 15 30` | `Safe: 2`<br>`Unsafe: 1`<br>`Maximum stress: 30` |

---

## 11. Notes

- The candidate may solve the problem using C, C++, or Python.
- The candidate must store the stress values.
- The original order of the values is not required for the final answer.
- Output labels, capitalization, spacing, and ordering must match the specified output format.
