Flyback Converter Simulation — 85-265V AC to 12V 5A (LTSpice)
Overview
A complete simulation of an isolated flyback converter designed for universal AC input (85–265V AC) with a regulated 12V, 5A DC output. The simulation is built in LTSpice and includes a closed-loop feedback network using an optocoupler and TLV431 shunt reference for output voltage regulation.

Specifications
ParameterValueInput Voltage85V – 265V AC (Universal)Output Voltage12V DCOutput Current5AOutput Power60WSwitching FrequencySet by LT1242 Rt/Ct networkTopologyIsolated Flyback ConverterControl MethodPeak Current Mode (LT1242)

Key Components
ComponentPartRoleController ICLT1242PWM controller with peak current mode controlPower SwitchSTN3N45K3 MOSFETPrimary side switchingOutput RectifierMBR20100CTSchottky diode for output rectificationFeedback ReferenceTLV431Programmable shunt voltage referenceOptocoupler4N26Isolated feedback signal transmissionSnubber DiodeMUR460Clamp for leakage inductance spikesInput Rectifier4× 1N4007Full-wave bridge rectifierTransformerCustom designedDesigned specifically for this project

Circuit Description
Input Stage

A full-wave bridge rectifier (4× 1N4007 diodes) converts the universal AC input (85–265V AC, 50Hz) to a rectified DC bus
A bulk capacitor (C1 = 220µF) smooths the rectified voltage

Control IC — LT1242

Operates in peak current mode control
Rt/Ct network (R13, C9, C10) sets the switching frequency
FB pin receives error signal via optocoupler
Isense pin monitors primary MOSFET current through R11 (0.25Ω)
COMP pin provides error amplifier compensation

Transformer (Custom Designed)

Designed from scratch for this application
Coupled inductors modeled with: L1 = 115µH (primary), L2 = 1.57µH, L3 = 2.76µH
Coupling coefficients: K1, K2, K3 ≈ 0.995 (tight coupling)

Output Stage

MBR20100CT Schottky rectifier for low forward-drop output rectification
Multiple output capacitors in parallel (C2–C7, 220µF each) for low ripple

Feedback Network (Closed Loop)

TLV431 shunt regulator senses the output voltage via resistor divider (R4, R5)
Error current drives the LED of 4N26 optocoupler
Optocoupler transmits the error signal across the isolation barrier to the LT1242 FB pin
Provides tight regulation of the 12V output across load and line variations

Startup & Auxiliary Supply

Rstart (68kΩ) provides startup current to the controller
Auxiliary winding supplies Vcc to the LT1242 after startup


Project Status
FeatureStatusSchematic Design✅ 
CompleteTransformer Design✅ 
CompleteOpen Loop Simulation✅
CompleteClosed Loop Feedback✅ 
ImplementedOvervoltage Protection (OVP)🚧 In Progress
Undervoltage Protection (UVP)🚧 In Progress
Efficiency Analysis🔲 Planned
PCB Design🔲 Planned

Tools Used

LTSpice — Circuit simulation
Custom transformer design calculations


Author
Rithik Mohanan
