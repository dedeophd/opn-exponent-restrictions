# Odd Perfect Numbers: Exponent Restrictions

Computational verification materials for **An Exponent Restriction for Odd Perfect Numbers Not Divisible by Three**, by **M. R. DeDeo**.

## Mathematical result

Let $N=q^k\prod_{i=1}^{t}p_i^{a_i}$ be an odd perfect number in Eulerian form, with $3\nmid N$. The paper proves that at least three non-Euler exponents satisfy $a_i\not\equiv2\pmod6$.

Thus at least three distinct non-Euler prime-power components must have exponents outside the sequence $2,8,14,\ldots$. Since these exponents are even, each such exponent is congruent to $0$ or $4$ modulo $6$. The result requires no upper bound on the size of $N$, its component exponents, or its number of prime factors.

The proof combines cyclotomic divisibility, abundancy estimates, exact finite computations, and analytic bounds on the infinite remainder. Complementary computations identify seventeen inclusion-minimal forbidden combinations from a specified pool of nine source primes.

## Download and run

Download the verification ZIP archive from this repository and extract it. The archive contains a directory named `OPN_verification`. Preserve its internal directory structure.

**Requirements:** Python 3.8 or later. No third-party Python packages are required. LaTeX is not needed to run the verification.

Open a terminal in the extracted directory and run:

```bash
cd OPN_verification
python3 verify_all.py
```

On Windows, if Python is installed through the Python launcher, use:

```powershell
cd OPN_verification
py -3 verify_all.py
```

The driver checks seventeen SHA-256 manifest entries, copies the verification programs and records into a temporary directory, and runs five verification tasks there. The packaged records remain unchanged.

A successful run prints a JSON object containing `"status": "PASS"`, `"manifest_files": 17`, and five check results, each with `"status": "PASS"`.

To save your own reproduction receipt:

```bash
python3 verify_all.py > new_reproduction_receipt.json
```

The archived `reproduction_receipt.json` records a successful run with Python 3.12.14. Each task has a 120-second timeout; slower hardware may exceed this limit. A timeout indicates that the task did not finish within the allotted time, rather than a failed mathematical inequality.

## Expected results

| Computation | Expected result |
|---|---|
| Three-output enumeration | 907,360 role-weighted configurations |
| Maximum finite contribution | `538811/328320` |
| Maximizing assignment | `(q,r,s) = (13,7,31)` |
| Small source primes at the maximum | `5, 191` |
| Bound used in the final comparison | `50/27 < 2` |
| Nonempty subsets of the nine-prime seed pool | 511 |
| Excluded subsets | 99 |
| Inclusion-minimal excluded subsets | 17 |

The separate finite-maximum checker uses a second implementation. An additional enumeration uses unordered output supports and checks agreement with the role-weighted count.

## Package contents

The ZIP contains nineteen files: eight Python programs, seven JSON records, a README, a SHA-256 manifest, and two optional LaTeX listing wrappers.

| File or directory | Purpose |
|---|---|
| `verify_all.py` | Runs the manifest check and all five verification tasks |
| `MANIFEST.sha256` | Records hashes for seventeen packaged files |
| `reproduction_receipt.json` | Archived successful execution receipt |
| `verification/opn_pivot16/` | Source factorizations, residue exclusions, and their certificate |
| `verification/opn_audit17/` | Source-certificate checker invoked by the two-exception task |
| `verification/opn_stage18/` | Two-exception bounds and archived results |
| `verification/opn_stage19/` | Three-output enumeration, separate finite-maximum checker, and certificates |
| `verification/opn_review25/` | Enumeration using unordered output supports and its receipt |
| `verification/opn_stage21/` | Forced-divisor seed-family computation and certificate |
| `OPN_py_listings.tex` | Optional legacy LaTeX wrapper for Python listings |
| `OPN_json_listings.tex` | Optional legacy LaTeX wrapper for JSON listings |

The directory names are retained because the programs use relative paths. The two LaTeX wrappers are not needed for verification. The formatted computational supplement accompanies the paper separately.

## Scope and reproducibility

The programs verify the finite calculations supporting the paper. The mathematical reductions and the justification of the analytic bounds remain in the article. A successful computation is not a machine-checked proof of the entire theorem or an external peer review.

The manifest checks byte consistency. It excludes itself and the top-level reproduction receipt. The README inside the archive is covered by the manifest: editing that file will cause the integrity check to fail. This repository README is separate from the archived README.

For reproduction of the paper's calculations, use the preserved verification archive. Any subsequent code changes should be distinguished from that archived snapshot.

## Citation

When referring to these computations, cite the accompanying paper:

> M. R. DeDeo, *An Exponent Restriction for Odd Perfect Numbers Not Divisible by Three*.

