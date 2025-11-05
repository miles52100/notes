# Resource PKI

From the Introduction reference

>RPKI allows holders of Internet number >resources to make verifiable statements >about how they intend to use their >resources. To achieve this, it uses a public >key infrastructure that creates a chain of >resource certificates that follows the same >structure as the way IP addresses and AS >numbers are handed down.
>
>...
>
> Currently, RPKI is used to let the legitimate holder of a block of IP addresses make an authoritative statement about which AS is authorised to originate their prefix in the BGP. In turn, other network operators can download and validate these statements and make routing decisions based on them. This process is referred to as route origin validation (ROV). This provides a stepping stone to provide path validation in the future.
>
>In addition to RPKI not having any identity information, there is another important difference with commonly used X.509 PKIs, such as SSL/TLS. Instead of having to rely on a vast number of root certificate authorities which come pre-installed in a browser or an operating system, RPKI relies on just five trust anchors, run by the RIRs. These are well established, openly governed, not-for-profit organisations. Each organisation that wishes to get an RPKI resource certificate already has a contractual relationship with one or more of the RIRs.
>
>In conclusion, RPKI provides a mechanism to make strong, testable attestations about Internet number resources. I

---
---

## References

Introduction [rpki_docs](https://rpki.readthedocs.io/en/latest/about/introduction.html)
