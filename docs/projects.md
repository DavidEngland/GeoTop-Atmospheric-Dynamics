Here is a set of four rigorous, multi-disciplinary class projects tailored for a mixed cohort of atmospheric scientists, physicists, and CFD engineers at UAH. Each project requires real-world (or high-fidelity simulated) data, a deep dive into the geometric/topological theory, custom code implementation, and high-impact visual rendering.

Given the complexity, these are scoped perfectly for **groups of 3 to 4 students**, allowing a natural division of labor (e.g., Data Wrangler/Meteorologist, Theoretical/Math Lead, CFD/Numerical Lead).

---

### Project 1: Mapping the "Invisible Walls" of the Polar Vortex

* **Real-World Problem:** Traditional methods of defining the polar vortex boundary rely on arbitrary thresholds (e.g., the 200-hPa geopotential height contour). This fails during structural split or displacement events (sudden stratospheric warmings), leading to poor mid-latitude winter weather predictability.
* **The Mission:** Use frame-independent Lagrangian topology to find the true, objective transport barrier of a polar vortex collapse event.
* **Data Source:** Open-access ERA5 hourly atmospheric reanalysis data (U and V wind components on pressure levels) available via Copernicus Climate Data Store.
* **Theory to Apply:** Cauchy-Green Deformation Tensor, Finite-Time Lyapunov Exponents (FTLE), and hyperbolic Lagrangian Coherent Structures (LCS).
* **Code Deliverables:** A Python script (utilizing `xarray` and `numpy` or `PyLCS`) to ingest wind fields, integrate fluid parcel trajectories forward/backward in time, and compute the maximum eigenvalue fields.
* **Visuals & Presentation:** High-resolution animations overlaying the FTLE "ridges" onto potential vorticity maps, clearly showing where air is trapped inside the vortex core versus where it is shredding off into mid-latitudes.

---

### Project 2: Topological Fingering of Severe Convective Storms

* **Real-World Problem:** Numerical weather prediction (NWP) models struggle to predict the exact morphology and organizing state of severe convective systems (e.g., supercells vs. squall lines) from raw radar data.
* **The Mission:** Apply Topological Data Analysis (TDA) to tracking radar reflectivity and updraft helicity to quantify convective organization over time.
* **Data Source:** Real-time or archived NEXRAD Level-II radar reflectivity data from a major Alabama tornado outbreak (available via NOAA NCEI AWS buckets).
* **Theory to Apply:** Persistent Homology, filtration of sub-level sets, Betti numbers ($\beta_0$ for counting isolated convective cells, $\beta_1$ for tracking structural loops/vortex holes), and Persistence Diagrams.
* **Code Deliverables:** A Jupyter Notebook leveraging the `GUDHI` or `Giotto-tda` Python libraries to convert spatial radar grids into point clouds, generate Vietoris-Rips filtrations, and output birth-death persistence metrics.
* **Visuals & Presentation:** Side-by-side plots of the changing radar storm structure next to its corresponding dynamic Persistence Diagram (or barcode plot). The presentation must prove whether a spike in $\beta_1$ lifetime acts as a precursor to tornadogenesis.

---

### Project 3: Modeling Nocturnal Boundary Layer Collapse as a Cusp Catastrophe

* **Real-World Problem:** Air quality and boundary layer models (like WRF-CMAQ) frequently miscalculate the evening transition, either killing off turbulence too quickly or failing to trap pollutants near the surface.
* **The Mission:** Build a simplified fast-slow low-order dynamical system that treats the Stable Boundary Layer (SBL) as a geometric manifold exhibiting a cusp bifurcation.
* **Data Source:** High-frequency tower observation data (e.g., from the legacy CASES-99 experiment or local UAH boundary layer profiling instruments measuring temperature and wind speed variance at multiple heights).
* **Theory to Apply:** Catastrophe Theory (Thom's Cusp Normal Form), Fast-Slow Dynamics, and Fenichel's slow manifold stability boundaries.
* **Code Deliverables:** A MATLAB or Python ODE solver initializing a low-order boundary layer model. The code must numerically sweep the parameter space of Geostrophic Wind ($U_g$) and Net Radiation ($R_n$) to find the state manifold boundaries.
* **Visuals & Presentation:** A beautifully rendered 3D state-space manifold surface. The group must project the actual observed real-world time-series trajectories of an evening boundary layer collapse onto the folded cusp surface, highlighting the hysteresis loop.

---

### Project 4: Energy-Preserving Discrete Exterior Calculus (DEC) Fluid Solver

* **Real-World Problem:** Traditional finite-difference and finite-volume CFD models suffer from artificial numerical dissipation—they slowly "drain" vorticity and energy over time due to grid interpolation errors, ruining long-term climate simulations.
* **The Mission:** Program a mimetic, structure-preserving 2D incompressible Euler/Navier-Stokes solver that guarantees conservation of energy and circulation on an irregular mesh.
* **Data Source:** Purely computational. Initialized with a standard challenging fluid benchmark, such as a localized Taylor-Green vortex or a shear layer roll-up (Kelvin-Helmholtz instability).
* **Theory to Apply:** Discrete Exterior Calculus (DEC), simplicial complexes (primal Delaunay triangles and dual Voronoi cells), discrete coboundary operators ($D$), and the discrete Hodge Star mass matrix.
* **Code Deliverables:** A custom fluid solver written in Python, Julia, or C++ that computes flow fields using discrete differential forms (cochains) rather than vector fields.
* **Visuals & Presentation:** A time-series plot comparing the total kinetic energy conservation of the DEC solver versus a standard upwind finite-difference scheme. Presentation must include animations of vorticity preservation over an extended timeline, proving that the DEC model does not lose its structural physics even on a coarse mesh.

---

### 🎓 Suggested Group Composition Strategy

For a successful presentation day, suggest that students organize their groups to feature:

1. **The Domain Expert:** (Atmospheric/Physics student) Responsible for ensuring the physical data interpretation makes physical sense.
2. **The Applied Math Lead:** Responsible for mapping the differential geometry/topology formulas to the project framework.
3. **The Software Architect:** (CFD/Engineering student) Highly capable of translating tensors and matrix operations into high-performance array operations (NumPy, PyTorch, or Julia).