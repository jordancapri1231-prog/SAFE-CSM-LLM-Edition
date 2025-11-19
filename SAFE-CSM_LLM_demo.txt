import numpy as np
import matplotlib.pyplot as plt

# =====================================
# SAFE-CSM Minimal Model (LLM Edition)
# =====================================

# θ is interpreted as a one-dimensional output-direction scalar ∈ [0, 1]
# θ → 0 : excessive fixation / collapse-like behavior
# θ → 1 : drift / runaway tendency
# CSM acts as a small “pressure-release valve” to keep θ within a moderate band

# Parameters
STEPS = 200          # Number of simulation steps
LOW  = 0.2           # Lower stability boundary (below this, slightly tilt upward)
HIGH = 0.8           # Upper stability boundary (above this, slightly tilt downward)
EPS  = 0.02          # Small corrective adjustment applied by the CSM
NOISE_STD = 0.05     # Noise added to the LLM’s movement (external fluctuation)

np.random.seed(0)    # For reproducibility (optional)


def llm_step(theta):
    """
    One update step of the LLM-only toy model.
    - Adds small noise
    - Introduces a slight bias toward extremes (0 or 1)
      to mimic fixation/drift tendencies
    """
    noise = np.random.normal(0, NOISE_STD)

    # Light pull toward extremes (source of fixation-like behavior)
    pull_to_extreme = 0.03 * (1 if theta > 0.5 else -1)

    new_theta = theta + noise + pull_to_extreme

    # Clip within [0, 1]
    return float(np.clip(new_theta, 0.0, 1.0))


def csm_step(theta):
    """
    SAFE-CSM minimal stabilization logic:
    - If θ < LOW, nudge it upward by EPS
    - If θ > HIGH, nudge it downward by EPS
    - Otherwise, do nothing (within stability band)
    """
    if theta < LOW:
        theta += EPS
    elif theta > HIGH:
        theta -= EPS

    return float(np.clip(theta, 0.0, 1.0))


def simulate(with_csm: bool):
    """
    Run the simulation.
    - with_csm=True : LLM + SAFE-CSM stabilization
    - with_csm=False: LLM-only behavior
    """
    thetas = []
    theta = 0.5  # Start near the middle

    for _ in range(STEPS):
        # LLM update
        theta = llm_step(theta)

        # Apply CSM if enabled
        if with_csm:
            theta = csm_step(theta)

        thetas.append(theta)

    return np.array(thetas)


# ===============================
# Run simulation
# ===============================
thetas_no_csm  = simulate(with_csm=False)
thetas_with_csm = simulate(with_csm=True)

# Plot results
plt.figure(figsize=(10, 4))
plt.plot(thetas_no_csm,  label="LLM only (no CSM)", linestyle="--")
plt.plot(thetas_with_csm, label="LLM + SAFE CSM", alpha=0.8)
plt.axhline(LOW,  color="gray", linestyle=":", label="LOW/HIGH band")
plt.axhline(HIGH, color="gray", linestyle=":")
plt.ylim(-0.1, 1.1)
plt.xlabel("step")
plt.ylabel("theta (0–1 output-direction scalar)")
plt.legend()
plt.title("SAFE CSM: Small Stabilizing Bias Against Fixation and Drift")
plt.show()

# Print final states
print(f"Final theta (no CSM): {thetas_no_csm[-1]:.3f}")
print(f"Final theta (with CSM): {thetas_with_csm[-1]:.3f}")

