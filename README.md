## QK8 BB84 without Eve — Simple Guide

This repository contains a single Jupyter Notebook that demonstrates the BB84 quantum key distribution protocol without an eavesdropper (no Eve). It uses basic Python (lists, loops, `input()` prompts) and minimal Cirq to prepare and measure qubits.

### File
- `QK8 BB84 without Eve.ipynb` — the only notebook you need to run.

### Requirements
- Python 3.8+
- Jupyter Notebook or JupyterLab
- Internet access on first run (the notebook installs Cirq quietly via `!pip install --quiet cirq`).

### How to Run
1. Open `QK8 BB84 without Eve.ipynb` in Jupyter.
2. Run cells from top to bottom.
3. Follow the on-screen `input()` prompts to enter:
   - Number of qubits
   - Alice’s bits (0/1)
   - Alice’s bases (`R` or `D`)
   - Bob’s bases (`R` or `D`)

### What the Notebook Does
1. Downloads and imports Cirq.
2. Phase 1 — Sending (Alice):
   - Prompts for `no_of_qubits`, `alice_qubits` (0/1), and `alice_basis` (`R`/`D`).
   - Builds a Cirq circuit: applies `X` for bit 1; applies `H` for diagonal basis; (the code also applies `X` when basis is `R`, following the original file’s logic).
3. Phase 2 — Receiving (Bob):
   - Prompts for `bob_basis` per qubit (`R`/`D`).
   - Applies Bob’s basis operations (`X` for `R`, `H` for `D`) and measures all qubits at once.
   - Stores measurement results in `bob_measurements`.
4. Phase 3 — Comparison (Sifting):
   - Compares `alice_basis` and `bob_basis`.
   - Keeps positions where bases match; builds `shared_key_alice` and `shared_key_bob`.
   - Reports counts: `matched_count` and `not_matched_count`.

### Variables (as used in the notebook)
- `no_of_qubits`: number of qubits to send.
- `alice_qubits`: list of integers (0/1) entered by Alice.
- `alice_basis`: list of `'R'` or `'D'` for Alice’s basis choices.
- `qubits`: list of `cirq.LineQubit` created for the circuit.
- `circuit`: `cirq.Circuit` holding the operations.
- `bob_basis`: list of `'R'` or `'D'` for Bob’s measurement bases.
- `simulator`: `cirq.Simulator()` instance used to run the circuit.
- `bob_measurements`: list of integers (0/1) from Bob’s measurement.
- `shared_key_alice`, `shared_key_bob`: sifted keys where bases matched.
- `matched_count`, `not_matched_count`: basis match statistics.

### Notes
- This version does not simulate Eve (no eavesdropper). It focuses on the core BB84 flow only.
- The notebook uses explicit loops and lists; it relies on `input()` for simplicity.
- The circuit logic mirrors the original file, including the basis operations.

### Learn More
- BB84 overview (introductory articles)
- Cirq documentation: `https://quantumai.google/cirq`


