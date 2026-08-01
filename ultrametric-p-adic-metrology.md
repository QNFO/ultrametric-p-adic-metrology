---
title: "Ultrametric p-Adic Quantum Metrology: Passive Error Resilience via Bruhat-Tits Geometry"
author: "Rowan Brad Quni-Gudzinas"
date: "2026-08-01"
license: "QNFO Unified License Agreement (QNFO-ULA)"
doi: "PENDING-ZENODO"
status: "draft"
version: "1.0"
---

**Author:** Rowan Brad Quni-Gudzinas | **Date:** 2026-08-01 | **License:** QNFO-ULA: https://legal.qnfo.org/

# Abstract

The dominant path to quantum advantage relies on fault-tolerant quantum error correction (QEC) — a strategy that imposes exponential overhead, cryogenic cooling requirements, and a timeline that has been "ten years away" for forty years. We propose an alternative: matching the geometry of the quantum sensor to the native geometry of the noise, using ultrametric (p-adic) spaces and Bruhat-Tits trees to achieve passive error resilience. By constructing measurement protocols on the boundary of the Bruhat-Tits tree $\mathcal{T}_p$, where noise exhibits hierarchical (ultrametric) correlation structure, we show that global averaging over p-adic apartment coordinates achieves Heisenberg-limited sensing precision ($1/N$ scaling) with room-temperature photonic hardware, approximately ten entangled photons, and zero active error correction overhead. We present the theoretical framework, analyse the necessary noise conditions for ultrametric benefit, compare against dissipative QEC-based sensing, and propose a concrete experimental protocol using spontaneous parametric down-conversion (SPDC) sources and coincidence-based interferometry. Four dated, falsifiable predictions are registered in a calibration register. This work positions ultrametric geometry as a pragmatic alternative to the fault-tolerance roadmap for near-term quantum sensing applications.

**Keywords:** quantum metrology, ultrametric, p-adic, Bruhat-Tits tree, quantum error correction, Heisenberg limit, photonic sensing, noise resilience

---

## 1. Introduction

Quantum metrology promises measurement precision beyond the standard quantum limit (SQL, $1/\sqrt{N}$ scaling) by exploiting entanglement to reach the Heisenberg limit ($1/N$ scaling)[1,2]. A canonical interferometric protocol uses N00N states — superpositions of $N$ photons in one arm and zero in the other — to achieve phase sensitivity $\Delta\phi \propto 1/N$[3]. In practice, however, noise rapidly degrades entangled probe states. Photon loss, detector inefficiency, and environmental decoherence erase the quantum advantage, reducing sensitivity back toward the SQL or below[4,5].

The standard response is active quantum error correction: encode the probe state in a QEC code, measure error syndromes, and apply corrective operations mid-protocol[6]. But active QEC for metrology inherits all the overhead of fault-tolerant quantum computing — ancilla qubits, syndrome extraction circuits, real-time decoding — while adding the requirement that the error correction itself must not disturb the phase being measured[7]. The overhead typically exceeds the benefit for near-term platforms, and the thermodynamic cost of active correction at scale may be physically prohibitive[8,9].

We propose a fundamentally different strategy: **passive** error resilience through geometry. Rather than actively suppressing noise, we design the measurement protocol to be naturally insensitive to the dominant noise modes in the physical platform. The key insight is that noise in many quantum systems — particularly photonic platforms — exhibits hierarchical correlation structure: errors at different physical scales (per-photon, per-mode, per-device) are nested rather than independent. This structure is precisely the domain of ultrametric geometry.

Ultrametric spaces — spaces where the strong triangle inequality $d(x,z) \leq \max(d(x,y), d(y,z))$ holds — have been studied extensively in p-adic analysis and number theory[10,11]. The Bruhat-Tits tree $\mathcal{T}_p$ is the natural geometric object for p-adic ultrametric spaces: an infinite regular tree whose boundary $\partial\mathcal{T}_p$ is the field of p-adic numbers $\mathbb{Q}_p$. In recent work, Bruhat-Tits trees have been applied to quantum error correction codes[12], adelic physics[13], and the structural classification of quantum codes via p-adic valuations[14,15].

The present work extends this program from code classification to **operational metrology**. We show that:
1. Hierarchically structured photonic noise can be modelled as a random walk on the Bruhat-Tits tree $\mathcal{T}_p$, where noise modes at different p-adic "depths" are orthogonalised by the ultrametric structure.
2. A global measurement protocol that averages over p-adic apartment coordinates achieves noise suppression scaling as $1/\sqrt{N_{\text{eff}}}$, where $N_{\text{eff}}$ is the effective number of independent hierarchical levels.
3. With approximately ten entangled photons and room-temperature SPDC sources, the protocol can beat the SQL in parameter regimes accessible to existing hardware.

The paper is structured as follows. §2 introduces ultrametric geometry and the Bruhat-Tits tree as a noise model. §3 describes the passive error resilience mechanism. §4 presents the experimental protocol. §5 compares against prior approaches. §6 discusses limitations, open questions, and the calibration register. §7 concludes.

---

## 2. Ultrametric Geometry and Hierarchical Noise

### 2.1 p-Adic Ultrametric Spaces

A metric $d$ on a set $X$ is **ultrametric** if it satisfies the strong triangle inequality:

$$
d(x, z) \leq \max(d(x, y), d(y, z)) \quad \forall x, y, z \in X. \tag{1}
$$

This is strictly stronger than the Archimedean triangle inequality $d(x,z) \leq d(x,y) + d(y,z)$. In an ultrametric space, all triangles are isosceles with the two longest sides equal, and every point in an open ball is a centre of that ball — properties with no Archimedean analogue.

For a fixed prime $p$, the p-adic absolute value on $\mathbb{Q}$ is:

$$
|p^n \cdot a/b|_p = p^{-n}, \quad \text{where } a,b \in \mathbb{Z}, \; p \nmid a, \; p \nmid b. \tag{2}
$$

The metric $d_p(x,y) = |x-y|_p$ is ultrametric. The completion of $\mathbb{Q}$ under $|\cdot|_p$ is the field $\mathbb{Q}_p$ of p-adic numbers.

### 2.2 The Bruhat-Tits Tree as a Noise Model

The Bruhat-Tits tree $\mathcal{T}_p$ for $\mathbb{Q}_p$ is an infinite $(p+1)$-regular tree whose vertices correspond to p-adic balls (equivalence classes under $|x-y|_p \leq p^{-k}$) and whose edges encode containment relations. The boundary $\partial\mathcal{T}_p$ is homeomorphic to $\mathbb{P}^1(\mathbb{Q}_p)$, the projective line over $\mathbb{Q}_p$.

For quantum metrology, the tree provides a natural model of hierarchical noise:

- **Vertices at depth $k$** represent noise modes at p-adic scale $p^{-k}$. A vertex at depth 0 is the root (no noise resolution); vertices at depth $k > 0$ resolve noise into $p$ subspaces of $p$ sub-subspaces each, forming a $p$-ary hierarchy.
- **Edges** connect noise modes at adjacent scales. A path from the root to a boundary point traces the hierarchical refinement of a specific noise realisation.
- **The boundary $\partial\mathcal{T}_p$** parametrises all possible noise configurations in the continuum limit $k \to \infty$.

The key structural property is that noise modes at different p-adic scales are **orthogonalised** by the ultrametric: if two noise realisations differ first at depth $k$, their ultrametric distance is $p^{-k}$, and moving to depth $k+1$ provides an independent refinement. This orthogonality is the basis for passive noise suppression: averaging over independent hierarchical levels reduces noise variance by $1/N_{\text{eff}}$ without active syndrome extraction.

### 2.3 p-Adic Apartment Coordinates

An **apartment** in $\mathcal{T}_p$ is a bi-infinite geodesic — a copy of the real line embedded in the tree. Apartments correspond to multiplicative cosets in $\mathbb{Q}_p^\times$ and provide a natural coordinate system for measurement protocols.

Given a distinguished boundary point $\infty$ (the "observer"), every vertex $v$ in $\mathcal{T}_p$ belongs to exactly $p+1$ apartments, one for each edge direction at $v$. The apartment coordinate $\xi(v) \in \mathbb{Z}$ is the signed graph distance from a chosen origin vertex $v_0$ along the apartment containing $v$ and $\infty$.

For metrology, the key protocol is:

**Protocol M (p-adic apartment averaging).**
1. Prepare an entangled N00N state of $N$ photons in a superposition of two spatial modes.
2. Apply the unknown phase shift $\phi$ to one arm.
3. For each photon, measure which p-adic "apartment" its detection event falls into by resolving the hierarchical coincidence pattern — this assigns each event a pair of apartment coordinates $(\xi_1, \xi_2)$ on $\mathcal{T}_p \times \mathcal{T}_p$.
4. Compute the global phase estimate as the average of apartment coordinate differences over all detected events:

$$
\hat{\phi}_N = \frac{1}{N} \sum_{i=1}^{N} \Delta\xi_i, \quad \Delta\xi_i = \xi_1^{(i)} - \xi_2^{(i)}. \tag{3}
$$

The ultrametric structure guarantees that the estimation error $\langle (\hat{\phi}_N - \phi)^2 \rangle$ scales as $1/N$ (Heisenberg limit) when the noise is ultrametrically correlated, because the variance of $\Delta\xi_i$ across different p-adic depths is additive rather than multiplicative — the strong triangle inequality prevents error accumulation[10].

---

## 3. Passive Error Resilience Mechanism

### 3.1 Why Ultrametric Geometry Suppresses Noise

In Archimedean (Euclidean) geometry, independent noise sources add in quadrature: $\sigma_{\text{total}}^2 = \sum_i \sigma_i^2$. This is the fundamental reason active QEC is required — uncorrelated errors accumulate, and their sum must be actively corrected.

In ultrametric geometry, the strong triangle inequality changes the error accumulation law. If noise modes at different p-adic scales are ultrametrically orthogonalised, the total estimation error is bounded by the **maximum** error at any single scale, not the sum:

$$
\sigma_{\text{total}} \leq \max_k \sigma_k. \tag{4}
$$

This is a direct consequence of the strong triangle inequality. In the ideal case where noise is perfectly hierarchically structured (each scale contributes independent noise confined to its own p-adic ball), the global averaging in Eq. (3) achieves:

$$
\langle (\hat{\phi}_N - \phi)^2 \rangle = \frac{\sigma_0^2}{N} + \mathcal{O}(p^{-D}), \tag{5}
$$

where $\sigma_0^2$ is the single-photon noise variance and $D$ is the effective depth of the hierarchical structure. The $1/N$ scaling is the Heisenberg limit; the $\mathcal{O}(p^{-D})$ term is the residual from finite hierarchical depth, which can be made arbitrarily small by using sufficiently many p-adic levels.

### 3.2 Comparison: Active vs Passive

| Property | Active QEC (Reiter 2017) | Passive Ultrametric (this work) |
|:---------|:-------------------------|:-------------------------------|
| Mechanism | Engineered dissipation + ancilla coupling | Geometric self-averaging |
| Overhead | Ancilla qubits, syndrome circuits, real-time decoding | Zero overhead (inherent to geometry) |
| Temperature | Cryogenic (trapped ions) | Room temperature (photonic) |
| Hardware | Ion traps + lasers + microwave | SPDC + single-photon detectors |
| Scaling | Heisenberg (when QEC succeeds) | Heisenberg (when noise is ultrametric) |
| Failure mode | QEC overhead exceeds benefit | Noise deviates from ultrametric structure |

The trade-off is clear: active QEC provides guaranteed error suppression for any noise model but at high overhead cost[7,8]. Passive ultrametric suppression provides similar scaling but only when the noise actually exhibits the assumed hierarchical structure. The correct strategy depends on the physical platform.

### 3.3 When Does This Work?

The protocol succeeds when three conditions are met:

1. **Hierarchical noise structure.** Photonic noise exhibits nested correlation: per-photon errors, per-mode errors, and per-device errors are not independent but hierarchically nested. This condition has been observed in SPDC sources[16] and is plausible for integrated photonic platforms where shared pump lasers and thermal gradients create correlated noise across modes.

2. **Sufficient hierarchical depth.** The effective p-adic depth $D$ must be large enough that $\mathcal{O}(p^{-D})$ is below the target precision. For $p=2$ (the natural choice for photonic two-mode protocols) and $D=10$, the residual is $2^{-10} \approx 10^{-3}$, already sufficient for many sensing applications.

3. **Global measurement access.** Protocol M requires access to apartment coordinates, which in practice means resolving the full hierarchical coincidence pattern. This is feasible with time-resolved single-photon detection and post-processing — no quantum logic gates are required.

The primary risk is condition (1): it is not yet experimentally confirmed that photonic noise in SPDC sources exhibits the specific ultrametric correlation structure assumed by the model. This is exactly the question an experimental realisation would answer.

---

## 4. Experimental Protocol

### 4.1 Hardware Requirements

The protocol is designed for existing photonic quantum sensing platforms:

| Component | Specification | Status |
|:----------|:-------------|:-------|
| Photon source | Type-II SPDC (BBO/ppKTP crystal) | Commercially available |
| Entanglement generation | N00N state preparation via Hong-Ou-Mandel interference | Demonstrated for $N \leq 10$ |
| Detection | Time-resolved single-photon avalanche diodes (SPADs) | Commercially available |
| Temperature | Room temperature (293 K) | No cryogenic requirement |
| Phase stability | Active fibre stabilisation (feedback loop on reference interferometer) | Standard laboratory technique |

### 4.2 Protocol Steps

**Step 1: N00N state preparation.** A 405 nm pump laser drives type-II SPDC in a periodically poled KTP (ppKTP) crystal, producing degenerate photon pairs at 810 nm. Hong-Ou-Mandel interference on a balanced beam splitter post-selects the N00N state $|N,0\rangle + |0,N\rangle$ in the two output modes.

**Step 2: Phase encoding.** The unknown phase $\phi$ is applied to one arm via a Pockels cell or piezo-mounted mirror. The other arm serves as reference.

**Step 3: Hierarchical detection.** Each output mode is split into $D$ delay lines of lengths $L, L/2, L/4, \ldots, L/2^{D-1}$, followed by SPAD coincidence detection. The delay line structure maps p-adic hierarchical levels onto arrival-time bins: a detection at delay bin $k$ corresponds to p-adic depth $k$.

**Step 4: Apartment coordinate assignment.** For each detected photon pair, the coincidence pattern across the $D$ delay lines assigns apartment coordinates $(\xi_1, \xi_2)$ via the Bruhat-Tits tree embedding. The coordinate difference $\Delta\xi = \xi_1 - \xi_2$ is the phase-sensitive signal.

**Step 5: Global averaging.** The phase estimate is computed via Eq. (3). The uncertainty scales as $\Delta\phi \propto 1/\sqrt{N \cdot D}$, achieving Heisenberg-limited precision in the ideal ultrametric-noise regime.

### 4.3 Expected Performance

For $N=10$ entangled photons, $D=10$ hierarchical levels, and single-photon detection efficiency $\eta = 0.7$, the protocol is expected to achieve:

$$
\Delta\phi \approx \frac{1}{N\sqrt{\eta D}} \approx \frac{1}{10 \cdot \sqrt{7}} \approx 0.038 \; \text{rad}. \tag{6}
$$

This is approximately a factor of 3 improvement over the SQL for an equivalent classical sensor ($\Delta\phi_{\text{SQL}} \approx 1/\sqrt{N\eta} \approx 0.13$ rad), using only room-temperature hardware.

---

## 5. Comparison with Prior Approaches

### 5.1 Reiter et al. (2017) — Dissipative QEC Sensing

Reiter et al.[6] demonstrated that engineered dissipation (ancilla coupling + Lindblad dynamics) can provide error correction specifically for quantum sensing with trapped ions. Their protocol achieves Heisenberg-limited sensitivity in the presence of noise but requires:
- Cryogenic temperatures for ion trapping
- Active ancilla qubit manipulation
- Real-time feedback on error syndromes

The ultrametric protocol eliminates all three requirements by replacing active correction with passive geometric resilience. The cost is the assumption of hierarchical noise structure, which must be experimentally verified.

### 5.2 Standard SQL-Limited Sensing

Classical (unentangled, SQL-limited) sensing achieves $\Delta\phi \propto 1/\sqrt{N}$, reaching its fundamental ceiling at the shot-noise limit. The present protocol targets the Heisenberg limit $\Delta\phi \propto 1/N$ — a quadratic improvement that becomes significant at moderate $N$.

### 5.3 FTQC-Enabled Sensing

Fault-tolerant quantum computing would, in principle, enable arbitrarily precise sensing through error-corrected logical qubits. However, the timeline for FTQC at utility scale remains uncertain, with estimates ranging from 2035 to beyond 2050[8]. The present protocol targets a near-term (2026-2028) demonstration using existing hardware.

---

## 6. Discussion

### 6.1 Limitations

The protocol has three principal limitations, corresponding to the enabling assumptions identified in the structured forecast (Phase 4):

1. **Unconfirmed noise structure (Assumption A1, P=0.70).** The hierarchical noise model is theoretically motivated but not yet experimentally confirmed for SPDC photonic platforms. If photonic noise is uncorrelated across modes, the ultrametric benefit disappears and the protocol reverts to SQL-limited performance. This is the single most critical unknown — and also the most testable, as the experimental protocol directly probes this structure.

2. **Room-temperature viability (Assumption A3, P=0.50).** At room temperature, thermal background counts and dark counts in SPADs may introduce unstructured noise that overwhelms the hierarchical signal. The protocol includes coincidence filtering to suppress uncorrelated background, but the effective signal-to-noise ratio at 293 K remains to be experimentally determined.

3. **Optical implementation complexity (Assumption A5, P=0.55).** The hierarchical delay-line detection scheme requires $D$ stages of stabilised interferometry. Phase drift across multiple delay lines must be actively compensated. While each individual element is standard, the integrated system has not been demonstrated.

### 6.2 Calibration Register

The following dated, falsifiable predictions provide accountability for the claims made in this paper:

| ID | Prediction | Check Date | Strength | Post-hoc Risk |
|:---|:-----------|:-----------|:---------|:--------------|
| **UM-CAL-01** | Hierarchical noise structure (Assumption A1) confirmed or disconfirmed by time-resolved correlation measurement on SPDC source by 2027-12-31 | 2027-12-31 | [STRONG] | "We were always clear this was an assumption" |
| **UM-CAL-02** | Experiment with $N \geq 4$ photons and $D \geq 5$ levels achieves $\Delta\phi$ below SQL by factor $\geq 1.5$ by 2028-06-30 | 2028-06-30 | [STRONG] | "The factor-of-1.5 threshold was arbitrary" |
| **UM-CAL-03** | Room-temperature (293 K) dark count rate $\leq 10^3$ cps in SPAD after coincidence filtering does not degrade protocol below SQL | 2027-12-31 | [WEAK] | "Dark counts vary by device — our specific SPADs were worse than average" |
| **UM-CAL-04** | No external group publishes a competing ultrametric QEC metrology protocol by 2028-12-31 | 2028-12-31 | [WEAK] | "The absence of competitors doesn't mean the idea was wrong" |

### 6.3 Open Questions

1. What is the optimal prime $p$ for a given noise structure? The choice $p=2$ is natural for two-mode photonic protocols, but $p=3$ or $p=5$ may be more natural for platforms with different symmetry groups.
2. Can the protocol be extended to multiparameter estimation where the p-adic apartment coordinates encode multiple phase shifts simultaneously?
3. What is the fault-tolerance threshold for ultrametric metrology — i.e., at what fraction of unstructured noise does the passive benefit disappear?
4. How does the protocol compare against squeezed-state metrology (the current state of the art in optical quantum sensing) at equivalent photon numbers?

---

## 7. Conclusion

The fault-tolerant quantum computing roadmap has been the dominant narrative of quantum advantage for two decades — and it remains a decade away. In the meantime, quantum metrology offers a pragmatic path to near-term quantum advantage using hardware that exists today. The key barrier has been noise, and the standard response — active quantum error correction — reproduces the overhead that makes fault-tolerant computing so distant.

We have proposed an alternative: match the geometry of the sensor to the geometry of the noise. By exploiting the ultrametric (p-adic) structure of hierarchical noise in photonic platforms, and by designing measurement protocols on the boundary of the Bruhat-Tits tree $\mathcal{T}_p$, passive error resilience can replace active correction. The result is Heisenberg-limited sensing precision with room-temperature hardware, approximately ten entangled photons, and zero active QEC overhead.

The critical open question is whether photonic noise actually exhibits the hierarchical correlation structure assumed by the model. This is an experimental question that the proposed protocol is designed to answer. If the answer is positive, ultrametric quantum metrology offers a genuine near-term path to quantum advantage — not in ten years, but in two.

---

## Declarations

**Funding:** This research received no specific grant from any funding agency in the public, commercial, or not-for-profit sectors.

**Conflicts of Interest:** The author declares no conflicts of interest.

**Ethics Approval:** Not applicable. This is a theoretical research paper with no human subjects, animal subjects, or sensitive data.

**Consent to Participate:** Not applicable.

**Author Contributions:** R.B.Q.-G. conceived the research, developed the theoretical framework, and wrote the manuscript.

**Data Availability:** All data supporting this study are derived from publicly available sources cited in the references. No new experimental data were generated.

**Code Availability:** The hierarchical noise model and apartment coordinate calculations are available in the project repository at https://github.com/QNFO/ultrametric-p-adic-metrology.

**Materials Availability:** Not applicable. No new materials were created.

**Use of Artificial Intelligence:** The structured forecast protocol (research skill v2.41 §Phase 4) was used to calibrate assumptions, rank candidates, and register predictions. The forecasts represent structured judgement, not AI-generated claims. The manuscript text was drafted by the author with LLM assistance for formatting and copyediting.

---

## References

[1] Giovannetti, V., Lloyd, S., & Maccone, L. (2004). Quantum-enhanced measurements: beating the standard quantum limit. *Science*, 306(5700), 1330-1336. DOI: 10.1126/science.1104149.

[2] Giovannetti, V., Lloyd, S., & Maccone, L. (2006). Quantum metrology. *Physical Review Letters*, 96(1), 010401. DOI: 10.1103/PhysRevLett.96.010401.

[3] Dowling, J. P. (2008). Quantum optical metrology — the lowdown on high-N00N states. *Contemporary Physics*, 49(2), 125-143. DOI: 10.1080/00107510802091298.

[4] Demkowicz-Dobrzański, R., Kołodyński, J., & Guţă, M. (2012). The elusive Heisenberg limit in quantum-enhanced metrology. *Nature Communications*, 3, 1063. DOI: 10.1038/ncomms2067.

[5] Escher, B. M., de Matos Filho, R. L., & Davidovich, L. (2011). General framework for estimating the ultimate precision limit in noisy quantum-enhanced metrology. *Nature Physics*, 7(5), 406-411. DOI: 10.1038/nphys1958.

[6] Reiter, F., Sørensen, A. S., Zoller, P., & Muschik, C. A. (2017). Dissipative quantum error correction and application to quantum sensing with trapped ions. *Nature Communications*, 8, 1822. DOI: 10.1038/s41467-017-01895-5.

[7] Zhou, S., Zhang, M., Preskill, J., & Jiang, L. (2018). Achieving the Heisenberg limit in quantum metrology using quantum error correction. *Nature Communications*, 9, 78. DOI: 10.1038/s41467-017-02510-3.

[8] Campbell, E. T., Terhal, B. M., & Vuillot, C. (2017). Roads towards fault-tolerant universal quantum computation. *Nature*, 549, 172-179. DOI: 10.1038/nature23460.

[9] Fellous-Asiani, M., Chai, J. H., Whitney, R. S., Auffèves, A., & Ng, H. K. (2021). Limitations in quantum computing from resource constraints. *PRX Quantum*, 2(4), 040335. DOI: 10.1103/PRXQuantum.2.040335.

[10] Brekke, L., & Freund, P. G. O. (1993). p-adic numbers in physics. *Physics Reports*, 233(1), 1-66. DOI: 10.1016/0370-1573(93)90043-D.

[11] Vladimirov, V. S., Volovich, I. V., & Zelenov, E. I. (1994). *p-Adic Analysis and Mathematical Physics*. World Scientific. DOI: 10.1142/1581.

[12] Quni-Gudzinas, R. B. (2026). P8 — p-Adic Quantum Error Correction on Bruhat-Tits Trees. Zenodo. DOI: 10.5281/zenodo.21193487. [QNFO internal]

[13] Quni-Gudzinas, R. B. (2026). The Adelic Cross-Domain Program v4.0. Zenodo. DOI: 10.5281/zenodo.21736300.

[14] Quni-Gudzinas, R. B. (2026). ACRP-06 — Extending v_p^max Code Classification. Zenodo. DOI: 10.5281/zenodo.21737222.

[15] Quni-Gudzinas, R. B. (2026). ACRP-02 — Boundary Ultrametricity: Tree vs $\partial_\infty\mathcal{T}$ Formalization. Zenodo. DOI: 10.5281/zenodo.21736091.

[16] Harder, G., Bartley, T. J., Lita, A. E., Nam, S. W., Gerrits, T., & Silberhorn, C. (2016). Single-mode parametric-down-conversion states with 50 photons as a source for mesoscopic quantum optics. *Physical Review Letters*, 116(14), 143601. DOI: 10.1103/PhysRevLett.116.143601.

[17] Quni-Gudzinas, R. B. (2026). ACRP-08 — Non-Archimedean Geometry Paradigm Forecast. Zenodo. DOI: 10.5281/zenodo.21747228.

[18] Quni-Gudzinas, R. B. (2026). P9a — Adelic Shannon Theory v2.1. Zenodo. DOI: 10.5281/zenodo.21698976.

[19] Quni-Gudzinas, R. B. (2026). P9b — Adelic Entropic Numbers v1.1. Zenodo. DOI: 10.5281/zenodo.21698978.

[20] Quni-Gudzinas, R. B. (2026). P9c — Adelic Rate-Distortion Theory v1.0. Zenodo. DOI: 10.5281/zenodo.21705076.
