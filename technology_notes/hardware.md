# Hardware notes

A somewhat random collection of information.

## Size prefixes

| Prefix | Abbrv | Order of Mag |
|:-----|--------:|----------:|
|Giga |G| 10**9 |
|Tera |T| 10**12|
|Peta |P| 10**15|
|Exa  |E| 10**18|
|Zetta|Z| 10**21|
|Yotta|Y| 10**24|

## Basic Physics and Power

Rough guide:

* CPU uses 65-150 watts
* GPU uses 30-1000 watts
* RAM uses 2-3.5 watts
* Hard drives use 5-10 watts (depends on type)

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

A specialized NN unit called the Apple Neural Engine (ANE) that's faster and more efficient than CPU or GPU.

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

The main difference between these two is:

* ARM64 is a RISC - Reduced Instruction Set Computing architecture

* AMD64 is a CISC - Complex Instruction Set Computing architecture

## Software Defined Networks, SDN

See [here](https://sdn.systemsapproach.org/) and [paper](https://www.sigcomm.org/sites/default/files/ccr/papers/2014/April/0000000-0000012.pdf)

## P4 Programming Language and P4 Programmable Switch

A domain-specific programming language used to describe a programmable forwarding hardware processes: can be ASIC, FPGA or NIC
Stands for Programming Protocol-indepdendent Packet Processors.

See [here](https://cloudswit.ch/blogs/what-you-should-know-about-p4-programming-language-p4-switch/)

## Memory

### Solid state drives, SSD

See [here](https://www.digitaltrends.com/computing/best-nvme-ssd/#h-EU822w49gE)
and [here](https://www.pcworld.com/article/394939/cant-buy-a-gpu-3-alternative-upgrades-to-make-your-gaming-pc-kick-butt.html)

### AMD Secure Memeory Encryption

See [here](https://www.kernel.org/doc/html/next/x86/amd-memory-encryption.html)

White paper [here](https://www.amd.com/content/dam/amd/en/documents/epyc-business-docs/white-papers/memory-encryption-white-paper.pdf)

## Optical Computing

Interesting [paper on ACCEL](https://www.nature.com/articles/s41586-023-06558-8#Sec9) experiment and claimed massive energy improvement over A100 as well as 10x speed up.

Not sure I've understood how the adaptive learing aka back propagation works though?


## RISC-V

Pronounced 'risk-five'.

An open-source chip architecture.



This link explains US policy makers concerns around RISC-V [here](https://cset.georgetown.edu/article/risc-v-what-it-is-and-why-it-matters/) from CSET, Center for Security and Emerging Technology.
Key concern:

  * Chinese firms use RISC-V arch to avoid U.S. export controls
  * Allows China's chip design ecosystem to grow

They're looking to regulate this, but that could be counter-productive.

Document does explain what RISC-V is

### Context
At foundation of every processor's design is a technical specification known as an
instruction set architecture - ISA.
This describes how software will control the processor's hardware(? TODO look up this?)

Specialized AI chips, such as those designed by AMD and NVIDIA, **rely on an in-house ISA**.
For general computing, i.e. CPUs, rather than reinvent the wheel, chip design teams typically **licence an existing ISA** from Intel or Arm, e.g., for their respective CPU designs AMD licences from Intel and Apple from Arm. But increasingly, rather than licence, CPU design shops are considering a third ISA option: RISC-V

RISC-V is an open-source ISA managed by a Swiss standards development body (RISC-V International). Chip design teams can access and implement the RISC-V standard free of charge, avoiding costly licensing fees.
Companies (U.S. and Chinese) are taking advantage of RISC-V to design chips of varying complexity from simple microcontrollers to complex systems-on-a-chip.

Export controls targeting standards-setting activity for RISC-V are likely the only regulatory tools that have a chance to slow down China's development and adoption of the tech.

**Note**

  * RISC-V International: moved HQ from U.S. to Switzerland in March 2020 in part to insulate from creeping influence of geopolitics on chip industry.

#### References and papers

  * [Potential of RISC-V platform in Financial Computing on Option Pricing and Energy Efficiency](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10394561)
  * 