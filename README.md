# Extended-Kalman-Filter
Object Oriented collection of Extended Kalman Filter.
![EKF Trajectory Tracking Animation](https://andrewadie.com/wp-content/uploads/2026/05/ekf_trajectory.gif)

The goal of this tool is to prototype an EKF solution for C++ implementation in the future. It's not designed to be production code as much as a personal implementation of a well-known algorithm for fine-grain control.

Mk I - Implementation on dataset with simulation, Object-Oriented for future port to C++

Future Updates:
- Improve dyanmics/observation system modularity, separate the dynamics and observation matrices to hotswap.
- Dynamically update observations based on user-specified sensor placements. Sensor placements are hardcoded in the math and the code, make this dynamic
- Port to C++ for use in projects


FAQ:
Why not Rust? Because I'm familiar with the C family of programming languages and am more focused on the math and code implementation than langauge selection

How would you tune this algorithm's noise for accuracy? It's actually pretty brittle if the Q and R (process/measurement covariance matrices) are set as they are in this code. A better approach would be an adaptive filtering situation. 

Would reducing matrix magnitude at greater distances improve accuracy? No, it would make the estimator overconfident resulting in faulty estimates, unwanted correlation, and error propegation. The better way to improve this would be to reduce the ACTUAL noise (from the hardware) or reconsider sensor placement. These placements are non-optimal since information "meaningfulness" per update drops off per arclength farther away. Spreading the sensors out along the trajectory we be the higher leverage move.
