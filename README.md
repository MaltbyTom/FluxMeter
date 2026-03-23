# Flux Meter

## Mathematical Notes

The visualization renders hypotrochoids: curves traced by a point on a wheel of radius r rolling inside a fixed circle of radius R, with the drawing point at distance d from the wheel's center.
x(t) = (R−r)·cos(t) + d·cos((R−r)/r · t)
y(t) = (R−r)·sin(t) − d·sin((R−r)/r · t)

Three parameters (R, r, d) are seeded uniquely per trace from a deterministic pseudorandom number generator (mulberry32), producing varied but reproducible geometries. A second noise layer applies per-step random deviation to each plotted point, scaled by the Deviation control — pulling the trace off its deterministic path by an amount proportional to the flux signal.

Multiple traces share rotational symmetry around the canvas center, each offset by 2π/n radians.

Persistence renders as temporal smear: the canvas fades incrementally rather than clearing, preserving recent path history. Combined with visual neural lag, this produces implicit multi-scale temporal derivatives — momentary, intermediate, and short-term flux — without explicit calculation. The eye integrates them.

Seed modes determine the RNG input: timestamp jitter (sampling system clock entropy), phrase hash (deterministic from text input — which has potential cryptographic implications), mouse movement entropy, microphone amplitude, or external quantum randomness (random.org). Each produces a distinct but mathematically equivalent perturbation character.

When R/r is rational, traces close into finite flowers. When irrational, they search without resolution. The noise ensures both feel alive.

Live metrics — click any metric to toggle it on the sparkline. Heat peak tracks convergence attractors via dynamic normalization against session maximum. Cold void measures negative space — regions the geometry actively avoids within the drawing radius. Coherence scores harmonic relationships between R/r ratios across traces. Phase sync measures how closely trace cycle positions align. Settings changes and events are logged with full parameter state. DUMP LOG exports timestamped CSV.

---

Lineage: clock-jitter environmental flux meter (T. Maltby, 1991) → CREATE Framework (2025) → Flux Meter (2026).
© T. Maltby & Claude, 2026. CC BY-SA 4.0. Recursive attribution required. 
