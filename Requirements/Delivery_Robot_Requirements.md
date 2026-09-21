# Autonomous Delivery Robot — Requirements

## Functional and Behavioral Requirements

| Req. ID | Requirement |
|---|---|
| R1 | The robot shall enter the IDLE state when it is switched on. |
| R2 | The robot shall remain IDLE until a valid delivery request is received. |
| R3 | Upon receiving a delivery request, the robot shall transition from IDLE to NAVIGATING. |
| R4 | While navigating, the robot shall detect obstacles and transition to AVOIDING_OBSTACLE when an obstacle is detected. |
| R5 | After successfully avoiding an obstacle, the robot shall return from AVOIDING_OBSTACLE to NAVIGATING. |
| R6 | The robot shall transition from NAVIGATING to DELIVERING only after reaching the destination. |
| R7 | The robot shall complete the delivery before transitioning from DELIVERING to RETURNING. |
| R8 | If the battery becomes critically low during navigation, the robot shall stop the delivery journey and transition to RETURNING. |
| R9 | When the robot reaches the warehouse, it shall transition from RETURNING to IDLE. |
| R10 | The robot shall not transition directly from IDLE to DELIVERING or from AVOIDING_OBSTACLE to DELIVERING. |