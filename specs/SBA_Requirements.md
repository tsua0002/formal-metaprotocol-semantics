# Formal Requirements for State-Bound Assets (SBA)

A protocol is considered SBA-compliant if it satisfies the following structural properties:

1. **Atomic Reification**: Every semantic state transition must be uniquely mapped to a physical UTXO transformation.
2. **Witness Binding**: The semantic intent must be committed within the witness stack of the transaction, creating a non-malleable link.
3. **Equalizer Constraint**: The physical address of the asset (on-chain) must be an algebraic consequence of the semantic state (off-chain).

### The Equalizer Equation
In a categorical sense, the SBA Covenant acts as an equalizer of two parallel morphisms:
- `f`: The physical observation of the UTXO structure.
- `g`: The semantic intent decoded from the witness.
Validity is defined as the subobject where `f = g`.
