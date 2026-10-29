# NixOS-on-RISC-V
NixOS on RISC-V for future apples-to-apples performance comparisons against ARM and x86.
# NixOS on RISC-V: Toward Apples-to-Apples Benchmarks

NixOS offers a practical way to create equivalent runtimes for gauging performance of both software and hardware—specifically RISC-V versus ARM versus x86.

Most published benchmarks are basically marketing. They don’t give you a clean way to see how software actually performs. The goal here is something closer to an apples-to-apples setup so performance can be compared at a basic level without a bunch of uncontrolled differences getting in the way.

Nix helps solve that testing problem. You can define the system once and get the same packages, same versions, and same configuration every time. When you’re trying to measure something like Kubernetes or a service mesh on different hardware, that consistency matters. Otherwise it’s hard to tell whether a difference comes from the CPU or just from how the software was built and installed.

For RISC-V specifically, the same idea applies. With a proper NixOS image on the hardware, the same workloads can be run on RISC-V, ARM, and x86 and compared more fairly. Nix doesn’t make the silicon faster, but it removes a lot of the noise so the numbers are more trustworthy.

## Current status

We got a native Nix build and a Kubernetes node running on a RISC-V board (year-old RVA21 system from DeepComputing). That shows the Nix package set (nixpkgs) and the tools needed to build a NixOS system can work on the hardware.

What we did **not** have yet:
- Finished benchmark results
- Full pods running
- Complete, ready-to-use NixOS images for side-by-side testing

The side-by-side performance numbers (RISC-V vs ARM vs x86) still have to be run. Screenshots of the progress were shown during the NixCon 2026 talk but were hard to read on the big screen.

## Why RISC-V

RISC-V is open and freely available. No government or company can simply charge you for the RISC-V instruction set or prevent you from implementing it. Anyone who wants to build a CPU can do so, provided they understand the architecture and comply with the applicable requirements.

It reduces the instruction set to the essentials (with optional extensions). It originated at Berkeley in the same academic tradition as earlier reduced-instruction-set work.

## Next steps

- Produce proper NixOS images for the hardware
- Deploy real workloads / pods
- Run controlled benchmarks (CPU, memory, service-mesh overhead, etc.) against comparable ARM and x86 systems
- Make the results and configurations public

Once those pieces are in place, this repo will hold the Nix expressions, hardware notes, and benchmark data for reproducible comparisons.

## Talk

This work was discussed in the NixCon 2026 talk “Declarative Frontiers: Running Kubernetes on RISC-V with NixOS” (Bruce Gain / ReveCom and Yuning Liang / DeepComputing). The talk covered the motivation and early progress; the finished comparisons are still ahead.
