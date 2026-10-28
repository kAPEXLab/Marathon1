# Obstacle-Avoiding Robot Motion Control

**Level:** Medium  
**Concepts:** Functions, Conditional Statements, Pointers, Input Validation, Integer Arithmetic

## Scenario

A mobile robot uses three ultrasonic sensors to measure the distance from obstacles on its left, front, and right sides. The robot must validate the sensor readings, select a safe movement direction, and calculate the speed of its left and right motors.

## Problem Statement

Write three functions to implement the obstacle-avoidance logic of the robot:

1. Validate the three ultrasonic-sensor readings.
2. Select a movement direction based on the available free space.
3. Calculate the left- and right-motor speeds for the selected direction.

Use the following constants:

~~~c
#define MOVE_STOP       0
#define MOVE_FORWARD    1
#define TURN_LEFT       2
#define TURN_RIGHT      3

#define MIN_DISTANCE_CM   2
#define MAX_DISTANCE_CM   400
#define SAFE_DISTANCE_CM  30
~~~

## Requirements

1. A sensor reading is valid when it is between `2 cm` and `400 cm`, inclusive.
2. A direction is safe when the corresponding distance is greater than or equal to `30 cm`.
3. If the front direction is safe, select `MOVE_FORWARD`.
4. If the front is blocked and both sides are safe, select the side with the greater distance.
5. If the left and right distances are equal and safe, select `TURN_LEFT`.
6. If only the left side is safe, select `TURN_LEFT`.
7. If only the right side is safe, select `TURN_RIGHT`.
8. If all three directions are blocked, select `MOVE_STOP`.
9. The valid range of `base_speed` is `0–100`.
10. Use integer arithmetic only.
11. Validate all output pointers before dereferencing them.
12. Do not modify output variables when a function returns an error.
13. Do not use global variables.
14. Students must write at least five additional test cases for each function.
15. All provided and additional test cases must be implemented and validated using the GoogleTest framework.

## Function Details

### Function 1

- **Name:** `validate_distances`
- **Arguments:**
  - `int left_cm` — Distance measured by the left ultrasonic sensor.
  - `int front_cm` — Distance measured by the front ultrasonic sensor.
  - `int right_cm` — Distance measured by the right ultrasonic sensor.
- **Return Value:** `int` — `0` if all readings are valid; `-1` if any reading is outside the valid range.
- **Description:** Validate that all three sensor readings are between `MIN_DISTANCE_CM` and `MAX_DISTANCE_CM`, inclusive.

~~~c
int validate_distances(int left_cm, int front_cm, int right_cm);
~~~

### Function 2

- **Name:** `choose_direction`
- **Arguments:**
  - `int left_cm` — Valid left-side distance.
  - `int front_cm` — Valid front distance.
  - `int right_cm` — Valid right-side distance.
  - `int *out_direction` — Output pointer for the selected direction.
- **Return Value:** `int` — `0` on success; `-1` if any sensor reading is invalid or `out_direction` is `NULL`.
- **Description:** Select `MOVE_FORWARD`, `TURN_LEFT`, `TURN_RIGHT`, or `MOVE_STOP` according to the specified obstacle-avoidance rules.

~~~c
int choose_direction(int left_cm, int front_cm, int right_cm,
                     int *out_direction);
~~~

### Function 3

- **Name:** `calculate_motor_speeds`
- **Arguments:**
  - `int direction` — Direction selected by `choose_direction`.
  - `int base_speed` — Requested motor speed in the range `0–100`.
  - `int *out_left_speed` — Output pointer for the left-motor speed.
  - `int *out_right_speed` — Output pointer for the right-motor speed.
- **Return Value:** `int` — `0` on success; `-1` for an invalid direction, invalid speed, or null output pointer.
- **Description:** Calculate the motor speeds according to the following rules:
  - `MOVE_STOP`: both motor speeds are `0`.
  - `MOVE_FORWARD`: both motor speeds are equal to `base_speed`.
  - `TURN_LEFT`: left speed is `base_speed / 2` and right speed is `base_speed`.
  - `TURN_RIGHT`: left speed is `base_speed` and right speed is `base_speed / 2`.

~~~c
int calculate_motor_speeds(int direction, int base_speed,
                           int *out_left_speed,
                           int *out_right_speed);
~~~

## Solution Approach

*Validate all sensor readings before selecting a direction. Give forward movement the highest priority. If the front is blocked, compare the safe side distances and select the side with more free space. Convert the selected direction into differential motor-speed commands using integer arithmetic. Validate all pointers and inputs before modifying output variables.*

## Tasks to Perform

1. Define the movement-direction and distance constants.
2. Implement `validate_distances`.
3. Implement `choose_direction`.
4. Implement `calculate_motor_speeds`.
5. Validate sensor readings, speed values, direction values, and output pointers.
6. Store results through output pointers only after successful validation.
7. Implement the provided test cases using the GoogleTest framework.
8. Write at least five additional test cases for each function.
9. Validate all additional test cases using the GoogleTest framework.

## Test Cases

### Test Cases for `validate_distances`

| # | `left_cm` | `front_cm` | `right_cm` | Expected Return | Notes |
|---|---:|---:|---:|---:|---|
| 1 | 100 | 150 | 120 | 0 | All sensor readings are valid |
| 2 | 1 | 100 | 100 | -1 | Left reading is below the minimum range |

### Test Cases for `choose_direction`

| # | `left_cm` | `front_cm` | `right_cm` | Expected Return | Expected `*out_direction` | Notes |
|---|---:|---:|---:|---:|---|---|
| 1 | 20 | 100 | 20 | 0 | `MOVE_FORWARD` | Front direction is safe |
| 2 | 70 | 20 | 45 | 0 | `TURN_LEFT` | Front is blocked and left has more free space |

### Test Cases for `calculate_motor_speeds`

| # | `direction` | `base_speed` | Expected Return | Expected `*out_left_speed` | Expected `*out_right_speed` | Notes |
|---|---|---:|---:|---:|---:|---|
| 1 | `MOVE_FORWARD` | 80 | 0 | 80 | 80 | Both motors run at the base speed |
| 2 | `TURN_LEFT` | 75 | 0 | 37 | 75 | Integer division is used for the left motor |
