# Robot Wheel Encoder Distance Analysis

**Level:** Medium  
**Concepts:** Arrays, Functions, Loops, Input Validation, Integer Arithmetic

## Scenario

A mobile robot records pulse counts from a wheel encoder at regular time intervals. The recorded samples must be validated, added to determine the total pulse count, and converted into the distance travelled by the robot.

## Problem Statement

Write three functions to analyse the wheel-encoder samples of a mobile robot:

1. Validate the encoder samples stored in an array.
2. Calculate the total number of encoder pulses.
3. Calculate the distance travelled by the robot in millimetres.

Use the following constants:

~~~c
#define MIN_PULSE_COUNT       0
#define MAX_PULSE_COUNT       10000
#define MIN_PULSES_PER_REV    1
#define MIN_WHEEL_CIRCUM_MM   1
~~~

## Requirements

1. The encoder samples must be stored in an integer array.
2. The number of samples must be greater than `0`.
3. Each encoder sample must be between `0` and `10000`, inclusive.
4. The total pulse count must be calculated by adding all valid encoder samples.
5. Use a `long` variable while calculating the total pulse count.
6. `pulses_per_revolution` must be greater than or equal to `1`.
7. `wheel_circumference_mm` must be greater than or equal to `1`.
8. Calculate the distance using the following formula:

   `distance_mm = round((total_pulses × wheel_circumference_mm) / pulses_per_revolution)`

9. Use integer arithmetic only.
10. Perform round-to-nearest by adding `pulses_per_revolution / 2` before division.
11. Use a `long` intermediate for multiplication during the distance calculation.
12. Do not use global variables.
13. Functions that perform calculations must return the calculated value directly.
14. Return `-1` when an input is invalid.
15. Students must write at least five additional test cases for each function.
16. All provided and additional test cases must be implemented and validated using the GoogleTest framework.

## Function Details

### Function 1

- **Name:** `validate_encoder_samples`
- **Arguments:**
  - `const int samples[]` — Array containing encoder pulse-count samples.
  - `int sample_count` — Number of elements in the array.
- **Return Value:** `int` — `0` if all samples are valid; `-1` if the array pointer is `NULL`, the sample count is invalid, or any sample is outside the valid range.
- **Description:** Validate that the sample array is not `NULL`, `sample_count` is greater than `0`, and every sample is between `MIN_PULSE_COUNT` and `MAX_PULSE_COUNT`, inclusive.

~~~c
int validate_encoder_samples(const int samples[], int sample_count);
~~~

### Function 2

- **Name:** `calculate_total_pulses`
- **Arguments:**
  - `const int samples[]` — Array containing encoder pulse-count samples.
  - `int sample_count` — Number of elements in the array.
- **Return Value:** `long` — Total number of encoder pulses on success; `-1` if the array pointer is `NULL`, the sample count is invalid, or any encoder sample is invalid.
- **Description:** Validate the encoder samples and calculate their sum using a `long` accumulator. Return the calculated total pulse count directly from the function.

~~~c
long calculate_total_pulses(const int samples[], int sample_count);
~~~

### Function 3

- **Name:** `calculate_distance_mm`
- **Arguments:**
  - `long total_pulses` — Total number of valid encoder pulses.
  - `int pulses_per_revolution` — Number of encoder pulses generated for one complete wheel revolution.
  - `int wheel_circumference_mm` — Wheel circumference in millimetres.
- **Return Value:** `long` — Calculated distance in millimetres on success; `-1` if `total_pulses` is negative, `pulses_per_revolution` is less than `1`, or `wheel_circumference_mm` is less than `1`.
- **Description:** Calculate and return the distance travelled using integer arithmetic. Perform round-to-nearest and use a `long` intermediate for multiplication.

~~~c
long calculate_distance_mm(long total_pulses,
                           int pulses_per_revolution,
                           int wheel_circumference_mm);
~~~

## Solution Approach

*Traverse the sample array to validate every encoder reading. Use a `long` accumulator to add all valid samples and return the total directly. To calculate the distance, multiply the total pulse count by the wheel circumference, add half of the pulses-per-revolution value for rounding, and divide by the pulses per revolution. Return `-1` when an input is invalid.*

## Tasks to Perform

1. Define the encoder-validation constants.
2. Implement `validate_encoder_samples`.
3. Implement `calculate_total_pulses`.
4. Implement `calculate_distance_mm`.
5. Use loops to process the encoder-sample array.
6. Use a `long` accumulator when calculating the total pulse count.
7. Return the calculated total pulse count directly from `calculate_total_pulses`.
8. Use integer arithmetic with round-to-nearest when calculating distance.
9. Return the calculated distance directly from `calculate_distance_mm`.
10. Validate array pointers, array size, encoder samples, and robot-wheel parameters.
11. Return `-1` for invalid inputs.
12. Implement the provided test cases using the GoogleTest framework.
13. Write at least five additional test cases for each function.
14. Validate all additional test cases using the GoogleTest framework.

## Test Cases

### Test Cases for `validate_encoder_samples`

| # | `samples` | `sample_count` | Expected Return | Notes |
|---|---|---:|---:|---|
| 1 | `{100, 120, 90, 110}` | 4 | 0 | All encoder samples are within the valid range |
| 2 | `{100, 120, -5, 110}` | 4 | -1 | One encoder sample is below the minimum valid value |

### Test Cases for `calculate_total_pulses`

| # | `samples` | `sample_count` | Expected Return | Notes |
|---|---|---:|---:|---|
| 1 | `{100, 120, 90, 110}` | 4 | 420 | Sum of all four encoder samples |
| 2 | `{250, 300, 450}` | 3 | 1000 | Sum of all three encoder samples |

### Test Cases for `calculate_distance_mm`

| # | `total_pulses` | `pulses_per_revolution` | `wheel_circumference_mm` | Expected Return | Notes |
|---|---:|---:|---:|---:|---|
| 1 | 1000 | 500 | 200 | 400 | Two wheel revolutions result in a distance of 400 mm |
| 2 | 251 | 500 | 200 | 100 | Calculated distance of 100.4 mm is rounded to 100 mm |
