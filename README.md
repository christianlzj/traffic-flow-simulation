# Traffic Flow
The goal is to model the behavior of freeway traffic, outlined in Chapter 8.2 of "Modeling and Simulation: An Application Oriented Approach" by Bungartz et al. (2014). The algorithm updates the state of each vehicle $i$ in three steps, outlined as follows:
1. **Accelerate**: $v_i := min(v_i+1,\, v_{max})$
2. **Decelerate**: $v_i := d(i,\,i+1)$, if $v_i>d(i,\,i+1)$
3. **Move**: vehicle $i$ moves $v_i$ cells forward

In order to more realistically model driver behavior, we also experiment with implementing a random dally factor between the deceleration and move steps. That is,
1. **Random Dally**: $v_i := max(v_i-1,\, 0)$ with probability $p<1$

Finally, we extend the one-lane traffic simulation to a two-lane system that supports cautious lane changes. We make the following assumptions regarding the model and driver behavior in making this extension:
1. Both lanes have a maximum possible speed, in which the maximum speed of the left lane is greater than or equal to the maximum speed of the right lane.
2. If a driver will not need to decelerate in their current lane, they will stay in their current lane (i.e. lane changes only occur when necessary).
3. If a driver must decelerate in their current lane, they must ensure that they will be able to drive at their current speed in the adjacent lane without causing an accident with the cars that would be in front of or behind them. The driver must also consider the possibility of other cars changing lanes as well, and ensure that there is no chance of a collision.
4. If the driver cannot change lanes safely and must decelerate in their current lane, they must do so.

Proofs of implementation and analysis of the above algorithms and simulations are included in traffic_flow.pdf.