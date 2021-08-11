# Project pipeline 

##  Analyzing data from Sensor fusion
At first we taking sensor fusion data of other vehicles from the simulator , these data include X,Y location , Velocity components in X,Y ,S and D values and the Car_ID<br>

Taking these data and start analyzing to extract useful information from it like:<br>
 - Deciding the lane , by checking the d value comming from sensor fusion and compare it with the width of each lane to decide the lane (see lines from 262 to 271).
 - Getting the car speed and S value from sensor fusion data 
 - Estimating the car s position after executing previous trajectory
 - Comparing with the Car_lane to decide if the car is in our lane or its left of our car or right of our car ( see lines from 281 to 290)



##  Taking decicion based on data analyzation 
Second we started to decide what to do in each case of the following : ( see lines from 294 to 315 )
  - The car is in front of us and there is no car on left : change lane to left 
  - The car is in front of us and there is no car on right : change lane to right 
  - The car is in front of us and there is the left and right have cars  : slow down 
  - The car is not ahead and we are not in the lane center : back to center if available
  - Try to reach maximum speed by increase speed gradually 




## Trajectory planner 
we use result from behaviour to set the current lane and speed then compute a trajectory using the previous path generated so the result path will be more smooth we compute the trajectory by using last 2 point from previous path or some transformation from the initial position of the car and 3 points far from the car(30s,60s, 90s) then transform all these points into the car coordinates then compute spline and transform it to global coordinates from car coordinates then to ensure continuity we add all previous path points
(see lines from 318 to 417)
