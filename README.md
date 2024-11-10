# Two-Population Coupled Oscillators Simulation

This project simulates the dynamics of two populations of coupled oscillators based on a generalized Kuramoto model. The model includes oscillators that are coupled with each other, possibly with a phase lag, and the goal is to study how different parameters influence synchronization over time. The simulation computes the evolution of the oscillator phases and visualizes key quantities like the **order parameter** and **phase distribution**.

## Key Concepts

- **Kuramoto Model**: A mathematical model for coupled oscillators where each oscillator evolves according to its own intrinsic frequency and is influenced by interactions with other oscillators.
  
- **Phase Lag** (\(\alpha\)): A phase offset between the oscillators when calculating their interactions. This phase lag can affect the synchronization dynamics of the system.

- **Order Parameter**: A measure of the degree of synchronization within each population of oscillators. It is calculated as the magnitude of the complex sum of oscillator phases, which quantifies how synchronized the oscillators are in each population.

  The **order parameter** \( r_k(t) \) for population \( k \) is computed as:

  \[
  r_k(t) = \left| \frac{1}{N} \sum_{i=1}^N e^{i \theta_{k,i}(t)} \right|
  \]

  where:
  - \( r_k(t) \) is the order parameter for population \( k \) at time \( t \),
  - \( N \) is the number of oscillators in the population,
  - \( \theta_{k,i}(t) \) is the phase of the \( i \)-th oscillator in population \( k \) at time \( t \),
  - The complex exponential \( e^{i \theta_{k,i}(t)} \) represents the phase of the oscillator in the complex plane.

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
