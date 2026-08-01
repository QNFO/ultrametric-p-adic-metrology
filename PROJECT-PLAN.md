# PROJECT-PLAN — Ultrametric p-Adic Quantum Metrology

## 1. Charter

**Research question:** Can ultrametric (p-adic) geometry provide passive error resilience for quantum sensing, achieving near-term quantum advantage without active quantum error correction?

**Core claim:** Noise in quantum systems exhibits hierarchical (ultrametric) correlation structure that active QEC treats as an enemy. By matching the geometry of the sensor to the native geometry of the noise — using p-adic spaces and Bruhat-Tits trees — we can achieve Heisenberg-limited sensing precision with room-temperature hardware, ~10 entangled photons, and zero active error correction overhead.

**Motivation:** The fault-tolerant quantum computing roadmap has been "10 years away" for 40 years. The thermodynamic cost of active QEC at utility scale may be physically prohibitive. This project explores whether a fundamentally different geometry offers a shorter path to quantum advantage.

## 2. Work Breakdown Structure

| Phase | Name | Status | Deliverables |
|---|---|---|---|
| **0** | Project Init | ✅ Complete | Repo, scaffold, PROJECT-PLAN, .gitignore |
| **1** | Due Diligence | ✅ v0.2 | KG query, D1 cross-ref, external literature search, gap analysis |
| **2** | Literature Search | ✅ v0.3 | Multi-source search (OpenAlex, Crossref, Zenodo, Europe PMC, arXiv, web, Vectorize, KG), dedup, classify |
| **3** | Citation Management | ⏳ Deferred | Extract citations, verify BibTeX, auto-generate missing DOIs — deferred until paper draft exists |
| **4** | Structured Forecast | ✅ v0.5 | Domain assessment, candidate ranking, assumption audit, red-team, sensitivity analysis, calibration register, effort allocation, practical applications, counterfactual backcasting — Light version (Stages 7-8 deferred) |
| **5** | Publication | 📝 In Progress | Write paper (`ultrametric-p-adic-metrology.md`), build PDF, Zenodo upload with DOI |
| **6** | Deployment | ⬜ Pending | D1 living-paper insert, papers-server Worker verification, R2 archive |
| **7** | Dissemination | ⬜ Pending | SEO audit, Buffer social media, CWI summer school follow-up, papers.qnfo.org verification |
| **8** | Core Distribution | ⬜ Pending | GitHub push + tag, Zenodo new-version, R2 archive sync, D1/KG records, DNSLink (optional) |

## 3. Milestones

| Date | Milestone | Gate Criteria |
|---|---|---|
| 2026-07-31 | Phase 0 complete | Repo created, scaffold populated, git tag v0.1 |
| 2026-08-15 | Phase 1 complete | Due diligence report committed |
| 2026-08-26 | CWI Summer School | Poster presented, feedback collected |
| 2026-09-15 | Phase 4 complete | Structured forecast protocol artifacts committed |
| 2026-09-30 | Phase 5 complete | Paper published on Zenodo with DOI |
| 2026-10-15 | Phase 8 complete | Core distribution verified across all 4 layers |

## 4. Deliverable Registry

| ID | Deliverable | Path | Format | Archival Target |
|---|---|---|---|---|
| D1 | Paper manuscript | `ultrametric-p-adic-metrology.md` | Markdown | Zenodo + GitHub + R2 |
| D2 | Rendered PDF | `releases/ultrametric-p-adic-metrology.pdf` | PDF | Zenodo + R2 |
| D3 | Due diligence report | `artifacts/phase1-due-diligence.md` | Markdown | GitHub + R2 |
| D4 | Literature classification | `artifacts/phase2-literature.md` | Markdown | GitHub + R2 |
| D5 | Structured forecast | `artifacts/structured-forecast-protocol-v2.md` | Markdown | GitHub + R2 |
| D6 | PROVENANCE-BUNDLE | `releases/PROVENANCE-BUNDLE.zip` | ZIP | Zenodo + R2 |
| D7 | CWI poster | `QNFO/cwi-qec-poster-2026` | HTML/SVG | GitHub + Zenodo |

## 5. Risk Register

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | Literature search finds prior art on p-adic QEC that weakens novelty claim | Medium | Medium | Niche is small; existing p-adic QEC literature is sparse. Document overlap honestly in due diligence. |
| R2 | Numerical benchmarks show no decoding advantage over surface codes | Medium | High | The claim is about metrology (sensing), not computation. Benchmarks should compare against classical sensors, not surface-code logical gates. |
| R3 | Industry dismisses metrology as "niche" | Medium | Low | $100B+ sensing market is not niche. Frame as complementary, not competitive. |
| R4 | No industry contacts from CWI summer school | Medium | Medium | Follow up via email/LinkedIn regardless. Conference is one channel, not the only channel. |
| R5 | PDF build fails with Unicode issues | Low | High | Use `scripts/build-paper.py` with UTF-8 forced encoding. Pre-publish check for U+FFFD. |

## 6. Success Criteria

1. Paper published on Zenodo with permanent DOI by September 2026
2. At least one industry conversation from CWI summer school leads to follow-up
3. Core distribution verified: GitHub + Zenodo + R2 + D1/KG
4. Buffer social media dissemination to Twitter/X, LinkedIn, Bluesky
5. Zero U+FFFD/U+FFFF rendering errors in published PDF

## 7. Related Projects

| Project | Repo | DOI |
|---|---|---|
| Adelic Physics Programme (P1-P9) | `QNFO/adelics` | Multiple |
| Adelic Epistemological Foundations | `QNFO/adelic-epistemological-foundations` | 10.5281/zenodo.21685479 |
| CWI QEC Poster 2026 | `QNFO/cwi-qec-poster-2026` | — |
| Adelic Shannon Theory v2.1 | — | 10.5281/zenodo.21698976 |
| Adelic Entropic Numbers v1.1 | — | 10.5281/zenodo.21698978 |
| Adelic Rate-Distortion Theory v1.0 | — | 10.5281/zenodo.21705076 |
| ACRP-08 Paradigm Forecast | `QNFO/acrp08-paradigm-forecast` | 10.5281/zenodo.21747228 |
| ACRP-02 (ZBW P1 Correction) | `QNFO/zbw-majorana-tqc` | 10.5281/zenodo.21736091 |

## 8. Core Claim Lock (§1.2)

**Original claim:** Active quantum error correction is thermodynamically prohibitive at utility scale, and an ultrametric (p-adic) geometric framework can achieve passive error resilience for quantum metrology applications.

**Reformulation (falsifiable):** A p-adic photonic sensor with N ≤ 10 entangled photons at room temperature can achieve measurement precision below the standard quantum limit (SQL) by a factor of at least √N, without active error correction, within 24 months of project initiation.

**Falsification condition:** If after constructing and testing a p-adic photonic sensor prototype, the measured precision does not exceed the SQL by the claimed factor, the core claim is disconfirmed.

## 9. Version History

| Version | Date | Description |
|---|---|---|
| v0.1-phase0 | 2026-07-31 | Initial scaffold — repo, PROJECT-PLAN, WBS, risk register, core claim lock |
