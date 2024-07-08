# staggered_duckling_platooning
Repository for the dpeloyment of staggered duckling platooning for safety-garunteed platooning.

# ENVIRONMENT VARIABLES:

## Spawner
```py
robot_name = os.getenv("ROBOT_NAME")

reset_button = os.getenv('DUCK_SPAWNER_RESET_BUTTON', 4)
spawn_button = os.getenv('DUCK_SPAWNER_SPAWN_BUTTON', 8)

node_distance = os.getenv('DUCK_SPAWNER_NODE_DISTANCE', 0.5)
```


## Mother
```py
robot_name = os.getenv('ROBOT_NAME')

safety_distance = os.getenv('DUCK_SAFETY_DISTANCE', 0.5)

auction_bid_cap = os.getenv('DUCK_AUCTION_TOTAL_BID_CAP', 8)
auction_timeout = os.getenv('DUCK_AUCTION_TIMEOUT', 15)
auction_bid_min = os.getenv('DUCK_AUCTION_BID_MINIMUM', 2.0)
```
## Duckling
```py
robot_name = os.getenv('ROBOT_NAME')

default_bid_value = os.getenv('DUCK_DUCKLING_DEFAULT_BID', 1000000)
navigation_method = os.getenv('DUCK_DUCKLING_NAVIGATION_VALUE', 'latest')
```


# UNIT TESTS:

## Platoon Head
Emulating the behaviour of the HEAD of the platoon filtering nodes. 
The order of launch does not change the functionality.
However, it may change the number of outputs to the observer script.

To see the pose data being published:
`ros2 run staggered_duckling_platooning head_test_observation`

To start the filtering:
`ros2 run staggered_duckling_platooning head_test_mother`

To trigger the node publishing:
`ros2 run staggered_duckling_platooning head_test_spawner`


## Follower Bidding
Emulating the behaviour of a bidding for a following position.
The order of nodes does not change the functionality.
However, the observer must be launched first to view all logs.

To see the pose data being published:
`ros2 run staggered_duckling_platooning follow_test_observation`

To start the auction:
`ros2 run staggered_duckling_platooning follow_test_mother`

To publish a request from ~71m away:
`ros2 run staggered_duckling_platooning follow_test_daughter_distant`

To publish a request from ~21m away:
`ros2 run staggered_duckling_platooning follow_test_daughter_close`

