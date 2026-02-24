---
title: "Maritime DDR Sensor — Material-Discriminating LiDAR for Search and Rescue"
date: 2026-01-01
draft: false
client: "Novel Systems Engineering (internal R&D)"
summary: "Designed a polarization-based LiDAR sensor architecture that automatically distinguishes life-saving equipment from ocean debris during maritime search and rescue operations, achieving >30 dB discrimination at projected production costs of $600–800 per unit — a 75–300x reduction versus conventional systems. Patent pending."
tags: ["optical systems", "LiDAR", "silicon photonics", "maritime SAR", "SBIR", "patent pending"]
outcomes:
  - "Novel dual orthogonal 1D phased array architecture achieving 128x reduction in phase shifter count (65,536 → 512)"
  - "Manufacturing yield transformed from 10–30% to 93–98% through dimensional decomposition"
  - "Projected production unit cost of $600–800 versus $50,000–200,000 for conventional systems"
  - ">30 dB signal-to-background discrimination between water and synthetic materials at 1550 nm"
  - "Provisional patent application filed (2026, patent pending)"
  - "SBIR Phase I proposal submitted to U.S. Coast Guard for bench-scale proof-of-concept validation"
  - "White paper published with peer-reviewed architecture and complete link budget analysis"
---

## The Problem

The critical bottleneck in maritime search and rescue is not response time — it is target detection time. The interval between arriving on scene and positively identifying survivors amid ocean debris, wave clutter, and natural materials determines whether people live or die.

Current sensor technologies each fail in specific ways that matter. Electro-optical cameras achieve sub-meter resolution but require visible light and clear weather — precisely the conditions absent during the maritime emergencies that generate most SAR operations. Thermal infrared sensors provide all-weather detection but cannot discriminate material composition: life jackets and marine debris have similar thermal signatures, forcing operators to manually classify every detected object. Maritime radar excels at long-range vessel detection but suffers from sea clutter and poor resolution for sub-meter targets, making person-in-water detection unreliable in rough seas.

No commercially available sensor affordable to volunteer SAR organizations currently provides automated material classification — the ability to tell a life jacket from a piece of driftwood without a human looking at it. Operators must visually examine every detected object, compressing search area coverage and increasing the probability that survivors are overlooked or reached too late.

Existing polarization-based LiDAR systems can perform material discrimination, but they employ 2D phased arrays with catastrophic manufacturing yields (10–30%), forcing costs to $50,000–200,000 per unit. This price barrier limits deployment to well-funded government agencies, leaving coastal communities, volunteer organizations, and commercial maritime operators without access to life-saving sensor technology.

## The Innovation: Differential Depolarization Response

The DDR sensor exploits a fundamental physical property: water and manufactured materials interact with polarized light in measurably different ways.

Water exhibits symmetric molecular-scale scattering that responds identically to orthogonally polarized illumination — its differential depolarization response (DDR) is near zero (typically < 0.05), consistent across sea states including whitecaps and foam. Manufactured materials — synthetic foams, fabrics, fiberglass — exhibit polarization-dependent scattering asymmetry through surface reflection and internal structure, producing DDR signatures of 0.15–0.25. The result is >30 dB signal-to-background discrimination: life-saving equipment and persons in water stand out against the ocean surface with statistical reliability sufficient for automated classification.

The sensor transmits simultaneous orthogonal polarization states at 1550 nm using dual wavelengths. Each channel independently measures returned power in both parallel and perpendicular polarization states, yielding four measurements per scan point. The differential response DDR = |DR_H − DR_V| captures material composition directly — volume scatterers like water produce near-zero DDR regardless of sea state, while surface scatterers produce consistent asymmetry enabling automated classification.

FMCW (frequency-modulated continuous wave) coherent detection provides simultaneous range and velocity measurement through heterodyne mixing. For maritime applications, this enables drift pattern analysis — life jackets drift differently than life rafts, which drift differently than vessel debris. Direct velocity measurement from single observation epochs supports current mapping and survivor location prediction, optimizing search patterns to intercept drifting survivors.

## The Manufacturing Breakthrough: Dual 1D Architecture

The core innovation — and the subject of the provisional patent application — is a dual orthogonal 1D silicon photonic phased array architecture that solves the manufacturing problem that has kept material-discriminating LiDAR prohibitively expensive.

Conventional 2D phased arrays require 65,536 phase shifters with stringent tolerances: waveguide width matching to ±10 nm, coupling efficiency >80%, and optical path length matching to λ/10 precision (155 nm at 1550 nm wavelength). Manufacturing yield follows multiplicative probability — at realistic single-device yields, these arrays produce catastrophic 10–30% system yields, requiring multi-wafer selection to produce a single functional sensor.

The dual 1D architecture decomposes 2D beam steering into independent azimuth and elevation scans implemented as physically separate silicon photonic dies, each containing an identical 256-element linear array (512 total elements). This 128x reduction in phase shifter count transforms the economics:

- **Die area reduction:** Each linear array occupies 0.05 cm² versus 1.0 cm² for a 2D array — a 20x reduction that dramatically improves Poisson defect yield
- **Wafer-level yield:** 98.5% per die at typical foundry defect densities, versus 74% for monolithic 2D
- **Assembly flexibility:** Any functional azimuth die pairs with any functional elevation die — failed dies do not render partners unusable
- **System yield:** 93–98% including packaging, versus 10–30% for conventional 2D arrays

A single DFB laser feeds an integrated 3 dB splitter, with one path maintaining original wavelength and the other passing through a carrier-suppressed SSB modulator generating a 50 GHz frequency shift. Both wavelengths originate from the same optical cavity, creating inherent coherence that tracks thermal drift while reducing component count. The 50 GHz separation (500x the signal bandwidth) enables complete wavelength isolation for simultaneous dual-point scanning.

At production volumes of 10,000+ units, sensor assembly costs reach $600–800 — a 75–300x reduction versus conventional systems. At higher volumes (100,000+ units) with photonic integration and ASIC-based processing, costs could approach $300–500 per sensor.

## Target Applications

**Coast Guard and Military SAR:** The U.S. Coast Guard operates 243 commissioned cutters and approximately 1,700 boats across 190+ stations. At $800 per unit, DDR sensors represent a negligible line item relative to platform acquisition costs. The Coast Guard Auxiliary adds 5,000 registered vessels operated by 30,000 volunteers who currently lack any automated material discrimination capability.

**Commercial Shipping — Man Overboard Detection:** Man overboard incidents among cargo vessels carry approximately 30% fatality rates, with crew recovery windows as short as 4 minutes in cold water. Hull-mounted DDR arrays function as continuous automated watch systems, eliminating dependence on crew visual detection during inclement weather or nighttime operations. The global merchant fleet of 50,000+ vessels represents a substantial addressable market at sub-$1,000 sensor costs.

**Coastal Monitoring and Swimmer Safety:** Fixed-installation DDR scanning for port authorities, bridge operators, and coastal monitoring agencies. Organizations protecting swimmers at recreational beaches can afford sensor coverage that was previously limited to military and federal applications.

**Autonomous Maritime Systems:** The sensor architecture is compatible with vessel-mounted, fixed-installation, and unmanned surface vehicle deployment, supporting the Coast Guard's investment in autonomous maritime systems for SAR grid-search operations.

## Development Status

**Current Phase — SBIR Phase I (Submitted):** A Phase I proposal has been submitted to the U.S. Coast Guard for a bench-scale proof-of-concept demonstrating DDR material discrimination at >13 dB SNR across nine target material classes relevant to maritime SAR. The proposed six-month effort delivers a man-portable field validation instrument with coaxial transmit/receive architecture, four-channel InGaAs detection, and integrated Raspberry Pi 5 processing with touchscreen display. Field validation at an Oregon coastal location under active wave conditions is included in the scope.

**Phase II Path:** Phase I results directly enable development of a scanning DDR sensor implementing the full dual 1D phased array architecture at 256x256 spatial resolution and approximately 10 Hz frame rate. Manufacturing partnerships have been identified with Voyant Photonics (silicon photonic phased array fabrication) and Teledyne FLIR (ruggedized maritime sensor production and existing Coast Guard procurement relationships).

**Intellectual Property:** Provisional patent application filed 2026 covering the dual orthogonal 1D architecture. All development was performed independently and exclusively from published literature, with no incorporation of proprietary information from current or former employers.

## What This Demonstrates

This project illustrates Novel Systems Engineering's ability to identify a fundamental engineering bottleneck — in this case, the manufacturing yield crisis that has kept material-discriminating LiDAR prohibitively expensive — and design an architecture that resolves it. The work required integration across semiconductor device physics, silicon photonics, optical system design, coherent detection theory, and maritime operational requirements. The provisional patent, white paper, and SBIR submission represent the translation of that analysis into intellectual property and a funded development pathway.
