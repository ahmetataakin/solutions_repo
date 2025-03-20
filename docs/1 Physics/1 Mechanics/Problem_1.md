# Problem 1
# Problem 1
# Investigating the Range as a Function of the Angle of Projection

## 1. Theoretical Foundation

### Introduction
Projectile motion is one of the fundamental topics in classical mechanics, describing the motion of an object launched into the air under the influence of gravity. The path followed by such an object is called a parabola, assuming there is no air resistance. The horizontal range of a projectile depends on various factors, including the initial velocity, launch angle, and gravitational acceleration.

Understanding projectile motion has practical applications in sports, engineering, and space exploration. This document aims to derive the governing equations, analyze the dependence of range on launch angle, and implement a Python simulation to visualize the results.

### Governing Equations of Motion
The motion of a projectile can be described using the equations of motion in two dimensions:

- **Horizontal motion** (constant velocity, no acceleration apart from initial push):
  
  $$ x(t) = v_0 \cos(\theta) t  $$   
- **Vertical motion** (accelerated motion due to gravity):
  
 $$ y(t) = v_0 \sin(\theta) t - \frac{1}{2} g t^2 $$
  
where:
   ($\v_0\$) is the initial velocity ,
   ($\theta \$)  is the launch angle,
   \$( g \$)\$  is the acceleration due to gravity (9.81 m/s² on Earth),
   \$( x(t) \$)  and  \$( y(t) \$) represent the projectile's position at time \( t \).

### Time of Flight
To determine how long the projectile stays in the air, we set the vertical position to zero (assuming it starts and ends at the same height):
  
  $$ v y(T) = 0 = v_0 \sin(\theta) T - \frac{1}{2} g T^2 $$
  
Factoring out \( T \), we solve for total flight time:
  
  $$ T = \frac{2 v_0 \sin(\theta)}{g} $$
  
This formula shows that the time in the air depends on the initial velocity and the launch angle.

### Horizontal Range
Using the time of flight equation, we compute the range \( R \) as follows:
  
  $$ R = v_0 \cos(\theta) T = \frac{v_0^2 \sin(2\theta)}{g} $$
  
From this equation, we can observe that:
  - The range depends on ($\v_0^2\$)  meaning an increase in initial velocity significantly increases the range.
  - The term  \$sin(2\theta$) determines how the launch angle affects the range. The range is maximum when \$$( \theta = 45^\circ \$$).

## 2. Analysis of the Range

- **Effect of Angle:** The range is symmetric about 45°. That means for two angles \$$( \theta \$$) and \$$( 90^\circ - \theta \$$), the range will be the same.
- **Effect of Initial Velocity:** Since \$$( R \propto v_0^2 \$$), doubling the initial velocity results in a fourfold increase in range.
- **Effect of Gravity:** A larger \$$( g \$$) reduces the range, which is why projectiles travel farther on the Moon (where \$$( g \$$) is smaller).
- **Maximum Range Derivation:** The derivative of \( R \) with respect to \( \theta \) shows that the maximum range occurs at \$$( 45^\circ \$$).

## 3. Practical Applications

Projectile motion is widely used in:
- **Sports:** In games like soccer, basketball, and golf, understanding projectile motion helps optimize shots.
- **Military and Engineering:** In ballistics, projectile trajectories are carefully calculated for accuracy.
- **Space Exploration:** Calculations for planetary landings and spacecraft motion involve projectile motion principles.

## 4. Implementation (Python Simulation)

The following Python script simulates projectile motion and plots the range as a function of the launch angle:

```python
import numpy as np
import matplotlib.pyplot as plt
![alt text](download.png)
def projectile_range(v0, g=9.81):
    """
    This function computes and plots the projectile range as a function of launch angle.
    
    Parameters:
    v0: float - Initial velocity in m/s
    g: float - Acceleration due to gravity (default is 9.81 m/s²)
    """
    angles = np.linspace(0, 90, num=100)  # Generate angles from 0° to 90°
    angles_rad = np.radians(angles)  # Convert angles to radians
    
    # Compute range using the derived equation R = (v0^2 * sin(2θ)) / g
    ranges = (v0**2 * np.sin(2 * angles_rad)) / g
    
    # Plot results
    plt.figure(figsize=(10,6))
    plt.plot(angles, ranges, label=f'Initial Velocity: {v0} m/s', color='b')
    plt.axvline(x=45, color='r', linestyle='--', label='Maximum Range at 45°')
    plt.xlabel('Angle (degrees)')
    plt.ylabel('Range (m)')
    plt.title('Projectile Range vs. Angle')
    plt.legend()
    plt.grid()
  
    # Save the plot as a PNG image
    plt.savefig('download.png', dpi=300)  # Saves the plot as PNG with 300 dpi
    plt.show()

# Example: v0 = 20 m/s
projectile_range(20)
```

1. ***Define `projectile_range` Function**
   - Generates a set of angles from 0° to 90°.
   - Converts angles to radians since trigonometric functions in Python use radians.
   - Computes the projectile range for each angle using the derived equation.
   - Plots the range as a function of launch angle.

2. **Plotting the Results**
   - A blue curve represents the range for different angles.
   - A dashed red line marks the angle at which the maximum range occurs (45°).
   - Labels and grid are added for better readability.

## 5. Limitations and Further Considerations

- **No Air Resistance:** The model assumes no drag forces, which can significantly affect real-world projectile motion.
- **Flat Terrain:** The calculations assume a flat surface, but in reality, terrains are uneven.
- **Wind Effects:** The influence of wind is ignored, though it can greatly impact the trajectory.
- **Launch Height:** The current derivation assumes the projectile is launched from and lands at the same height. If the launch height differs, the equations become more complex.

### Future Improvements:
- Incorporating air resistance using numerical methods.
- Simulating projectiles with variable gravitational fields.
- Exploring multi-stage projectile motion (e.g., rocket launches).
- Considering spin and Magnus effect for applications in sports and aerodynamics.
