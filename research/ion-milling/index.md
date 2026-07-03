---
layout: post 
title: Ion Milling
advisor: Dr. Yashwanth Balaji
permalink: /research/ion-milling/
tags: ["Nanofabrication", "Python"]
author: Eric Du
date: 2026-06-26
---

## Overview

This project focuses on developing novel qubit fabrication techniques with the goal of increasing coherence
times. In quantum computing, the coherence time (also sometimes called the $T_1$ time), refers to the amount
of time a qubit can remain in its first excited state before inevitably returning to the ground state due to
interactions with the environment. To date, the primary loss mechanisms we are trying to minimize are
so-called two level system (TLS) losses, which are generally introduced by surface roughness, residues, and
other forms of "damage" that can naturally arise from the fabrication process.

To start, the central component in a quantum circuit is the
Josephson Junction (JJ), which can be thought of as a nonlinear inductor.[^nonlinearity] Physically, the
JJ is realized as two superconducting metal leads, with an insulating barrier in between. The idea is
essentially that when the metals become superconducting, Cooper pairs[^cooper-pair] from one metal are able to tunnel
through the barrier from one superconductor to the other, and we can control the rate of tunnelling which
then allows us to control the qubit transitioning between the $\ket{0}$ and $\ket{1}$ state. There's a lot of
extremely interesting physics I'm skipping here, but that's the basic idea. 

Another component central to a quantum processor are the capacitor pads that the JJs are connected to. The
capacitors, when combined with the inductive JJ element, form a LC resonator with a resonance frequency, and its
this resonance that allows us to drive the qubit with electric signals from voltage and current sources. For
this project, the capacitors are relevant because they are the component that we need to attach our JJ to in
order to make a proper circuit. 

In essence, here's the problem we are trying to solve: because JJs are on the order of hundreds of nanometers
thick, they cannot be patterned using photolithography -- these machines don't have the sub-micron level
precision required to make the junctions, and instead we need to rely on electron beam (e-beam) lithography.
Therefore, our lithography is separated into two steps: we first pattern large features like feedlines and
capacitor pads, then pattern the JJs in a separate e-beam lithography step. As a result of this two-step
process, a lossy oxide will grow on our capacitor pads, which we then need to remove in order to ensure an
ohmic contact between the capacitor and JJ pads.

Historically, the method to remove these oxides was using an ion mill, which uses ionized Argon (or some
other noble gas) to mechanically remove the oxide ensuring ohmic contact. However, this is non-ideal, since
the ion mill will also damage the silicon surface by increasing its surface roughness, which can be a source
of TLS loss. The goal of this project is to find alternative chemical processes that can be done to reduce
the ion milling step, thereby reducing the damage to the silicon and thus eliminating one source of TLS loss.

## Experimental Procedure

To investigate different chemical processes, we first fabricate an array of test structures on which we can
test different chemical procedures, and evaluate their efficacy in generating ohmic contact. For us, the
array looks as follows:

[INSERT IMAGE HERE]

Shaded in red are the large pads which we pattern using photolithography, and the regions in blue are the
regions where we use e-beam lithography. Therefore, the region where we have both red and blue are where we
are testing the ohmic contact, since these regions will have aluminum deposited from the photolithography
step, and then have an additional aluminum layer from the e-beam step. Embedded in this design is also a
reference channel where we deposit the entire structure in one deposition (in the photolithography step). 
  
Once both deposition steps are complete, we then use a probe station to measure the DC resistance through the
channel. The working principle is as follows: if an ohmic contact is achieved, then we should get a near-zero
resistance across all structures. However, if an oxide barrier (or some other species) forms, then it would
show up as some large resistance. Typically, our shorts usually measure anywhere from 10 to 20 ohms, whereas
oxides will generally result in mega-ohm scale resistances, so it's pretty easy to tell when an oxide is
forming.


  
 
    


 
 

[^nonlinearity]: The nonlinearity of the JJ is important for reasons pertaining to driving the qubit, which
    I won't go into detail here.

[^cooper-pair]: These are pairs of entangled electrons that give rise to the phenomenon of
    *superconductivity*, where current can be passed through a metal with zero resistance under the right
    conditions. The fundamental mechanism behind their creation is given by the Bardeen-Cooper-Schrieffer
    (BCS) theory, which deserves a deep dive on its own, so I won't go more into it here. What's important 
    for now is that it's a fundamentally quantum phenomenon, and is the central mechanism that defines a
    qubit.
