# Formal Semantics for Bitcoin Meta-Protocols

[![Agda](https://img.shields.io/badge/Formal_Verification-Agda-orange.svg)](https://wiki.portal.chalmers.se/agda/pmwiki.php)
[![Category Theory](https://img.shields.io/badge/Mathematics-Category_Theory-blue.svg)](https://ncatlab.org/nlab/show/category+theory)
[![Bitcoin](https://img.shields.io/badge/Protocol-Bitcoin-gold.svg)](https://bitcoin.org/bitcoin.pdf)

## Overview

This repository hosts a formal framework for analyzing and resolving the **Semantic Gap** in Bitcoin Layer 2 (L2) and meta-protocol architectures. 

In current implementations (e.g., Inscriptions, BRC-20), there is a critical disconnect between the **Accounting Layer** (UTXO-based physical movements) and the **Applicative Layer** (off-chain semantic state transitions). This gap necessitates a reliance on trusted third-party indexers, which undermines Bitcoin's "Don't Trust, Verify" ethos.

**Our Objective:** To provide a mathematical foundation for **State-Bound Assets (SBA)** by modeling Bitcoin transactions as categorical structures where semantic validity is a natural consequence of the on-chain consensus.

---

## Theoretical Foundations

This research builds upon and extends several seminal works in formal methods and protocol design:

1.  **Ledger Structures:** We utilize the monoidal category framework defined by **Chad Nester (2021)** in *"A Foundation for Ledger Structures"* to model resources and their transformations.
2.  **Naturality & Reification:** Following **Mac Lane**, we define the "Semantic Binding" not as a simple procedural check, but as a **natural transformation** between the Semantic State Functor ($S$) and the Physical Ledger Functor ($L$).
3.  **Denotational Semantics:** We target **Simplicity (O'Connor, 2017)** as the low-level execution language, leveraging its finitary completeness and formal properties.

---

## Key Research Contributions

### 1. The Naturality Gap Theorem
We formally characterize the "Semantic Gap" as a failure of commutativity in the interpretation diagram. We provide an Agda-verified proof that without **Witness Introspection**, full state-binding is mathematically impossible at the base layer.

### 2. Categorical Reification of Vaults
We model complex Bitcoin Covenants (Vaults) as **equalizer constraints** within a distributive category. This ensures that a transaction is only physically valid if it is the unique "lifting" of a valid semantic transition.

### 3. Structural Isomorphism in Compilers
Research into static analysis pipelines (building on **Bithoven**) to ensure that high-level imperative contract logic is structurally isomorphic to its optimized Bitcoin Script output, preventing stack and liveness vulnerabilities by construction.

---

## Repository Structure

*   `proofs/`: Agda formalization of the Ledger/Semantic functors and the Naturality Theorem.
*   `specs/`: Formal specifications for **State-Bound Assets (SBA)** and analysis of community standards.
*   `models/`: Category theory models for introspective covenants using MAST and Schnorr signatures.
*   `analysis/`: Comparative study of meta-protocols (Inscriptions vs. SBA-compliant protocols like OPI-003).

---

## Case Study: The OPI-003 Standard

As a primary case study for this framework, we analyze the community-led **OPI-003 (Standard "W")** [proposal](https://github.com/The-Universal-BRC-20-Extension/OPI/blob/main/OPI/OPI-003-W.md). We demonstrate how its use of `W_PROOF` witness commitments and dual-transaction "Commit/Reveal" cycles attempts to satisfy the conditions of our **Natural Transformation** model. 

*Our work provides the first formal verification of the OPI-003 state-binding mechanism, highlighting the language extensions required (e.g., specific Simplicity Jets) to achieve total trust-minimization.*

---

## Collaboration & Research

I am actively seeking feedback and collaboration from the formal methods and Bitcoin core research communities.

**Current Research Areas:**
*   Standardizing **Witness-Introspective Jets** for Simplicity.
*   Proving **Coinductive Robustness** for infinite transaction chains (PCD).
*   Categorical treatment of **Nash Equilibria** in collateralized L2 bridges.

If you are a researcher (CNRS, Tallinn UT, Blockstream Research, etc.) or a PhD supervisor interested in these topics, please reach out via [LinkedIn](https://www.linkedin.com/in/thomas-s-92932889) or open an issue.

---

## License

This research and the associated formal proofs are released under the [MIT License](LICENSE).
