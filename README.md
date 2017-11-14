# HW-5-SIS

Abstract:

This Repository contains the following items:

1- My code that i used to move the robot and collect the data.

2- The graphs generated from the motion of the robot.

3- The raw data that is recorded  from the sensors onboard the robot during its motion.

4- the data recived from my colleague.

5- the codes and trajectory graphs generated after applying some algorithms.

My colleague that i shared the data with him is: Bakhtawar Rehman.


Introduction:

The robot that i built is a wall following robot, i choose ultrasonic sensor and gyroscope to be the onboard sensors for the robot, the robot depends on the readings from the ultrasonic sesnor to correct its path that it follows and its distance from the wall, during the motion of the robot, the gyroscope records the angles resulted form the drifts that the robot took dueto the change of the direction of the wall from the horizontal to the vertical side.

The data recorded from the sensors onboard the robot during its motion is exported as excel file, and also the graph of this data is included in this repositiory.

The algorithm followed to get trace segmentation from wall following trajectory:

Inputs:
odometry and sensor measurements {(xk, yk, blk, wrk)}

Outputs:
line segments {(li, θi, ti)}

Initialization: with the first two points
l =((x2 − x1)^2 + (y2 − y1)^2)^(1/2)
θ = arctan(y2 − y1, x2 − x1)
t = STRAIGHT

record segment beginning: (x^b, y^b) = (x1, y1)

Parameters:
κ: threshold for line fitting distance
L: minimum length for line segments

while there is an input (xk, yk, blk, wrk):
compute (l', θ')for line (x^b, y^b) → (xk, yk)
 if blk == 1 and blk−1 == 0 then
 output segment (l', θ', t)
create new segment (x^b, y^b) = (xk, yk), l = 0
t = LEFT
else if wrk == 0 and wrk−1 == 1 then
output segment (l', θ', t)
create new segment (x^b, y^b) = (xk, yk), l = 0
 t = RIGHT
 else
 d = | cos(θ)(yk − yb) − sin(θ)(xk − xb)|
d¯=p(xk − xk−1)^2 + (yk − yk−1)^2
if d > κd¯ and l > L then % create a new segment
 output current segment (l, θ, t)
 create new segment (x^b, y^b) = (xk−1, yk−1), l = d¯
 t = STRAIGHT
 else % extend current segment
 θ = θ', l = l'

    end if
   end if
 end while







