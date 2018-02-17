# CarND-PID-Controller
Self-Driving Car Engineer Nanodegree Program: PID Controller Project

---

[//]: # (Image References)

[image1]: ./pid.png "PID"

## Discussion of Hyperparameter Tuning

* Effect of individual parameters on the control output was observed:
 * P-only - With P-only parameter set e.g. p, i, d = [1.0, 0.0, 0.0] - It was observed that the vehicle was swinging left and right. Swing amount looked proportional to the p parameter.
 * D-only - With D-only parameter set e.g. p, i, d = [0.0, 0.0, 1.0] - It was observed that the control output was not correcting the trajectory of the vehicle or was very slow at doing so.
 * I-only - With I-only parameter set e.g. p, i, d = [0.0, 1.0, 0.0] - It was observed that the vehicle was rotating around instead of making forward progress. Looking at the final values below, may be a value of 1.0 was high for I param. But even with value of 0.001, vehicle was making turns after going some distance forward.
 * PD Control - the combination of P and D looked promising as D param seemed to smooth out swings introduced by P param.
 * PID Control - a small addition of Integral controller to PD seemed to help (Although the given track was seem to be completed by PD controller). As explained in lesson, I controller helps with systematic bias. Lower values of P param seemed to smooth out the swings seen ealier so P param was iteratively tuned down. Higher values of D param seemed to help keep vehicle centered, so it was tuned up. Final values - p, i, d = [0.2, 0.001, 3.0]

 Overall effects of the P, I, D params was in accordance with below figure seen in lesson:

 ![alt text][image1]