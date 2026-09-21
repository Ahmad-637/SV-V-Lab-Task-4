# Autonomous Delivery Robot — State Model

## States

| State ID | State |
|---|---|
| S1 | IDLE |
| S2 | NAVIGATING |
| S3 | AVOIDING_OBSTACLE |
| S4 | DELIVERING |
| S5 | RETURNING |

## State Descriptions

### IDLE
The robot is waiting for a delivery request.

### NAVIGATING
The robot is travelling toward the delivery destination.

### AVOIDING_OBSTACLE
The robot has detected an obstacle and is temporarily handling it.

### DELIVERING
The robot has reached the destination and is delivering the package.

### RETURNING
The robot is travelling back to the warehouse.

## Events / Conditions

| Event ID | Event / Condition |
|---|---|
| E1 | Robot Switched On |
| E2 | Delivery Request Received |
| E3 | Destination Reached |
| E4 | Delivery Successful |
| E5 | Warehouse Reached |
| E6 | Obstacle Detected |
| E7 | Obstacle Avoided |
| E8 | Critical Battery |