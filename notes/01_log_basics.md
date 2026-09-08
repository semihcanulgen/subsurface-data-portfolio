# Wireline log fundamentals

Short technical notes on the core wireline logs used for lithology
discrimination, written while refreshing petrophysics fundamentals.

## The four core logs

- **GR (Gamma Ray)** — measures natural radioactivity. Clay minerals
  (illite, kaolinite, smectite) host radioactive elements (K, Th, U),
  so GR is the primary tool for distinguishing shale from clean
  reservoir rock (sandstone, limestone, dolomite).
- **RHOB (Bulk Density)** — measures the rock's total density
  (matrix + fluid-filled pore space combined). Used, alongside a known
  matrix density, to derive porosity.
- **NPHI (Neutron Porosity)** — measures hydrogen atom concentration,
  which is dominated by fluid in the pore space. It cannot distinguish
  water from oil (both have similar hydrogen index), but it responds
  strongly to gas.
- **DTC (Sonic / Delta-T Compressional)** — measures the travel time of
  a compressional wave through the rock. Reflects mechanical
  stiffness: fast travel (low DTC) = stiff/tight rock, slow travel
  (high DTC) = softer/more porous rock. Sonic is largely blind to
  secondary (vuggy/fracture) porosity, since the wave can bridge
  around isolated voids through the matrix — this makes sonic-density
  porosity divergence a classic secondary-porosity indicator in
  carbonates.

## Crossplots and the gas effect

RHOB and NPHI respond in *opposite* directions to gas:
- Gas has very low hydrogen density → NPHI reads porosity too **low**.
- Gas is far less dense than water → RHOB reads porosity too **high**.

Plotted together, a water-filled zone shows RHOB- and NPHI-derived
porosity close together. A gas-filled zone shows the two values pull
apart — this divergence is the classic "crossover" signature used to
flag gas-bearing intervals.

## M-N plot

A derived crossplot (using RHOB, NPHI, and DTC) designed to isolate
matrix mineralogy (quartz, calcite, dolomite) largely independent of
porosity — useful when the goal is lithology identification rather
than pure porosity estimation.

## Relevance to the FORCE 2020 lithology project

These same principles underpin the feature engineering used in the
FORCE 2020 wireline log lithology prediction project:
- VSH derived from GR (shale volume).
- Acoustic impedance derived from RHOB × sonic velocity (1/DTC).
- M-N-style matrix mineralogy targeting.
- Coal_Flag: a rule-based feature exploiting coal's distinctive low
  RHOB / high DTC signature, added because coal was a rare class that
  a purely data-driven model tended to under-detect.