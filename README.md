# Theoretical MHD Modelling of the Polomac Concept

**Author:** Nicola Rupf  
**Supervisor:** Dr. Andreas Adelmann (PSI – Center for Scientific Computing, Theory and Data)  
**Institution:** ETH Zürich, Department of Physics  
**Date:** May 2026

---

## Overview

This repository accompanies the research project *Theoretical MHD Modelling of the Polomac Concept*, which develops a self-contained ideal MHD framework for the Polomac, a novel poloidal magnetic confinement geometry for nuclear fusion proposed by [Deutelio](https://www.deutelio.com) (described in [Elio et al. 2024](https://jtsp.eu/jtsp/article/view/32)).

The work proceeds from first principles: starting from the Boltzmann equation, it derives the ideal MHD equations, specialises them to the Polomac geometry, formulates the static MHD equilibrium, evaluates the relevant dimensionless parameters, compares the concept to tokamak and stellarator geometries, and lays out a concrete framework for a linearised FDTD solver.

No experimental plasma data from the Polomac exist as of this writing; the device is at the design stage.

---

## Contents

| Chapter | Topic |
|---------|-------|
| 2 | Derivation of the single-fluid ideal MHD equations from the Boltzmann equation |
| 3 | Polomac geometry and specialisation to poloidal configurations |
| 4 | Static equilibrium via a reduced Grad–Shafranov equation |
| 5 | Characteristic parameters: Alfvén velocity, Lundquist number, plasma β |
| 6 | Comparison with tokamak and stellarator geometries |
| 7 | Framework for a minimal FDTD solver for linearised ideal MHD |
| Appendices | Detailed derivations of species momentum equation, single-fluid momentum equation, and adiabatic equation of state |

---

## Key Results

- **Ideal MHD validity:** All six standard MHD assumptions (quasi-neutrality, negligible electron inertia, negligible displacement current, zero resistivity, small Larmor radius, adiabatic isotropic closure) are verified quantitatively for Polomac target parameters.
- **Reduced Grad–Shafranov equation:** The static equilibrium reduces to `Δ*ψ = −μ₀r² dP/dψ`, with boundary conditions of regularity at r = 0 and ψ = const on the conducting walls.
- **Characteristic parameters** (based on design values from Elio et al. 2024):
  - Alfvén velocity: v_A ≈ 5.5 × 10⁵ m/s
  - Lundquist number: S ∈ [2.8 × 10⁴, 2.1 × 10⁵] , ideal MHD limit well justified
  - Plasma β ∈ [0.04, 1.01] , high-β operation potentially achievable (derived by simply using extremizing values in Elio et al. 2024)
- **FDTD framework:** The linearised system is proven to be first-order hyperbolic. A staggered Yee-type grid discretisation is derived, separating the shear-Alfvén branch (V_φ, B_φ) from the compressional/magnetosonic branch. CFL bound: Δt ≤ Δx / (√2 · v_f), where v_f = √(v_A² + c_s²).

---

## Context: Poloidal Confinement

The Polomac belongs to a class of poloidal confinement devices, most notably pioneered by the [Levitating Dipole Experiment (LDX)](https://en.wikipedia.org/wiki/Levitated_Dipole_Experiment) at MIT, which demonstrated compressibility-driven stabilisation of interchange modes in a superconducting dipole geometry before concluding in 2011, and also being explored by the Japanese [RT-1 experiment](https://www.nature.com/articles/s41467-024-44977-x?utm_source=researchgate.net&utm_medium=article). The concept is also being revisited by the [OpenStar](https://www.openstar.tech/) project, which is developing a levitated-dipole reactor in a closely related regime (see also [Simpson et al. 2026](https://arxiv.org/abs/2602.20564)).

---

## Key References

- **Freidberg, J. P.** (2014). *Ideal MHD*. Cambridge University Press.  - Primary reference for MHD theory, equilibrium, and stability.
- **Chen, F. F.** (2016). *Introduction to Plasma Physics and Controlled Fusion*, 3rd ed. Springer. DOI: [10.1007/978-3-319-22309-4](https://doi.org/10.1007/978-3-319-22309-4)
- **Elio, F. et al.** (2024). Technical Report: The Polomac approach to fusion energy. *Journal of Technological and Space Plasmas* 5.1, pp. 172–180. DOI: [10.31281/med9bh43](https://doi.org/10.31281/med9bh43)  - Device description and target parameters.
- **Garnier, D. T., Kesner, J., and Mauel, M. E.** (1999). Magnetohydrodynamic stability in a levitated dipole. *Physics of Plasmas* 6.9. DOI: [10.1063/1.873601](https://doi.org/10.1063/1.873601)
- **Garnier, D. T., Hansen, A., et al.** (2006). Production and study of high-beta plasma confined by a superconducting dipole magnet. *Physics of Plasmas* 13.5. DOI: [10.1063/1.2186616](https://doi.org/10.1063/1.2186616)
- **Rosenbluth, M. N. and Longmire, C. L.** (1957). Stability of plasmas confined by magnetic fields. *Annals of Physics* 1.2. DOI: [10.1016/0003-4916(57)90055-6](https://doi.org/10.1016/0003-4916(57)90055-6)  - Original interchange instability criterion.
- **Nishiura, M. et al.** (2015). Smproved beta (local beta > 1) and density in electron
cyclotron resonance heating on the RT-1 magnetosphere plasma. *Nuclear Fusion* 55.5. DOI: [10.1088/0029-5515/55/5/053019](https://doi.org/10.1088/0029-5515/55/5/053019)  - Local beta in magnetic dipole above 1.
- **Yee, K.** (1966). Numerical solution of initial boundary value problems involving Maxwell's equations in isotropic media. *IEEE Transactions on Antennas and Propagation* 14.3. DOI: [10.1109/TAP.1966.1138693](https://doi.org/10.1109/TAP.1966.1138693)
- **Godlewski, E. and Raviart, P.-A.** (2021). *Numerical Approximation of Hyperbolic Systems of Conservation Laws*, 2nd ed. Springer. DOI: [10.1007/978-1-0716-1344-3](https://doi.org/10.1007/978-1-0716-1344-3)

---

## Acknowledgements

I would like to thank **Dr. Andreas Adelmann** for the opportunity to work at the intersection of plasma and computational theory, and for his guidance throughout this project. I would also like to thank **Filippo Elio** for the collaboration and valuable insights into the Polomac concept.

---

## Feedback

I am happy to receive feedback, questions, or suggestions at **nicola.rupf@gmail.com**.
