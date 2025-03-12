# Problem 1
# Projectile motion analysis: Range as a function of the angle of projection

import numpy as np
import matplotlib.pyplot as plt

# Constants
g = 9.81  # Acceleration due to gravity in m/s^2

# Function to calculate the horizontal range (R) for given initial velocity and launch angle
def calculate_range(v0, angle_deg):
    """
    Calculates the range of a projectile given the initial velocity and launch angle.
    
    Parameters:
        v0 (float): Initial velocity in meters per second.
        angle_deg (float): Launch angle in degrees.
    
    Returns:
        float: The horizontal range of the projectile.
    """
    # Convert angle to radians
    angle_rad = np.radians(angle_deg)
    
    # Calculate time of flight (total time before hitting the ground)
    time_of_flight = (2 * v0 * np.sin(angle_rad)) / g
    
    # Calculate the horizontal range
    range_of_projectile = v0 * np.cos(angle_rad) * time_of_flight
    
    return range_of_projectile

# Function to plot the range as a function of the launch angle
def plot_range_vs_angle(v0, angle_range=(0, 90), num_points=100):
    """
    Plots the range of the projectile as a function of the launch angle.
    
    Parameters:
        v0 (float): Initial velocity in meters per second.
        angle_range (tuple): A tuple defining the range of angles (min_angle, max_angle).
        num_points (int): Number of points to plot between the min and max angles.
    """
    # Generate a list of angles from min_angle to max_angle
    angles = np.linspace(angle_range[0], angle_range[1], num_points)
    
    # Calculate the corresponding ranges
    ranges = [calculate_range(v0, angle) for angle in angles]
    
    # Plot the graph
    plt.figure(figsize=(8, 6))
    plt.plot(angles, ranges, label=f'Initial velocity = {v0} m/s', color='b')
    plt.xlabel('Launch Angle (degrees)')
    plt.ylabel('Range (meters)')
    plt.title(f'Projectile Range vs Launch Angle for v0 = {v0} m/s')
    plt.legend()
    plt.grid(True)
    plt.show()

# Theoretical Foundation:
 We will now explain how we derived the equations used in this simulation.

 The horizontal and vertical motions are governed by the following kinematic equations:
 Horizontal displacement: x(t) = v0 * cos(theta) * t
 Vertical displacement: y(t) = v0 * sin(theta) * t - (1/2) * g * t^2

 The range R is the horizontal distance covered by the projectile when it returns to the ground.
 The time of flight T is the total time the projectile is in the air:
 T = (2 * v0 * sin(theta)) / g

 The range is then: R = v0 * cos(theta) * T
 Hence, the range is: R = (v0^2 * sin(2 * theta)) / g
 This equation gives the horizontal distance or range as a function of launch angle.

# Analysis of the Range:
 The range as a function of angle is parabolic. The maximum range occurs at an angle of 45 degrees.

# Practical Applications:
 This model is idealized and assumes no air resistance. In real life, air resistance and other factors
 such as wind, spin, and altitude can significantly affect the trajectory.

# Implementation:
 Now, we implement the computation and visualization of the projectile range for different angles.
 Let's create some simulations.

# Test 1: Plotting the range for an initial velocity of 20 m/s
v0_test = 20  # Initial velocity in m/s
plot_range_vs_angle(v0_test)

# Test 2: Plotting the range for an initial velocity of 30 m/s
v0_test = 30  # Initial velocity in m/s
plot_range_vs_angle(v0_test)

# Test 3: Plotting the range for an initial velocity of 40 m/s
v0_test = 40  # Initial velocity in m/s
plot_range_vs_angle(v0_test)

# Conclusion and Limitations:
 In this simulation, we used the ideal equations of projectile motion without considering air resistance or other real-world factors.
 To make this model more realistic, factors such as drag, wind speed, and launch height should be incorporated.
 These effects would require more complex differential equations or numerical methods such as solving the equations of motion using a Runge-Kutta method.

 A more realistic model would also take into account uneven terrain, wind velocity, and spin, all of which alter the trajectory.

