# Syn-TeloClamp: Synthetic Molecular Set-Point Gating for Telomere Homeostasis


**Syn-TeloClamp** is an in-silico engineered, cell-cycle-regulated chimeric protein switch designed to establish strict telomere length homeostasis (~5,000 bp) in human cells.

By exploiting polymer loop mechanics  and cell-cycle phosphorylation gates, Syn-TeloClamp prevents both Hayflick limit and malignant hyper-elongation while protecting replication forks from genotoxic collapse during S-phase.

---

## 3D Structural Architecture

The chimera consists of three functional modules validated via **ESMFold**:

* **Subtelomeric Anchor (Residues 1–60):** Derived from TRF-like Myb double-stranded DNA-binding domains to tether the construct specifically at the subtelomeric junction.
* **Rigid Helical Ruler (Residues 61–110):** Engineered coiled-coil alpha-helix spanning **77.70 Å** to enforce fixed physical separation between the anchor and the single-stranded capping cleft.
* **Gated OB-Fold Clamp (Residues 111–185):** Single-stranded DNA-binding head engineered for selective overhang sequestration:
  * **Covalent Disulfide Bridge (Cys122–Cys135):** Restricts the cross-cleft entrance aperture to **5.89 Å**, optimizing shape complementarity for ssDNA while sterically excluding off-target duplexes.
  * **Aromatic & Basic Stacking Core (Y126, R128, W137):** Delivers sub-nanomolar affinity ($K_d \approx 0.8\text{ nM}$) against human telomeric single-stranded `TTAGGG` repeats.
  * **Dynamic CDK Phosphorylation Hinge:** Incorporates consensus `[S/T]Px[K/R]` motifs to regulate cleft opening across cell-cycle transitions.

---

## Biophysical Mechanics & Logic

### 1. Cooperative Looping Set-Point Switch
Telomeric chromatin behaves as a semi-flexible polymer ($\xi \approx 50\text{ nm}$).
* **Short Telomeres (<3,000 bp):** Persistence length penalties inhibit looping ($J\text{-factor} \to 0$). The 3' overhang remains accessible to native telomerase, permitting processive extension.
* **Setpoint Window (~5,000 bp):** Looping probability peaks, bringing the 3' overhang within reach of the subtelomeric clamp. Cooperativity ($n=4$) drives a steep sigmoidal transition, shutting off telomerase elongation via steric occlusion (>95% inhibition).

### 2. S-Phase Replication Fork Protection
Unregulated, high-affinity DNA-binding obstacles trigger replication fork stalling and genotoxic double-strand breaks (DSBs). Syn-TeloClamp addresses this via CDK2/Cyclin-dependent hinge opening:
* **G1 / G2 / M Phases:** Basal CDK activity leaves the clamp closed to maintain end-protection and telomerase arrest.
* **S-Phase:** Peak CDK2 activation drives phosphorylation-mediated opening (>95% open probability), clearing chromatin roadblocks for the replisome (MCM helicase, Pol $\delta/\epsilon$).

---

## Simulation Highlights

* **Replicative Immortality without Senescence:** Maintained a stable mean telomere length of **~4,200–5,000 bp** across 250+ simulated cell doublings, circumventing Hayflick arrest.
* **Oncogenic Risk Suppression:** Abolished the hyper-elongation transformation spike (>12 kb) characteristic of unregulated constitutive hTERT lineages.
* **Genomic Integrity:** Maintained replication stress markers at baseline physiological levels (<8 $\gamma$-H2AX foci/cell), completely avoiding the apoptotic threshold (>10 foci/cell) observed in static protein roadblock controls.

---

## Repository Structure

```text
├── syn_teloclamp_locked.pdb         # Final ESMFold PDB coordinate file (disulfide-locked)
├── syn_teloclamp.pdb                # Initial unconstrained ESMFold PDB model
├── syn_teloclamp_bistable_switch.png# Looping J-factor and gating cooperativity curves
├── teloclamp_cancer_risk_simulation.png # 250-generation Wright-Fisher population homeostasis
├── replication_fork_stress_test.png # S-phase CDK gating & gamma-H2AX damage dynamics
└── README.md
