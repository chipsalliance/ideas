# CHIPS Alliance GSoC 2023 project ideas

1. [Create FEOL Classes in OpenROAD and a GDS writer](#create-feol-classes-in-openroad-and-a-gds-writer)
1. [Simplify and automate the Verilog Generation Step in OpenFASOC](#simplify-and-automate-the-verilog-generation-step-in-openfasoc)
1. [Introduce Special Router Feature and Utilize in OpenFASoC](#introduce-special-router-feature-and-utilize-in-openfasoc)
1. [FPGA chips database visualizer improvements](#fpga-chips-database-improvements)
1. [DSP hard block integration in F4PGA](#dsp-hard-block-integration-in-f4pga)
1. [Improve the visual representation of the placement done by VTR](#improve-the-visual-representation-of-the-placement-done-by-vtr)
1. [Spartan6 bitstream documentation](#spartan6-bitstream-documentation)
1. [Document XADC and `DNA_PORT` blocks for Xilinx Series 7](#document-xadc-and-dna_port-blocks-for-xilinx-series-7)
1. [FPGA Tool Performance Results Visualization](#fpga-tool-performance-results-visualization)

## Create FEOL Classes in OpenROAD and a GDS writer

OpenFASOC uses OpenROAD heavily for AMS design.
To extend our usage of OpenROAD to more customized layout generation of the designs, it would be necessary to add support of FEOL (Fron End of Line) layers in OpenROAD.
This would be unheard of that a place, and route tool understands active layers.
We could potentially use the odb format to store this information and eventually create shapes for active and passive devices.
Additionally, creating a gds writer in OpenROAD would make the tool more complete and the need tp call external tools to write a gds.
The current workarounds are hacks that do not yield ideal results.

### Task description

1. Investigate Layer related classes in OpenROAD
1. Process metal stack data from open source PDKs to automatically load FEOL layers in OpenROAD when needed

    1. Create a proof of concept where a simple auxiliary cell or Standard cell is created within OpenROAD for OpenFASOC’s usage
    1. Explore potential leads on how to create a full generator within OpenROAD

        1. The temperature sensor could be used as an example

1. Create a GDS writer and reader in OpenROAD

    1. Work on feature PR with team-members from OpenROAD
    1. Implement and thoroughly test the new GDS writer for bugs or issues
    1. Review with Openroad team (PR review)

1. Create a simple generator within OpenROAD

### Expected outcomes

The goal is to create more possibilities for OpenFASOC within OpenROAD by creating support for FEOL layers. And making OpenROAD more complete by adding a write gds command.

### Required skills

* Programming languages: Python, C++
* Operating system knowledge: Linux, Windows
* Nice to have: Circuit level and Physical Design basic understanding

### Difficulty

Medium: The task does require python and C++ coding skills are needed, circuit IC design knowledge would be useful.

_Duration_: 350 hours

_Mentor_: [@msaligane](https://github.com/msaligane)

## Simplify and automate the Verilog Generation Step in OpenFASOC

OpenFASOC creates an automated generation of the Verilog representation of a design/block using Python and template files.
The existing Verilog generation is design dependent and isn’t using consistent formatting.
Also, depending on the complexity of the design, sweeping the number of auxiliary cells can become complex and time consuming.
The current workarounds are hacks that do not yield ideal results.

### Task description

1. Investigate the existing generators in OpenFASOC and FASOC

    1. Explore new ways of generating Verilog using tools existing open source tools
    1. Propose new ideas to simplify th verilog generation

1. Implement Python code that allows Verilog generation for new analog generators

    1. Review all the generators in FASOC and implement them in OpenFASOC
    1. Create new templates and Python tools for new blocks

1. Implement regression tests in the CI to make sure functionality isn’t broken

    1. Add Verilog to Spice generation to be able to simulate the netlist before synthesis

1. Implement the new Verilog generation flow in OpenFASOC and test it on existing generators

### Expected outcomes

The goal is to simplify the Verilog Generation step in OpenFASOC and reduce the time to create a new generator

### Required skills

* Programming languages: Python, C++
* Operating system knowledge: Linux, Windows
* Nice to have: Circuit level and Physical Design basic understanding

### Difficulty

Medium: The task does require python and C++ coding skills are needed, circuit IC design knowledge would be useful.

_Duration_: 350 hours

_Mentor_: [@msaligane](https://github.com/msaligane)

## Introduce Special Router Feature and Utilize in OpenFASoC

OpenFASoC generators create multi-voltage domain designs using Openroad.
Currently, these routes require special scripts (python and tcl scripts) to identify and create routes from analog cells to power straps and between macros in different voltage domains.
Routes to power nets (for example the temp-sense HEADER routes) require creating a rpin on the power strap and configuring it as a “signal” type route; This is because the power nets are not routed by signal routers in Openroad.
Generators currently use non default rules to allow for high quality routing, but the route layer cannot be specified (and the route uses the signal router).
The signal type route additionally createst LVS issues (rpin signal net causes issues with LVS); Custom OpenFASoC python scripts are used to resolve the issues caused by rpin/pin naming.
This feature was first proposed in summer 2022 and has been brought up several times when discussing temp-sense-gen and ldo-gen (see OR issue 2209 below).
The issues caused by these hacks have been a constant source of bugs in OpenFASoC. The OpenFASoC team has attempted to improve the quality of the routes, but a full solution in Openroad would yield much better results.
The current workarounds are hacks that do not yield ideal results.

### Task description

1. Investigate routing algorithms that are well suited for a special router

    1. Implement test algorithms or explore existing literature and documented results.

1. Understand relevant portions of the Openroad code-base

    1. Communicate further with Openroad team about proposed algorithms and appropriate changes
    1. Plan router with Openroad team

1. Create: code and merge new feature to Openroad

    1. Work on feature PR with team-members
    1. Implement and thoroughly test the new router for bugs or issues
    1. Review with Openroad team (PR review)

1. Utilize p2p feature in OpenFASoC

    1. Test this feature with ldo-gen

### Expected outcomes

The aim of this task is to create a special router in Openroad and begin utilizing it in the OpenFASoC generators.

### Required skills

* Programming languages: Python, C++
* Operating system knowledge: Linux, Windows
* Nice to have: Circuit level and Physical Design basic understanding

### Difficulty

Medium: The task does require python and C++ coding skills are needed, circuit IC design knowledge would be useful.

_Duration_: 350 hours

_Mentor_: [@msaligane](https://github.com/msaligane)

### Further reading

* [Open FASoC repo](https://github.com/idea-fasoc/OpenFASOC)
* [Temperature sensor Openroad issue 2209](https://github.com/The-OpenROAD-Project/OpenROAD/issues/2209)
* [LVS workaround for extracted netlist pin/rpin hack](https://github.com/idea-fasoc/OpenFASOC/blob/main/openfasoc/common/drc-lvs-check/process_extracted_pins.py)

## FPGA chips database visualizer improvements

The [F4PGA database visualizer](https://github.com/chipsalliance/f4pga-database-visualizer) is an open source tool for visualizing the structure of FPGA chips covered by the F4PGA project. This is very useful in understanding the internal structure of specific FPGAs and reasoning about ways to best support them in the open source tools. Currently the tool supports visualizing the top level structure (tiles) of an FPGA chip as it is documented and modeled in open source toolchains.

### Task description

The main goal of the project is to extend the tool with the possibility of visualizing internal structures of the tile cells of an FPGA chip. This will require the following changes:

* Extending the frontend with functionality of rendering sub tiles within a tile, or with a functionality of “entering” a tile to see its details
* Extending the intermediate format used by the tool with functionalities required to handle multiple levels of the device
* (Nice to have) Adding a more detailed visualization of the tiles internals (Basic Logic Elements [like LUTs, DFFs], and their interconnections

## Expected outcomes

The work will result in improvements in the existing FPGA devices visualization software allowing it to show details of logic tiles of the visualized chip. As part of the work, the existing [visualization demo](https://chipsalliance.github.io/f4pga-database-visualizer/) will have to be extended to present the tile details.

### Required skills

Python, NodeJS, basics of HTML/CSS

### Difficulty

Medium: the project touches different aspects of the tool:

* Intermediate representation of the chip data
* Frontend and grid rendering

During the project it will be necessary to collaborate with the F4PGA development team to determine the best way of presenting the tiles details so that it is understandable to FPGA users.

_Duration_: 175 hours or 350 hours

_Mentor_: [@kgugala](https://github.com/kgugala)

### Further reading

* [Example chip visualization](https://chipsalliance.github.io/f4pga-database-visualizer/?dbfile=data%2Fprjxraydb%2Fartix7%2Fxc7a100t.json)
* [Visualizer repository](https://github.com/chipsalliance/f4pga-database-visualizer)

## DSP hard block integration in F4PGA

Modern FPGAs are equipped with multiple dedicated hard-blocks which can perform operations that would be slow and resource consuming if implemented as a part of a design in the fabric. An example of such a hard-block is a DSP (Digital Signal Processing) unit. DSP blocks can perform basic math operations like addition, multiplicaion and multiply-accumulate which are very common in signal processing pipelines.

The DSP hard block of the Xilinx 7-series FPGA devices (DSP48E) is currently documented in [Project X-Ray](https://github.com/SymbiFlow/prjxray), but it currently lacks support within the [F4PGA architecture definitions](https://github.com/SymbiFlow/f4pga-arch-defs). The aim of this project is to add support for DSP48E to the architecture definition so that it can be supported by the toolchain. This will enable designs using DSPs to be synthesized, placed and routed correctly.

This project will also aim at enabling the entire testing flow for designs using Xilinx 7-series DSP hard blocks to complete successfully.
The testing flow includes:

* Verilog-to-Bitstream using the F4PGA toolchain
* Fasm2bels to re-generate the original netlist from the bitstream output of F4PGA
* Proof-test through Vivado to verify the correctness of the netlist.

### Expected Outcome

This project will enable full support of DSP hard blocks within the F4PGA toolchain, which will translate to improving coverage for real world designs and more widespread adoption. 

### Skills Required

* Familiar with the following tools: Vivado, Yosys
* Programming/Scripting languages: Python, C++
* HDL: Verilog

### Difficulty

Hard: This project takes into consideration many different aspects of the toolchain, including the architecture generation infrastructure, synthesis and place and route. Moreover, the skill-set required to achieve the goal is very diverse.

### Further Reading

* [f4pga-arch-defs documentation](https://f4pga.readthedocs.io/projects/arch-defs/en/latest/)

_Duration_: 350 hours

_Mentor_: [@mkurc-ant](https://github.com/mkurc-ant)

## Spartan6 bitstream documentation

Spartan6 is a popular FPGA from AMD (formerly Xilinx) which is still used in many boards on the market today. For exactly this reason there is continuous interest in creating an open source toolchain for this architecture. There has already been some work in F4PGA with regard to this architecture. Namely, it’s possible to read the original bitstream and convert to a textual representation of its content in the form of what bits in which frame are active. F4PGA tools can also generate a bitstream from a textual representation.
The missing part falls into the scope of project X-Ray where the meaning of those bits found in the bitstream has to be determined.
The idea is to extend the existing set of project X-Ray infrastructure/tools/fuzzers to document the information which bits correspond to what features of the Spartan6 architecture

### Expected Outcome

As a result of this work some basic fuzzers required in X-Ray for a small Spartan6 FPGA (e.g. XC6SLX9) will be created.
One of them is the part fuzzer which produces the information about how many configuration columns and rows there are. Another is the tilegrid fuzzer which lists what tiles the FPGA is built on.

### Skills Required

* Familiar with the following tools: Vivado, ISE
* Programming/scripting languages: TCL, Python, C++
* HDL languages: Verilog

### Difficulty

Hard: This project requires some deeper understanding of FPGA architectures. Experience with the ISE tool and TCL scripting language is useful for this task. Python and C++ are vital to create or enhance existing tools used in X-Ray.

_Duration_: 350 hours

_Mentor_: [@tmichalak](https://github.com/tmichalak)

## Document XADC and `DNA_PORT` blocks for Xilinx Series 7

Among other dedicated hard-blocks performing functionality that cannot be implemented directly using FPGA fabric Xilinx 7-series devices provide the `XADC` block and `DNA_PORT` block. The former is a generic dual 12-bit A/C converter capable not only of sampling external voltages but also reading the device's internal sensors like the temperature sensor. The latter block allows accessing unique device identification data a.k.a. "DNA".

F4PGA’s FPGA flow depends on so-called [architecture definitions](https://github.com/SymbiFlow/f4pga-arch-defs), which are hardware descriptions of specific FPGAs that enable using specific configurable and hard blocks. Documentation of Xilinx 7-series hard blocks is covered by [project X-Ray](https://github.com/SymbiFlow/prjxray).
The task is to extend the existing fuzzer to document all XADC related configuration bits as well as create a new fuzzer for the DNA block so that they become available in the open source flow.

### Expected Outcome

As a result of this task 2 complete fuzzers shall be created:

* `XADC` fuzzer which will be the extended version of the existing fuzzer for XADC that will generate the list of XADC related features and the bits corresponding to them
* `DNA_PORT` fuzzer that will generate the list of DNA_PORT related features and corresponding bits

### Skills Required

* Scripting languages: TCL
* HDL languages: Verilog

### Difficulty

Easy: The task mostly requires getting familiar with the methodology used in other X-Ray fuzzers and reusing existing or coming up with your own approach to get the expected outcome.

_Duration_: 175 hours

_Mentor_: [@mkurc-ant](https://github.com/mkurc-ant)

