# RL-ros-planar
Reinforcement learning with ROS and planar robot

The simulation is run in Gazebo with a cam view from RVIZ. 
![Alt Text](https://github.com/androbaza/RL-ros-planar/blob/main/1.gif)

### Parameters modified:

* number of epochs decreased to 50, so that the process will end in few hours
* alpha, the learning rate, was decreased to 0.5, no effect was noticed
* gamma was chosen to be 0.95, so that algorithm prepers higher reward later, than small reward in a short time. Not really applicable to this simulation, as there is only one type of reward.
* epsilon was chosen to be 0.95 with decay of 0.93 each epoch. So that it is just above 0.02 at 50th epoch. This should have made the algorithm more "random" in the beginning and less random closer to the end. After training, I believe the initial value was too high, as it could be seen from training graph below - there were not much more scores above 0 closer to 50th epoch.
* the "actions" for each joint were tuned. The base motor and 2nd motor could only go ±5 degrees, 3rd and 4th ±10 degrees and 5th and 6th ±15 degrees. This was made so that there is higher chance for the end effector to reach the aim.
* reward for each step was decreased to -1.5. 
* reward for failing was decreased to -30.
* reward for succes was increased to 70. I guess I should have increased it even more, as there were a lot of negative scores even in case of success.

The training curve could be seen below:
![Alt Text](https://github.com/androbaza/RL-ros-planar/blob/main/2.png)

### Conclusion
Overall, the learned q-table test did not work as intended - the robot was just going straight to right side after initiation. Probably low number of epochs affected it. However, higher number was not doable due to high CPU usage for a few hours in a row and overheating.
