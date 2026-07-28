# Cools Sapphire Single-Optical-Domain Computing

## Beyond CPO: one optical domain from GPU–HBM package to data center

> **Co-Packaged Optics moves electrical-to-optical conversion closer to the chip.**  
> **Cools removes repeated conversion boundaries and builds one optical fabric across package, motherboard, backplane, rack and data center.**

[한국어](README_KR.md) · [中文](README_ZH.md)

---

## The strategic proposition

The next computing wall is not only transistor density. It is the hierarchy between compute, memory, power delivery, clock distribution and networking.

Today, data repeatedly crosses boundaries:

```text
GPU electrical I/O
→ package interconnect
→ SerDes
→ optical engine
→ fiber
→ switch
→ another optical engine
→ another SerDes
→ another GPU or memory
```

Each boundary adds conversion power, latency, area, alignment burden and packaging complexity.

Cools proposes a different architecture:

```text
Sapphire vertical optical package
→ free-space optical coupling
→ optical-mesh motherboard
→ optical backplane
→ optical rack
→ optical data-center fabric
```

> **The signal remains optical until it reaches the final receiving detector.**

This is not a faster optical module. It is a new computing hierarchy.

---

## The sapphire handler becomes the center of the system

A single-crystal sapphire handler can perform multiple functions at the same time:

- mechanical handler for advanced dual-side integration;
- broadband optical transmission medium;
- electrically insulating body for through-sapphire vias;
- alignment reference for opposite-face optical arrays;
- substrate for GaN-family epitaxial light sources;
- power-delivery platform;
- heat-spreading and dual-side thermal-separation structure; and
- optical-emission interface to the motherboard.

> **Do not treat sapphire as a temporary growth substrate. Turn it into the optical, electrical and mechanical backbone of the package.**

---

# 1. Vertical GPU–HBM optical package

Conventional GPU–HBM integration places the GPU and HBM stacks side by side on an interposer. The longest links remain millimeters to centimeters long and compete for routing area.

Cools places the GPU and HBM on opposite faces of the sapphire handler.

```text
GPU / AI accelerator
↓ through-thickness optical channels
single-crystal sapphire handler
↓
HBM base die / HBM stack
```

The sapphire thickness—representatively hundreds of micrometers—becomes the high-speed data path.

- high-speed data: vertical optical channels through sapphire;
- power and low-speed control: Through-Sapphire Vias (TSaVs);
- optical and electrical regions: spatially separated;
- GPU heat and HBM heat: removed from opposite sides;
- optical path: reduced from lateral millimeter scale to through-thickness micrometer scale.

> **The memory wall is attacked by changing the direction of the interconnect.**

---

# 2. Keep the GaN light source on the sapphire

Conventional micro-LED manufacturing grows GaN-family emitters on sapphire, then removes or transfers them to another substrate.

Cools keeps the sapphire and turns the original epitaxial substrate into the package itself.

```text
GaN / InGaN micro-LED array
↓ epitaxially integrated on sapphire
sapphire optical medium
↓ one-to-one through-thickness channels
photodetector array
```

The same sapphire body provides:

- GaN epitaxial growth surface;
- optical transmission medium;
- front-to-back alignment reference;
- mechanical support for the detector array; and
- electrical insulation for liner-free TSaVs.

This removes or reduces dependence on:

- laser lift-off;
- micro-transfer of thousands of emitters;
- separate optical waveguide chips;
- separate optical alignment frames; and
- additional interposer structures.

> **Grow the light source on sapphire—and never throw away the most valuable part of the optical package.**

---

# 3. Backside wide-bandgap IVR

AI accelerators operate at low core voltage and extremely high current. A motherboard-side Voltage Regulator Module (VRM) forces that current through a long Power Distribution Network (PDN).

Cools bonds a GaN- or SiC-based Integrated Voltage Regulator (IVR) to the opposite face of the sapphire handler.

```text
AI accelerator core
↑ hundreds-of-micrometers power path through TSaVs
sapphire handler
↑
backside GaN / SiC IVR
```

The architecture targets:

- shorter IVR-to-core power path;
- lower IR drop;
- lower dynamic voltage droop;
- lower path inductance;
- higher-frequency WBG switching;
- smaller integrated inductors and capacitors;
- separation of AI-die heat and IVR heat; and
- dual-side cooling.

> **Data travels optically through sapphire. Power travels vertically through insulated sapphire vias. Heat exits from both sides.**

---

# 4. One optical domain from module to motherboard

Each sapphire module presents an optical-emission face toward an optical-mesh motherboard.

A controlled free-space gap couples the module to the motherboard without a soldered optical interface.

```text
module optical waveguide
→ grating / microlens
→ free-space gap
→ motherboard grating
→ motherboard optical waveguide matrix
```

The free-space gap can simultaneously provide:

- optical coupling;
- compliance for coefficient-of-thermal-expansion mismatch;
- tolerance to motherboard warpage;
- vibration and stress isolation;
- module removal and replacement; and
- freedom from optical BGA solder-joint statistics.

The optical path remains continuous from the transmitting modulator to the final receiving photodetector.

> **The package boundary no longer has to be an optical-electrical conversion boundary.**

---

# 5. Optical-mesh motherboard

The motherboard contains an optical waveguide matrix and wavelength- or wavelength-space-routed communication fabric.

Instead of building a dedicated physical waveguide for every module pair, the architecture can combine:

- bus waveguides;
- Dense Wavelength Division Multiplexing (DWDM);
- wavelength-selective add/drop elements;
- spatial channels; and
- module-group routing labels.

This provides logical all-to-all connectivity without requiring a full physical N(N−1)/2 waveguide mesh.

The optical signal plane and the electrical power plane remain physically separated.

---

# 6. The network changes with the workload

A fixed topology forces every workload to use the same communication structure.

Cools uses optical switches so that the topology can be reconfigured at runtime.

Representative switch technologies include:

- microring resonators;
- Mach–Zehnder Interferometers (MZIs);
- Micro-Electro-Mechanical Systems (MEMS) mirrors; and
- Phase-Change Material (PCM) cells.

Representative topology mapping:

| Workload pattern | Optical topology direction |
|---|---|
| AllReduce / AllGather | Ring |
| Attention / All-to-All | Mesh or custom fabric |
| Pipeline parallelism | Chain |
| Broadcast / aggregation | Tree |
| Multi-tenant operation | Independently isolated optical groups |

> **The workload no longer adapts to a fixed network. The optical network adapts to the workload.**

---

# 7. One global optical memory pool

Each module’s HBM can be mapped into a hardware global address space.

A module can issue optical:

- READ;
- WRITE; and
- ATOMIC

transactions to another module’s HBM through the optical mesh.

The platform includes concepts for:

- module-ID-based address translation;
- wavelength and spatial routing labels;
- optical memory packet formats;
- strong, release-acquire or weak consistency;
- remote atomic operations;
- hardware isolation between tenants or jobs; and
- dynamic routing-table updates after topology changes.

> **Do not move data between isolated GPU memories. Turn every HBM stack into one addressable optical memory pool.**

---

# 8. One optical fabric for data, memory and time

The same optical mesh can distribute femtosecond- to picosecond-scale clock pulses from a master source to every module.

The architecture includes:

- optical clock distribution over the shared mesh;
- wavelength, separate-waveguide or time-division coexistence with data;
- module-specific optical delay compensation;
- local photodetection and Phase-Locked Loop (PLL) clock derivation; and
- common timing for GPU, HBM and I/O domains.

> **One optical fabric carries data, memory transactions and the time reference that synchronizes them.**

---

# 9. Scale beyond the motherboard

The single-optical-domain architecture extends through:

```text
sapphire module
→ optical-mesh motherboard
→ optical backplane
→ optical rack
→ optical data-center topology
```

The portfolio includes:

- motherboard-to-backplane free-space or optical-connector coupling;
- rack optical patch panels and Optical Circuit Switches (OCSs);
- optical amplification using EDFA, SOA or Raman approaches;
- spine-leaf, fat-tree and dragonfly optical topologies;
- hierarchical optical routing labels; and
- extension of dynamic topology, optical clocking and unified memory across system hierarchy.

> **CPO ends at the package edge. Cools extends the optical domain through the data center.**

---

## The full architecture

```text
MONOLITHIC LIGHT
GaN / InGaN micro-LED arrays grown directly on sapphire

VERTICAL PACKAGE
GPU ↕ optical sapphire channels ↕ HBM

VERTICAL POWER
backside WBG IVR ↕ TSaVs ↕ AI core

MODULE COUPLING
sapphire optical face ↕ free-space gap ↕ motherboard

OPTICAL FABRIC
wavelength-routed and dynamically switched optical mesh

GLOBAL MEMORY
all HBM mapped into a unified addressable pool

GLOBAL TIME
femtosecond optical clock distributed across the same fabric

SYSTEM SCALE
motherboard → backplane → rack → data center
```

---

## What this architecture is intended to replace or absorb

| Conventional dependency | Cools direction |
|---|---|
| Long lateral GPU–HBM electrical wiring | Through-thickness optical GPU–HBM links |
| Separate optical chiplets | Sapphire-integrated light and detector arrays |
| Repeated O/E and E/O boundaries | Continuous optical domain |
| Motherboard-side low-voltage VRM path | Backside WBG IVR through TSaVs |
| Fixed electrical topology | Runtime-reconfigurable optical topology |
| Isolated HBM address spaces | Unified optical memory pool |
| Multi-stage electrical clock trees | Shared optical clock distribution |
| Soldered module-to-board data links | Reworkable free-space optical coupling |
| Package-limited CPO | Motherboard-, rack- and data-center-scale optical fabric |

---

## Adoption message

> **Do not invest the next computing generation in adding more conversion engines to the same hierarchy.**  
> **Collapse the hierarchy into one optical domain.**

Cools is seeking discussions with:

- AI accelerator and GPU companies;
- HBM and memory manufacturers;
- foundries and advanced-packaging companies;
- optical-interconnect and photonics companies;
- motherboard, backplane and data-center system companies;
- GaN, SiC and sapphire ecosystem partners; and
- strategic investors.

---

## Patent protection and transaction options

The technologies and architectures described in this repository are protected by pending patent applications and associated proprietary know-how of Cools Inc.

The portfolio includes patent-pending concepts covering:

- dual-side sapphire GPU–HBM vertical optical packaging;
- sapphire-backside wide-bandgap IVR integration;
- monolithic GaN micro-LED and photodetector arrays;
- single-optical-domain module-to-motherboard coupling;
- optical-mesh motherboards;
- runtime optical-topology reconfiguration;
- unified optical memory pools;
- femtosecond optical clock distribution; and
- backplane-, rack- and data-center-scale expansion.

Potential transaction structures may include:

- exclusive or non-exclusive patent licensing;
- field-, product-, node- or territory-limited rights;
- joint architecture and process development;
- package, board and data-center integration programs;
- equipment and manufacturing collaboration;
- strategic investment or technology-business transfer; and
- where commercially appropriate, assignment or transfer of the relevant patent applications and patent rights themselves.

**Negotiations are not limited to a licence. Where the strategic objective and transaction conditions are appropriate, the relevant patent portfolio itself may be included in the transaction.**

Publication of this repository does not constitute a licence, waiver or permission to practise the disclosed technology. Detailed stack structures, optical budgets, channel geometries, process flows, control protocols and claim charts are reserved for controlled technical and legal discussions.

---

## Related Cools platforms

- [Cools CPO Zero-Thermal-Budget Bonding](https://github.com/jhcho9494/Cools_CPO_Zero_Thermal_Budget_Bonding)
- [Cools Hydrogen Reservoir Bonding](https://github.com/jhcho9494/Cools_Hydrogen_Reservoir_Bonding)
- [Cools HBM Thermal Clutch](https://github.com/jhcho9494/Cools_HBM_Thermal_Clutch)
- [Cools CoWoP Realization Patent](https://github.com/jhcho9494/NVIDIA-CoWoP-Realization-Patent)

---

## Contact

**Cools Inc.**  
Jinhyun Cho  
Former Samsung Electronics Master-level semiconductor engineer  
Ph.D., Mechanical Engineering, University of Michigan

Email: jhcho@cools.co.kr  
Email: jhcho9494@naver.com  
Mobile: +82-10-2280-9414
