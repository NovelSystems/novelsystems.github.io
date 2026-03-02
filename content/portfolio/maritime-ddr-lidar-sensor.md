---
title: "DDR Sensor — Material-Discriminating LiDAR for Maritime SAR and Radar Augmentation"
date: 2026-01-01
draft: false
client: "Novel Systems Engineering (internal R&D)"
summary: "Invented a polarization-based LiDAR architecture that classifies objects by material composition — distinguishing survival equipment and persons in water from ocean background, or carbon-fiber drones from birds — by exploiting water and atmosphere as near-zero depolarization backgrounds. A dual orthogonal 1D silicon photonic phased array achieves 128x phase shifter reduction, transforming physical defect yield from 74% to 98.5% and bringing sensor costs from $50,000–200,000 down to $600–800. Two provisional patents filed covering the core DDR architecture, adaptive environmental calibration, shared-aperture autonomous target acquisition, and distributed perimeter sensor networks; SBIR Phase I submitted to U.S. Coast Guard."
tags: ["optical systems", "LiDAR", "silicon photonics", "maritime SAR", "radar augmentation", "drone detection", "SBIR", "patent pending"]
outcomes:
  - "Dual orthogonal 1D phased array architecture achieving 128x reduction in phase shifter count (65,536 → 512)"
  - "Physical defect yield transformed from 74% to 98.5% through dimensional decomposition"
  - "Projected production unit cost of $600–800 versus $50,000–200,000 for conventional systems"
  - "~20:1 predicted DDR contrast ratio between synthetic materials and ocean surface background at 1550 nm"
  - "Two provisional patent applications filed (U.S. Provisional No. 63/984,145, Feb 2026; supplemental provisional covering additional DDR core embodiments, adaptive environmental calibration, shared-aperture autonomous target acquisition, and perimeter sensor network architectures)"
  - "SBIR Phase I proposal submitted to U.S. Coast Guard for bench-scale proof-of-concept validation"
  - "Peer-reviewed white paper published with complete architecture, link budget analysis, and application to both FMCW maritime and pulsed ToF radar augmentation modalities"
---

## The Problem

The critical bottleneck in maritime search and rescue is not response time — it is target detection time. The interval between arriving on scene and positively identifying survivors amid ocean debris, wave clutter, and natural materials determines whether people live or die. In Pacific Northwest waters (~10°C), hypothermia onset creates survival windows measured in minutes to hours, not days.

Current sensor technologies each fail in specific ways that matter. Electro-optical cameras achieve sub-meter resolution but require visible light and clear weather — precisely the conditions absent during the maritime emergencies that generate most SAR operations. Thermal infrared sensors provide all-weather detection but cannot discriminate material composition: life jackets and marine debris have similar thermal signatures, forcing operators to manually classify every detected object. Maritime radar excels at long-range vessel detection but suffers from sea clutter and poor resolution for sub-meter targets, making person-in-water detection unreliable in rough seas.

A parallel problem exists in airspace security: airport perimeter surveillance radar detects and tracks airborne contacts but cannot classify material composition. A carbon fiber drone and a seagull return similar radar cross-sections at short range, requiring human review of every contact.

No commercially available sensor affordable to volunteer SAR organizations or most airport operators currently provides automated material classification. Existing polarization-based LiDAR systems can perform material discrimination, but they employ 2D phased arrays with catastrophic manufacturing yields (10–30%), forcing costs to $50,000–200,000 per unit.

## The Innovation: Differential Depolarization Response

The DDR sensor exploits a fundamental physical property: water and manufactured materials interact with polarized light in measurably different ways. The same principle applies to atmosphere and airborne objects.

Water exhibits symmetric molecular-scale scattering that responds identically to orthogonally polarized illumination — its differential depolarization response (DDR) is near zero (typically < 0.05), consistent across sea states including whitecaps and foam. Manufactured materials — synthetic foams, fabrics, fiberglass, carbon fiber composites — exhibit polarization-dependent scattering asymmetry through surface reflection and internal structure, producing DDR signatures of 0.15–0.25. The result is an approximately 20:1 predicted DDR contrast ratio: life-saving equipment and persons in water stand out against the ocean surface with statistical reliability sufficient for automated classification.

Clear atmosphere provides an equally clean background (DDR ≈ 0 to 0.03), enabling the same measurement physics to classify airborne targets — composite drone hulls versus biological returns — against sky.

The sensor transmits simultaneous orthogonal polarization states at 1550 nm using dual wavelengths. Each channel independently measures returned power in both parallel and perpendicular polarization states, yielding four measurements per scan point. The differential response DDR = |DR_H − DR_V| captures material composition directly — volume scatterers like water produce near-zero DDR regardless of sea state, while surface scatterers produce consistent asymmetry enabling automated classification. The four-channel architecture is the minimum sufficient for this discrimination, enabling the receiver without the eight or more channels required for full Mueller matrix reconstruction.

DDR measurement is inherently robust to unpolarized ambient light: solar background contributes equally to both polarization channels and cancels in the DDR computation, making the sensor operational in full daylight without optical filtering.

## The Manufacturing Breakthrough: Dual 1D Architecture

The core manufacturing innovation — and the subject of the first provisional patent application — is a dual orthogonal 1D silicon photonic phased array architecture that solves the manufacturing problem that has kept material-discriminating LiDAR prohibitively expensive.

Conventional 2D phased arrays require 65,536 phase shifters with stringent tolerances: waveguide width matching to ±10 nm, coupling efficiency >80%, and optical path length matching to λ/10 precision (155 nm at 1550 nm wavelength). Physical defect yield follows Y = exp(−D₀ × A), giving approximately 74% for the ~1 cm² 2D die — roughly one in four fails before functional testing. Downstream process variation and thermal gradient losses drive realized system yields to 10–30%.

The dual 1D architecture decomposes 2D beam steering into independent azimuth and elevation scans implemented as physically separate silicon photonic dies, each containing an identical 256-element linear array (512 total elements). This 128x reduction in phase shifter count transforms the economics:

- **Die area reduction:** Each linear array occupies 0.05 cm² versus 1.0 cm² for a 2D array — a 20x reduction that raises physical defect yield from 74% to 98.5%
- **Wafer throughput:** 20x more dies per wafer run before yield is applied, an independent multiplier on cost
- **Assembly flexibility:** Any functional azimuth die pairs with any functional elevation die — failed dies do not render partners unusable
- **System yield:** 93–98% including packaging, versus 10–30% for conventional 2D arrays

A single DFB laser feeds an integrated 3 dB splitter, with one path maintaining original wavelength and the other passing through a carrier-suppressed SSB modulator generating a 50 GHz frequency shift. Both wavelengths originate from the same optical cavity, eliminating the thermal drift sensitivity of dual-laser architectures — a 0.5°C differential thermal transient between independent lasers shifts relative frequency by ~6 GHz, enough to elevate inter-channel crosstalk from <0.1% to 5–10% and produce DDR systematic errors comparable to the water baseline the classification depends on. The single-laser design maintains frequency stability to ~1 ppm (50 kHz uncertainty), keeping the complete wavelength-channel crosstalk error budget at ≤0.005.

At production volumes of 10,000+ units, sensor assembly costs reach $600–800 — a 75–300x reduction versus conventional systems. At higher volumes (100,000+ units) with photonic integration and ASIC-based processing, costs could approach $300–500 per sensor.

## Adaptive Environmental Calibration

Operational DDR classification depends on a stable baseline — the sensor must know what "zero" looks like before it can reliably flag deviations. The supplemental provisional discloses a complete calibration system that uses the deployment environment itself as a continuous reference, exploiting the physics that symmetric scattering media (ocean surface water, clear atmosphere) produce DDR values near zero by Mie and Rayleigh scattering theory.

Three calibration modes operate across different operational contexts. Periodic automatic calibration acquires DDR measurements from spatially separated positions at set intervals, validates them through a spatial consistency check and quorum agreement, and updates the baseline using an exponentially weighted moving average with rate clamping to reject transient contamination. Continuous opportunistic calibration evaluates every scan point as a potential calibration candidate during normal operation — measurements near the current baseline and spatially distributed across the field of regard contribute to a running calibration pool without interrupting classification. Manual calibration covers startup initialization and operator-commanded resets.

Both automated modes apply a two-stage validation before permitting a baseline update: a spatial consistency evaluation (localized contamination from debris, oil, or biological matter creates spatial heterogeneity and is rejected) and a quorum agreement check (requiring a majority of measurements to fall within the acceptance range, catching spatially uniform contamination such as algal blooms). These checks are architecturally distinct from Constant False Alarm Rate (CFAR) adaptive thresholding — CFAR estimates an unknown background level from reference cells, while DDR calibration validates against a physics-derived prediction that symmetric scatterers should produce DDR near zero.

The calibration system includes fault detection and predictive maintenance: a running baseline that drifts beyond warning and critical thresholds triggers tiered alerts indicating possible polarization state degradation, detector drift, or optical contamination. Trend analysis projects time-to-fault, enabling scheduled maintenance before classification reliability degrades.

## Application: Maritime Search and Rescue

Maritime SAR outcomes are time-constrained in a way that makes automated classification operationally decisive rather than merely convenient. Water's near-zero DDR background produces an approximately 20:1 predicted contrast ratio against persons in water, survival equipment, and vessel debris, enabling automated flagging of high-priority contacts so operators investigate confirmed targets rather than visually examining every return.

FMCW (frequency-modulated continuous wave) coherent detection provides simultaneous range and velocity measurement through heterodyne mixing. Life jackets, life rafts, and vessel debris exhibit distinct drift behavior under identical current and wind conditions. Direct velocity measurement from single observation epochs supports current mapping and survivor location prediction, shifting search patterns from area coverage to intercept.

The second provisional patent extends the maritime application with a **perimeter sensor network** architecture: multiple DDR sensor nodes with non-parallel optical axes, connected to a centralized network processor that resolves two-dimensional velocity vectors from per-node radial Doppler measurements. This enables drift-predictive focused-scan handoff — as a target drifts across zone boundaries, adjacent nodes concentrate scan resources on the predicted arrival position, maintaining target persistence without requiring a new classification event. Hull-mounted networks with 2–5 meter node spacing provide angular separations exceeding 30° for near-hull targets, enabling well-conditioned velocity resolution for man overboard detection. Shore installations with 5–20 meter spacing cover harbor approaches at 10–100 meter range.

The network architecture includes confidence-weighted multi-node classification (requiring coincident DDR exceedance from at least two nodes to declare an event), node health monitoring via network DDR consensus, and zero-velocity graceful degradation for stationary or unconscious persons in water.

Salt-spray contamination is mitigated by routing electronics waste heat (25–35W) through a duct across the aperture face, maintaining surface temperature above the local dew point without consumable cleaning materials.

## Application: Radar Augmentation for Drone/Bird Discrimination

The DDR measurement architecture applies equally to airborne target classification. Airport perimeter surveillance radar detects and tracks contacts but cannot determine material composition. The DDR sensor integrates as a secondary classification layer on top of existing radar track output, consuming bearing and range data via NMEA 0183/2000 interfaces and returning a material confidence score on each cued contact — without modifying radar hardware or operator workflow.

Clear atmosphere at 1550 nm provides a lower and more stable DDR background than ocean surface water (DDR ≈ 0 to 0.03), and rain/fog attenuation at perimeter ranges of 200–500 m is less than 0.05 dB, preserving classification accuracy under adverse weather.

The fixed-infrastructure application uses a **pulsed time-of-flight** ranging modality in place of FMCW coherent detection, eliminating the frequency chirp electronics while retaining the dual-polarization four-channel DDR receiver. The underlying patent covers the DDR measurement architecture independent of ranging implementation. High pulse repetition frequency enables rapid sequential classification of a dense contact queue.

A **shared-aperture acquisition** architecture (covered by the supplemental provisional patent) resolves the radar position uncertainty mismatch: a non-polarizing beamsplitter routes returned optical energy to both a SWIR focal plane array for beam-axis centroiding and the DDR receiver for classification. A Galilean beam expander with self-locking worm-gear drive provides two divergence states — a wide acquisition footprint (~2.8 m diameter at 100 m range) for initial target capture, and a narrow classification footprint after closed-loop pointing converges. The net classification signal improvement from beam narrowing exceeds the signal reduction from the beamsplitter tap.

The system includes **anti-spoofing** through DDR variance monitoring: biological coatings applied to drone surfaces undergo rapid evaporative drying in airflow during flight, transitioning DDR values from the biological range toward the underlying composite substrate within approximately 60 seconds. Confidence scoring based on DDR variance over consecutive measurement epochs distinguishes stable biological signatures from decaying coating signatures.

Acoustic, RF, and kinematic detection answer whether something is present; DDR adds *what it is made of*, making it additive to every existing detection system rather than competitive with any.

## Target Markets

**Coast Guard and Military SAR:** The U.S. Coast Guard operates 243 commissioned cutters and approximately 1,700 boats across 190+ stations. At $800 per unit, DDR sensors represent a negligible line item relative to platform acquisition costs. The Coast Guard Auxiliary adds 5,000 registered vessels operated by 30,000 volunteers who currently lack any automated material discrimination capability.

**Commercial Shipping — Man Overboard Detection:** Man overboard incidents among cargo vessels carry approximately 30% fatality rates, with crew recovery windows as short as 4 minutes in cold water. Hull-mounted DDR perimeter networks function as continuous automated watch systems, providing material classification, 2D drift prediction, and persistent tracking across zone boundaries. The global merchant fleet of 50,000+ vessels represents a substantial addressable market at sub-$1,000 sensor costs.

**Airport Perimeter and Critical Infrastructure Security:** DDR radar augmentation adds material classification capability to installed radar infrastructure at airport perimeters, port authorities, harbors, and critical infrastructure sites — all operators with existing radar systems that DDR supplements without replacement. The pulsed ToF modality and shared-aperture acquisition architecture are specifically optimized for these fixed-installation cued-classification deployments.

**Autonomous Maritime Systems:** The sensor architecture is compatible with vessel-mounted, fixed-installation, and unmanned surface vehicle deployment, supporting autonomous SAR grid-search and autonomous vessel navigation where material classification provides information complementary to geometric and kinematic sensing.

## Intellectual Property and Development Status

**Patent Portfolio:** Two provisional patent applications filed in February 2026. The first provisional (U.S. No. 63/984,145, filed February 16, 2026) covers the dual orthogonal 1D architecture, DDR measurement principle, single-laser coherent source with SSB modulator, four-channel polarimetric receiver, FMCW velocity measurement, integrated thermal management, and maritime SAR application. The supplemental provisional extends the portfolio with: (1) additional DDR core embodiments including pulsed ToF ranging, sequential polarization switching, NMEA external sensor cueing, DDR variance-based confidence scoring with anti-spoofing analysis, and instrument fault detection; (2) robust adaptive environmental calibration using symmetric scattering media as continuous references; (3) shared-aperture beamsplitter architecture for autonomous closed-loop target acquisition with adaptive Galilean beam expander; and (4) perimeter sensor network with multi-node 2D velocity vector resolution and drift-predictive focused-scan handoff.

**SBIR Phase I (Submitted):** A Phase I proposal has been submitted to the U.S. Coast Guard for a bench-scale proof-of-concept demonstrating DDR material discrimination across nine target material classes relevant to maritime SAR. The proposed six-month effort delivers a man-portable field validation instrument with coaxial transmit/receive architecture, four-channel InGaAs detection, and integrated Raspberry Pi 5 processing with touchscreen display. Bench characterization at four distances (2–20 m) is followed by field validation at an Oregon coastal location under active wave conditions (Sea State 2–4). Success criterion: 10:1 DDR contrast ratio or greater between water and all critical target materials.

**Phase II Path:** Phase I results directly enable development of a scanning DDR sensor implementing the full dual 1D phased array architecture at 256×256 spatial resolution and approximately 10 Hz frame rate. Manufacturing partnerships have been identified with Voyant Photonics (silicon photonic phased array fabrication) and Teledyne FLIR (ruggedized maritime sensor production and existing Coast Guard procurement relationships).

**White Paper:** Peer-reviewed architecture published covering the complete system — from DDR measurement physics and manufacturing economics through link budget analysis and application to both FMCW maritime and pulsed ToF radar augmentation modalities.

## What This Demonstrates

This project illustrates Novel Systems Engineering's ability to identify a fundamental engineering bottleneck — in this case, the manufacturing yield crisis that has kept material-discriminating LiDAR prohibitively expensive — and design an architecture that resolves it while opening applications that the original problem framing did not anticipate. The work began with maritime SAR and expanded to radar augmentation, perimeter security networks, and autonomous systems — all enabled by the same DDR measurement physics and the same cost reduction that makes deployment viable. The patent portfolio, white paper, and SBIR submission represent the translation of that analysis into intellectual property and a funded development pathway.
