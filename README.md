# Tyk2 SBDD — Structure-Based Reasoning & SAR Analysis

**A structure-based drug design reasoning exercise on Tyk2: prep a real co-crystal, understand the ATP binding site, pull measured SAR from ChEMBL, predict activity rank-order from structure, and analyze where structure-based prediction succeeds and fails.**

This is a companion to [AlchemyBench](../AlchemyBench) (relative-binding FEP on the Tyk2 JACS benchmark). Both target the **same Tyk2 congeneric series**, so the structure-based reasoning here and the physics-based free energies there converge on one integrated target story.

> **Scope, stated honestly:** this demonstrates SBDD *judgment* on a real target with real SAR — structure prep choices, binding-site pharmacophore reasoning, activity-cliff analysis, and honest assessment of where docking/scoring fails. It is target-analysis and method reasoning, not a live discovery program.

## The point (vs. a docking tutorial)

The value is *reasoning about a real target*, not running a pipeline. Concretely:
- **Conscious structure prep** — PDB **4GVJ** (Tyk2 **JH1** ATP site), with documented protonation / resolution / missing-loop decisions.
- **Binding-site understanding** — hinge, gatekeeper, catalytic Lys / αC-Glu, DFG, P-loop, in chemical language.
- **Real SAR** — Tyk2 IC50 data from ChEMBL, cleaned to pIC50.
- **Predict then check** — rank-order predicted from structure *before* looking at measured values.
- **Failure analysis** — activity cliffs (SALI) where structure-based scoring notoriously breaks.

## A target-biology detail worth knowing

Tyk2 has two druggable sites: **JH1** (active kinase, ATP-competitive — where the JACS benchmark ligands bind) and **JH2** (pseudokinase, where the modern *selective* inhibitors like deucravacitinib bind). This project targets JH1 to match the benchmark ligands; the field's selectivity story living in JH2 is noted as target context.

## Layout

```
notebooks/01_target_and_sar.ipynb   PDB fetch, site pharmacophore, ChEMBL SAR pull + cleaning
notebooks/02_activity_cliffs.ipynb   (next) similarity, SALI cliffs, structure-vs-activity test
data/                                 fetched PDB + cleaned SAR csv
analysis/                             reusable metric functions
```

## Environment

Runs in the `teachopencadd` conda env (RDKit + ChEMBL web client + pandas already present). CPU-only, no GPU.
