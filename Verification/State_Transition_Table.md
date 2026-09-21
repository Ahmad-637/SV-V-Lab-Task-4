# State Transition Table

| Current State | Event / Condition | Next State | Requirement |
|---|---|---|---|
| IDLE | Delivery Request Received | NAVIGATING | R2, R3 |
| NAVIGATING | Obstacle Detected | AVOIDING_OBSTACLE | R4 |
| AVOIDING_OBSTACLE | Obstacle Avoided | NAVIGATING | R5 |
| NAVIGATING | Destination Reached | DELIVERING | R6 |
| DELIVERING | Delivery Successful | RETURNING | R7 |
| NAVIGATING | Critical Battery | RETURNING | R8 |
| RETURNING | Warehouse Reached | IDLE | R9 |

## Invalid Transitions

| Invalid Transition | Reason |
|---|---|
| IDLE → DELIVERING | Violates R10 because the robot must first receive a request and navigate to the destination. |
| AVOIDING_OBSTACLE → DELIVERING | Violates R10 because the robot must first successfully avoid the obstacle and return to NAVIGATING. |
| IDLE → RETURNING | No delivery journey has started, so there is no valid return journey. |
| NAVIGATING → IDLE | The robot cannot become idle directly while a delivery journey is in progress. |

# Verification Activity

## Check 1 — Invalid Transition

### IDLE → DELIVERING

This transition must not be allowed.

The robot must follow:

IDLE → NAVIGATING → DELIVERING

The direct IDLE → DELIVERING transition violates R10.

## Check 2 — Missing Transition

If the robot moves from:

NAVIGATING → AVOIDING_OBSTACLE

but there is no transition from AVOIDING_OBSTACLE back to NAVIGATING, the robot becomes stuck in obstacle-avoidance mode.

The required transition is:

AVOIDING_OBSTACLE → NAVIGATING

This satisfies R5.

## Check 3 — Obstacle During Delivery

The transition:

AVOIDING_OBSTACLE → DELIVERING

must not be allowed.

The robot must first avoid the obstacle and return to navigation:

AVOIDING_OBSTACLE → NAVIGATING → DELIVERING

This satisfies R10.

# Valid State Flow

IDLE
↓
NAVIGATING
↓
AVOIDING_OBSTACLE
↓
NAVIGATING
↓
DELIVERING
↓
RETURNING
↓
IDLE

## Critical Battery Flow

NAVIGATING
↓
Critical Battery
↓
RETURNING
↓
Warehouse Reached
↓
IDLE

# Commit 4 — Verification Against Requirements

## Verification Results

### Check 1 — Invalid Transition

IDLE → DELIVERING is an invalid transition.

It violates R10 because the robot must first receive a delivery request and navigate to the destination.

Required flow:

IDLE → NAVIGATING → DELIVERING

### Check 2 — Missing Transition

If AVOIDING_OBSTACLE has no transition back to NAVIGATING, the robot cannot continue its delivery journey.

Required transition:

AVOIDING_OBSTACLE → NAVIGATING

This satisfies R5.

### Check 3 — Obstacle During Delivery

AVOIDING_OBSTACLE → DELIVERING is not allowed.

The robot must first successfully avoid the obstacle and return to NAVIGATING.

Required flow:

AVOIDING_OBSTACLE → NAVIGATING → DELIVERING

This satisfies R10.

## Verification Conclusion

All valid state transitions were checked against the requirements.

The identified invalid transitions must not be included in the state model.
