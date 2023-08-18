
#  Traffic_light_controller

This repository contains the Verilog code for a traffic light controller. The controller can be used to control traffic at a T-intersection.
The input to the controller is the current state of the traffic lights, and the output is the next state of the traffic lights. The controller transitions from one state to the next based on the current state of the traffic lights and the input from the user.The controller is designed to ensure that traffic flows smoothly and safely at the intersection.
The controller is tested using a simulator, the simulator allows you to input different traffic scenarios and see how the controller reacts.

## Roadmap

The image v1.img describes the system of the controller where moving from left to right in images describes the orad and traffic conditions
 - M1=Traffic movement from road left to right 
 - M2=Main turn from the main road
 - M3=right to left & top to bottom road
 - S=side turn merge to main road
These specification are also provided with digram in the image for better understanding.
The color dots in front of the M1,M2,MT & S means:
 - RED--STOP
 - YELLOW--WAIT
 - GREEN--GO



## Screenshots

v1.img
The traffic light controller system is designes as where:-
System1                            
- M1=GREEN
- MT=RED
- M2=GREEN
- S =RED
(TMG=M1 remains green for time being)

System2
- M1=GREEN
- MT=RED
- M2=YELLOW
- S =RED
(after TMG;M1 still remains green)

System3
- M1=GREEN
- MT=GREEN
- M2=RED
- S =RED
(After TY time )

System4
- M1=YELLOW
- MT=YELLOW
- M2=RED
- S =RED
(after TTG time)

System5
- M1=RED
- MT=RED
- M2=RED
- S =GREEN
(After TY time)

System6
- M1=RED
- MT=RED
- M2=RED
- S =YELLOW
(after TSG time)

## State diagram
s1.img provided is the state diagram of the the traffic controller
where;
- S1=system 1
- S2=system 2
- S3=system 3
- S4=system 4
- S5=system 5
- S6=system 6
 and time for the traffic to wait is provided as:-
 - TMG=7sec
 - TY=2sec
 - TTG=5sec
 - TSG=3sec

## STATE TABLE

| Sys.No. | PRESENT STATE | INPUT | ABC |ST   | M1 | M2 | MT | S  |
|-------|----------|----------|----------|----------|----------|----------|----------|----------|
|   1   |   000    | ____   |  001    |   1    |   000    |   000    |   000   |   000   |      
|   2   |   001    |   TMG'    |   001    |   0    |   001   |   010   |   100    |   100    |
|       |      |   TMG   |   010   |   1  |      |      |    |     |
|   3   |   010    |   TY'   |    010   |   0    |   001    |   010  |   100    |   100   |
|       |      |   TY'  |   011   |   1   |     |      |      |      |   
|   4   |   011   |   TTG'   |   011    |   0   |   001    |   100  |   001    |   100  |
|       |      | TTG     |   100  |   1  |     |      |      |     |
|   5  |   100    |  TY'    |   100   |   0    |  010    |   100   |   010    |   100   |
|       |      | TY   |   101   |   1   |     |     |     |    |
|   6   |   101    | TSG'    |   101    |   0   |   100   |   100    |   100    |   001   |
|       |     | TSG    |   110  |   1   |     |    |   |     |   
|   7   |   110    |     TY'  |   110    |   0    |  100    |      100 |   100    |  010  |
|       |     |  TY    |   001   |   1   |      |     |      |      |
|   8   |   111    |  ____     |   000    |   0   |  000    |   000 |   000    |  000    |   
