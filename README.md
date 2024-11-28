# KALMAN-FILTERING
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
 
    
</head>
<body>
    <h1>Kalman Filtering in 2D</h1>
    <p>
        This project demonstrates the implementation of a <strong>Kalman filter</strong> for 2D object tracking. 
        The Kalman filter combines noisy measurements and system dynamics to provide smoothed position estimates.
    </p>

   <h2>Features</h2>
    <ul>
        <li>2D object tracking using a Kalman filter.</li>
        <li>Simulation of true positions and noisy measurements.</li>
        <li>Visualization of trajectories (true, noisy, and estimated).</li>
    </ul>

  <h2>Prerequisites</h2>
    <ul>
        <li>Python 3.x</li>
        <li>NumPy</li>
        <li>Matplotlib</li>
    </ul>

  <h2>Code Snippets</h2>
    
  <h3>Prediction Step</h3>
    <pre><code>def predict(x, P):
    x = F @ x
    P = F @ P @ F.T + Q
    return x, P
</code></pre>

  <h3>Update Step</h3>
    <pre><code>def update(x, P, z):
    y = z - (H @ x)  # Measurement residual
    S = H @ P @ H.T + R  # Residual covariance
    K = P @ H.T @ np.linalg.inv(S)  # Kalman gain
    x = x + K @ y  # Update state estimate
    P = (np.eye(len(P)) - K @ H) @ P  # Update covariance estimate
    return x, P
</code></pre>

  <h3>Visualization</h3>
    <pre><code>plt.plot(true_positions[:, 0], true_positions[:, 1], label="True trajectory", color="g")
plt.scatter(measurements[:, 0], measurements[:, 1], label="Noisy measurements", color="r", alpha=0.6)
plt.plot(estimated_positions[:, 0], estimated_positions[:, 1], label="Kalman estimate", color="b")
plt.legend()
plt.xlabel("X position")
plt.ylabel("Y position")
plt.title("Kalman Filter for 2D Object Tracking")
plt.show()
</code></pre>

  <h2>How to Run</h2>
    <ol>
        <li>Clone the repository to your local machine.</li>
        <li>Install the dependencies: <code>pip install numpy matplotlib</code></li>
        <li>Run the script: <code>python kalman_filter_2d.py</code></li>
    </ol>

  <h2>Output</h2>
    <p>The script generates a plot showing:</p>
    <ul>
        <li><strong>True trajectory</strong> (ideal positions).</li>
        <li><strong>Noisy measurements</strong> (simulated sensor data).</li>
        <li><strong>Kalman estimate</strong> (filtered trajectory).</li>
    </ul>

  <h2>About</h2>
    <p>
        Developed by <strong>Mohammed YOUSUF</strong>. For more information or questions, feel free to 
        <a href="mailto:yousufmohammed9148@gmail.com">contact me</a>.
    </p>
<h2>Acknowledgement</h2>
 <p>I would like to extend my deepest gratitude to Dr. Victor A.I, professor at Maharaja Institute of Technology Mysore,for his invaluable guidance throughout this project</p>
 
</body>
</html>
