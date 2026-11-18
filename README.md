# OPN computational verification

Companion to *An Exponent Restriction for Odd Perfect Numbers Not Divisible by Three*, by M. R. DeDeo.

This revision uses the two-output bound `169/99` and assigns exponent four to non-Euler output primes in the forced-divisor calculation. It supersedes the earlier computation with 99 excluded seed sets and 17 minimal sets.

## Reproduction

Extract the archive, preserve its directory structure, and run from the `OPN_verification` directory:

```sh
python3 verify_all.py
```

Python 3.8 or later is required; no third-party packages are needed. LaTeX is not needed for verification. The tested interpreter is recorded in `reproduction_receipt.json`.

The driver checks the SHA-256 manifest, copies `verification/` to a temporary directory, and runs seven tasks. Each task must pass, and its regenerated record must agree with the archived record. Only the interpreter-version field is omitted from record comparison. The packaged certificates remain unchanged.

A successful run prints a JSON object with `status: PASS`, seven successful checks, and `archived_record_matched: true` for every check. To retain a new receipt:

```sh
python3 verify_all.py > new_reproduction_receipt.json
```

Each task has a 120-second timeout. On substantially slower hardware, the timeout in `verify_all.py` can be increased in a working copy; its manifest hash must then be regenerated. A timeout means the calculation did not finish within the allowed time.

## Correspondence to the article

| Program under `verification/` | Calculation |
|---|---|
| `opn_pivot16/verify_residue_exclusion.py` | The 86 source factorizations, mixed-source minima, finite product, and rational two-output tail in Section 2 |
| `opn_audit17/check_certificate.py` | Separate read-only check of that certificate, including four damaged records that must be rejected; invoked by the output-bound and three-output tasks |
| `opn_stage18/verify_two_exception_bounds.py` | The revised two-output constant, residue cases, and the 1600 cutoff in Section 3 |
| `opn_stage19/verify_three_output_exclusion.py` | The Euler-prime comparison, output lists, three-output enumeration, and rational tail estimates in Sections 3–4 |
| `opn_stage19/check_head_independently.py` | The same finite maximum by direct radical divisibility and integer cross multiplication |
| `opn_review25/review_three_exception.py` | Fresh factorization, unordered-support enumeration, rational comparisons, and the numerical bounds for the three-exception residue corollary; imports no project code or certificates |
| `opn_stage21/verify_forced_families.py` | The strengthened seed inventory, including every permitted Euler choice, in Section 5 |
| `opn_stage21/check_forced_families_independently.py` | Separate factorization and bit-mask enumeration, using integer divisor sums and cross multiplication to check every Euler choice, lower bound, and minimal set |

## Expected results

| Calculation | Expected result |
|---|---|
| Source primes in the finite interval | 86 |
| Uniform two-output bound | `169/99` |
| Two-output logarithmic tail bound | `3244296875/350791685712 < 1/100` |
| Output configurations, with the Euler prime distinguished | 907,360 |
| Maximum finite contribution | `538811/328320` |
| Maximizing assignment | `(q,r,s) = (13,7,31)` |
| Sources at the maximum | `5, 191` |
| Final upper bound for the reduced three-output case | `50/27 < 2` |
| Seed subsets examined | 511 |
| Excluded seed subsets | 103 |
| Inclusion-minimal excluded seed sets | 18 |
| Remaining seed subsets not excluded by this test | 408 |
| Forced-prime counts in the minimal seed sets | 10 through 15 |
| Bound in the three-exception residue corollary | `2873/1440 < 2` |

The seed certificate records the supports, Euler choices, forced divisors and divisor sums, exact rational lower bounds, and minimal-family coverage. Source primes receive exponent two; non-Euler outputs receive exponent four; a permitted Euler output receives exponent one. An Euler prime outside the forced support is also allowed.

## Files and scope

The archive contains nine Python programs, eight JSON records including the reproduction receipt, this README, a SHA-256 manifest, and two optional LaTeX listing wrappers. The wrappers include the current files and can regenerate readable listings. No previously generated listings PDF is included in this revision.

`MANIFEST.sha256` covers nineteen files, excluding itself and the top-level reproduction receipt. Hashes check file integrity. The independently implemented calculations check finite arithmetic. The mathematical reductions, published prime-power and primitive-divisor inputs, and the justification of the infinite-tail bounds remain in the article.

The primitive-divisor corollary in Section 5 requires no additional finite enumeration. The numerical comparisons in the other new corollary are checked by the standalone review program.

The source directory names are retained to preserve relative paths; they do not identify theorem numbers in the revised manuscript.
