### Particle Physics Engine Coding Assignment in Rust

#### Goal of the Project
The objective of this assignment is to develop a basic particle physics engine using Rust, focusing on simulating gravitational interactions between particles. The engine will model the behavior of particles influenced by gravity, providing hands-on experience with Rust's core features such as memory safety, concurrency, and its powerful type system.

#### Project Requirements

##### 1. Particle Representation
- **Attributes**: Each particle should have attributes such as position, velocity, acceleration, and mass.
- **Initialization**: Implement a method to initialize particles with random or user-defined attributes.
- **Unique Identifiers**: Assign unique identifiers to each particle for tracking and debugging purposes.

##### 2. Physics Simulation
- **Newton’s Laws**: Apply Newton’s laws of motion to update the particles' positions and velocities over time.
- **Force Accumulation**: Implement a mechanism to accumulate gravitational forces acting on each particle.
- **Integration Methods**: Choose and implement a numerical integration method (e.g., Euler, Verlet) to update particle states over discrete time steps.

##### 3. Gravity Calculation
- **Gravitational Force**: Simulate gravitational attraction between particles based on Newton’s law of universal gravitation. This involves calculating the force as \( F = G \frac{m_1 m_2}{r^2} \), where \( G \) is the gravitational constant, \( m_1 \) and \( m_2 \) are the masses of the particles, and \( r \) is the distance between them.
- **Tunable Gravity**: Allow the gravitational constant \( G \) to be adjustable by the user, either through a configuration file or command-line arguments.

##### 4. Collision Detection and Response
- **Collision Detection**: Implement an efficient algorithm for detecting collisions between particles.
- **Collision Response**: Define how particles respond to collisions, ensuring the conservation of momentum and energy where appropriate.

##### 5. Data Structures
- **Spatial Partitioning**: Use appropriate data structures to manage and query particle positions efficiently (e.g., quad-trees, octrees, spatial grids).
- **Storage Optimization**: Ensure that the data structures and algorithms are optimized for performance and memory usage.

##### 6. Concurrency
- **Parallel Processing**: Utilize Rust’s concurrency features to parallelize computations where possible, such as updating particle states or force calculations.
- **Safety Considerations**: Ensure that all concurrent operations are safe and free of race conditions, leveraging Rust’s ownership system and concurrency primitives.

##### 7. User Interface
- **Input Handling**: Design a basic input system to allow users to interact with the simulation, such as adding, removing, or modifying particles.
- **Visualization**: Provide a simple visualization of the particle system, using text-based output or integrating with a graphics library for real-time rendering.
- **Configuration**: Allow users to configure simulation parameters, including the gravitational constant \( G \), through a configuration file or command-line arguments.

##### 8. Testing and Validation
- **Unit Tests**: Write unit tests for key components of the engine to ensure correctness.
- **Performance Testing**: Measure and optimize the performance of the engine, especially for large numbers of particles.
- **Validation**: Compare the simulation results with analytical solutions or known physical behaviors to validate the accuracy of the engine.

##### 9. Documentation
- **Code Documentation**: Document the codebase thoroughly, explaining the purpose and functionality of each module, class, and function.
- **User Guide**: Provide a user guide that explains how to set up, run, and interact with the simulation, including examples and troubleshooting tips.
- **Developer Guide**: Offer insights for future developers on how to extend or modify the engine, highlighting the design decisions and architectural patterns used.

#### Submission Requirements
- **Code Repository**: Submit the project via a public code repository (e.g., GitHub, GitLab), including all source code, tests, and documentation.
- **README**: Ensure the repository contains a README file with an overview of the project, instructions for building and running the simulation, and any other pertinent information.
- **Demo**: Optionally, provide a short demo video or animated GIF showcasing the simulation in action.

This assignment focuses on implementing gravity in a particle physics engine, encouraging the application of both theoretical knowledge and practical programming skills. Good luck, and enjoy the journey into Rust and physics simulation!