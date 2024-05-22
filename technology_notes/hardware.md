# Hardware notes

A somewhat random collection

# Size prefixes

| Prefix | Abbrv | Order of Mag |
|:-----|--------:|----------:|
|Giga |G| 10**9 |
|Tera |T| 10**12|
|Peta |P| 10**15|
|Exa, |E| 10**18|
|Zetta|Z| 10**21|
|Yotta|Y| 10**24|


# Basic Physics and Power
Rough guide
CPU uses 65-150 watts
G|U|uses 30-1000 watts
RAM uses 2-3.5 watts
Hard drives use 5-10 watts (depends on type)



## ASIC
Application-specific integrated circuit. A microchip designed for a special application.


## FPGA
Field-programmable gate array, a type of IC that can be programmed or reprogrammed after manufacture. Consists of an array of programmable logic blocks and interconnects.

## CPU
General purpose computing brain

## GPU
Specialised processor that accelerates parallelized computations.

## DPU
Processor that processes data that moves around the data center, such as network, security and storage functions.

## IPU
Infrastructure processing chips

## SmartNICs, IPUs, DPUs
See [here](https://www.theregister.com/2021/11/24/infrastructure_processing_units/) for a Register article on an interesting trend in data centres.
See [blog](https://blogs.nvidia.com/blog/2021/10/29/what-is-a-smartnic/)

## Apple's Neural Engine
A specialized NN unit called the Apple Neural Engine (ANE) that's faster and more 
efficient than CPU or GPU.

See [here](https://www.makeuseof.com/what-is-a-neural-engine-how-does-it-work/?newsletter_popup=1)


## ARM64 vs AMD64

Both are Instruction Set Architectures, ISA.

ARM64 developed by ARM Holdings

AMD64 is a 64-bit extension of the x86 ISA for microprocessors.
First implemented by AMD in 2003, and since adoptd by many companies incl.
Intel, and VIA Technologies.

Comparison of these two can be found [here](https://allthedifferences.com/difference-between-arm64-and-amd64-which-is-faster/).
A Visual Capitalist [chart](https://www.visualcapitalist.com/nvidia-vs-amd-vs-intel-comparing-ai-chip-sales/) is also interesting

There's an interesting tech comparison between the AMD M1200 vs A100 [here](https://www.nextplatform.com/2021/12/06/stacking-up-amd-mi200-versus-nvidia-a100-compute-engines/)

The main difference between these two is 

  * ARM64 is a RISC - Reduced Instruction Set Computing architecture
  * AMD64 is a CISC - Complex Instruction Set Computing architecture

  



## Software Defined Networks, SDN

See [here](https://sdn.systemsapproach.org/) and [paper](https://www.sigcomm.org/sites/default/files/ccr/papers/2014/April/0000000-0000012.pdf)

## P4 Programming Language and P4 PRogrammable Switch
A domain-specific programming language used to describe a programmable forwarding hardware processes: can be ASIC, FPGA or NIC
Stands for Programming Protocol-indepdendent Packet Processors.


See [here](https://cloudswit.ch/blogs/what-you-should-know-about-p4-programming-language-p4-switch/)

# Memory

## Solid state drives, SSD

See [here](https://www.digitaltrends.com/computing/best-nvme-ssd/#h-EU822w49gE)
and [here](https://www.pcworld.com/article/394939/cant-buy-a-gpu-3-alternative-upgrades-to-make-your-gaming-pc-kick-butt.html)



## AMD Secure Memeory Encryption

See [here](https://www.kernel.org/doc/html/next/x86/amd-memory-encryption.html)

White paper [here](https://www.amd.com/content/dam/amd/en/documents/epyc-business-docs/white-papers/memory-encryption-white-paper.pdf)


# Optical Computing

Interesting [paper on ACCEL](https://www.nature.com/articles/s41586-023-06558-8#Sec9) experiment and claimed massive energy improvement over A100 as well as 10x speed up.

Not sure I've understood how the adaptive learing aka back propagation works though?

