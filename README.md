# CarND-Controls-PID

The purpose of the project is to implement a PID Controller that will be able to drive a vehicle around the track using the Term2 simulator.

---

### Steps of implementation

1. Initialize the PID with values for the tunning constants Kp, Ki and Kd that allow the vehicle to correctly drive around the track
   - The correct values for the tunning constants have been selected through trial and error method
   - Below are some of the tested values, in ascending order from worst to best (comments on each set of settings are made with respect to previous line of settings):
   
   | Kp | Ki | Kd | Result |
   | -- | -- | -- | -- |
   | 1.00 | 0.00 | 0.00 | a lot of oversteering, car eventually leaves the track |
   | 1.00 | 0.00 | 1.00 | less oversteering, car moves from side to side, car eventually leaves the track |
   | 0.50 | 0.00 | 0.50 | less oversteering, car moves from side to side, eventually leaves the track |
   | 0.50 | 0.00 | 1.00 | oversteering, car moves from side to side, car stays on track |
   | 0.50 | 0.00 | 1.50 | oversteering, car moves from side to side, car stays on track |
   | 0.25 | 0.00 | 1.50 | car is a lot more centered on the track, less movement from left to right, car stays on track |
   | 0.15 | 0.00 | 1.50 | car is a lot more centered on the track, less movement from left to right, car stays on track |
   | 0.10 | 0.00 | 1.50 | car is centered on the track most of the time, car is stable and stays on track |

2. Calculate the steering value
   - The steering value has been computed using the following formula:
   ![PID mathematical formula](https://raw.githubusercontent.com/sorix6/CarND-PID-Control-Project/master/images/PID_formula.JPG)

### Influence of tunning constants on the vehicle behaviour

* Kp - the proportional term 
  - Deals with how far the vehicle is from its target(the center of the road) and how hard does it need to steer back in order to reach that target
  - Setting a large value makes the car oscilate a lot on the road
  - It need to be counter balanced by the Kd 

* Ki - the integral term
  - Deals with the fact that the vehicle might pull to the left of to the right, due to wheels not being pefectly aligned
  - This constant has been set to 0.0 while using the simulator 

* Kd - the derivative term
  - Deals with reducing oscilation around the center
  - It aims at flattening the error trajectory into a horizontal line

### Final tunning values and results

* The selected tunning values are the following:

| Kp | Ki | Kd |
| -- | -- | -- |
| 0.10 | 0.00 | 1.50 |


* The result of the simulation using these parameters can be found in **videos/track.mp4**.

### Resources used for implementation

Apart from the lecture materials, the following resources have been used during the implementation of this project:

1. [Self-Driving Car Project Q&A | PID Controller](https://www.youtube.com/watch?v=YamBuzDjrs8&feature=youtu.be)
2. [PID Controller](https://en.wikipedia.org/wiki/PID_controller)
