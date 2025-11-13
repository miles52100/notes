# SALSA write-up Initial notes

Rough notes for the write up of SALSA

To cover

- [ ] PQC context

- [ ] Underlying hard problem

- [ ] State of the art for attacking hard problems

- [ ] What the papers do

- [ ] Key results

- [ ] Conclusion

## PQC context

## Underlying hard problem

### Context

The underlying hard problem in CRYSTAL-KYBER, see [Ref](#references), is
*Module Learning With Errors* (MLWE).
A simplified problem is the *Learning With Errors* (LWE).

### Notation

Some standard notation:

- $n$ - dimension of the lattice (in FIPS-203](#references), $n=256$)
- $q$ - a prime (in [FIPS-203](#references), $n=3329=2^8\cdot 13 +1$)
- $\mathbb{Z}_q:=\mathbb{Z}/q\mathbb{Z}$
- $\mathbf{s}\in\mathbb{Z}^{n}_{q}$ - the secret vector
- $e$ - error value sampled from a distribution, $\chi$, over $\mathbb{Z}_q$ (e.g., the Discrete Gaussian distribution)
- $a$ - a random vector in $(\mathbb{Z}^{n}_{q})^m$ (identified with $\mathbb{Z}^{m\times n}_{q})$, typically from the Uniform distribution
- $b$ - Element of $\mathbb{Z}$ defined by $b=\langle a, s \rangle + e$
- $\mathcal{A}_{\mathbf{s},\chi}$ - the distribution over $\mathbb{Z}^{m\times n}_{q}\times \mathbb{Z}^{m}_{q}$ represened by elements $(\mathbf{a},\mathbf{e})$ drawn according to the above distributions

### LWE

The LWE problem is 

> Given $(a,b)\in\mathbb{Z}^{m\times n}_{q}\times \mathbb{Z}^{m}_{q}$ drawn randomly from $\mathcal{A}_{\mathbf{s},\chi}$, with the distribution $\chi$ known.
>
> Find $\mathbf{s}\in\mathbb{Z}^{n}_{q}$

There are various refinements and reductions. The above is often called the *search LWE*, in contrast to the *decision LWE*. The latter is simply to distinguish a sample $(a,b)\sim\mathcal{A}_{\mathbf{s},\chi}$, from one drawn from the Uniform distribution on $\mathbb{Z}^{m\times n}_{q}\times \mathbb{Z}^{m}_{q}$.

There's a reduction from the $search$ to the $decision$ version of LWE (provided $q$ is prime and $n=O(f(q))$, for some polynomial $f$)

The exact relationship between these problems is filled with technicalities, but an important result is Brakerski et al. who show a reduction of
$\textrm{GAP}_\gamma$ to *decision* LWE (with modulus $q$ polynomial in $n$)

## State of the art for attacking hard problems

pass

## What the papers do

pass

## Key results

pass

## Conclusion

pass

## References

pass

- [SALSA](https://arxiv.org/pdf/2207.04785)

- [SALSA-PICANTE](https://arxiv.org/pdf/2303.04178v3)

- [Lattice Attacks for variants of LWE](https://www.youtube.com/watch?v=gPUgjzVHb9k)

- [Khyber](https://pq-crystals.org/kyber/)
  
- [Nist PQC project](https://csrc.nist.gov/Projects/Post-Quantum-Cryptography)

- [NTT Intro](https://eprint.iacr.org/2024/585.pdf)

- [Classical Reduction of SVP to LWE: A Concrete Seurity Analysis](https://iacr.steepath.eu/2020/880-ClassicalReductionofSVPtoLWEAConcreteSecurityAnalysis.pdf)

- [benchmarking attacks on LWE](https://csrc.nist.gov/csrc/media/Projects/post-quantum-cryptography/documents/pqc-seminars/presentations/17-benchmarking-lwe-attack-08062024.pdf)

blah blah
blah blah
blah blah
blah blah
blah blah

## More sections

blah blah
blah blah
blah blah
blah blah
blah blah
blah blah
blah blah
blah blah

## More sections and more

blah blah
blah blah
blah blah
blah blah
blah blah
blah blah
blah blah
blah blah

## More sections and more and more

From [Refs](#references) Nist PQC project, FIPS 203, FIPS 204 and FIPS 205, which specify algorithms derived from CRYSTALS-Dilithium, CRYSTALS-KYBER and SPHINCS+, were published August 13, 2024.

In particular FIPS 203 describes the 'Module-Lattice-Based Key-Encapsulation Mechanism Standard' which is NIST's selection of the 'CRYSTAL-KYBER' candidate.
