# Two-Population Coupled Oscillators Simulation

This work simulates the dynamics of two populations of coupled oscillators based on a generalized Kuramoto model. The model includes oscillators that are coupled with each other, possibly with a phase lag, and the goal is to study how different parameters influence synchronization over time. The simulation computes the evolution of the oscillator phases and visualizes key quantities like the **order parameter** and **phase distribution**.

## Brief Description

- **Kuramoto Model**: A mathematical model for coupled oscillators where each oscillator evolves according to its own intrinsic frequency and is influenced by interactions with other oscillators.
  
- **Phase Lag** (\(\alpha\)): A phase offset between the oscillators when calculating their interactions. This phase lag can affect the synchronization dynamics of the system.

- **Order Parameter**: A measure of the degree of synchronization within each population of oscillators. It is calculated as the magnitude of the complex sum of oscillator phases, which quantifies how synchronized the oscillators are in each population.

&nbsp;![image](https://github.com/user-attachments/assets/89d4a016-013e-46b2-8898-72d82980be6b)


  A value close to 1 indicates high synchronization, while a value close to 0 indicates desynchronization.

- **Coupling Matrix**: A matrix that defines the coupling strength between oscillators in different populations. It includes both intra-population and inter-population coupling strengths.

## Dependencies

To run the code, the following Python libraries are required:

- `numpy`
- `matplotlib`
- `scipy`
- `numba`

You can install these libraries using `pip`:

```bash
pip install numpy matplotlib scipy numba
```


## Code

### 1. **Initialization of Parameters**

- **N**: Number of oscillators in each population (set to 128).
- **T**: Total time for the simulation (set to 500).
- **dt**: Time step for numerical integration (set to 0.1).
- **omega**: Intrinsic frequency of the oscillators (set to 1).
- **alpha**: Phase lag between oscillators, varied across a range (from 1.4 to 1.6).
- **K**: Coupling matrix, which defines the strength of interactions between the two populations, varied over a specified range.

The initial phases of the oscillators are randomly initialized from a normal distribution with a mean of 0 and standard deviation of 2.

### 2. **Core Functions**

- **`wrap_to_pi(theta)`**: Ensures that the phase values are constrained within the range \([-π, π]\). This function is essential for maintaining the periodic nature of phase differences in the system. It wraps the phase values to avoid overflow (i.e., ensuring they stay within one full circle of the unit circle in the complex plane).

- **`dtheta_dt_flat(theta_flat, t, omega, K, delta, N, alpha)`**: Computes the rate of change of the phases for all oscillators. This function defines the evolution of the system using a coupled set of differential equations, which account for both the intrinsic frequency of the oscillators and their interactions with other oscillators in both populations.

&nbsp;![image](https://github.com/user-attachments/assets/507eb934-1f9a-4414-8c50-5a2a66c052a7)


- **`integrate_and_wrap(theta_init_flat, t, omega, K, delta, N, alpha)`**: Solves the differential equations using `odeint` from the `scipy.integrate` module to numerically integrate the system. After the integration, the phase values are wrapped to the range \([-π, π]\) to ensure they remain consistent over time. The integration runs over the time array `t` and computes the evolution of all oscillator phases, taking into account the coupling and phase lag.

### 3. **Numerical Integration**

The system of coupled oscillators is solved using the `odeint` function, which numerically integrates the differential equations over the specified time range. The `odeint` function takes the following inputs:
- The differential equation function (`dtheta_dt_flat`).
- The initial phase values (`theta_init_flat`).
- The time array (`t`).
- The parameters for intrinsic frequency (`omega`), coupling matrix (`K`), phase lag (`alpha`), and the number of oscillators (`N`).

The output is the evolution of the phase values for each oscillator over time. After integration, the phase values are wrapped to the range \([-π, π]\) to ensure they remain within the periodic boundary conditions.

The integration captures how the system evolves over time, revealing synchronization or desynchronization dynamics between the two populations of oscillators.

## References

This work is based on the **Kuramoto model of coupled oscillators**, which is widely used in the study of synchronization phenomena in physics, biology, and network theory.

- Kuramoto, Y. (1975). Self-entrainment of a population of coupled non-linear oscillators. *International Journal of Engineering Science*, 16(11), 1187-1206.



