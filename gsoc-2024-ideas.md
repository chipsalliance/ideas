# CHIPS Alliance GSoC 2024 project ideas 

1. [Create a GDS reader/writer in OpenROAD](#create-a-gds-readerwriter-in-openroad)
1. [Implement a common-pythonic API for the OpenROAD flow in OpenFASoC](#implement-a-common-pythonic-api-for-the-openroad-flow-in-openfasoc)
1. [Python based ORFs with parallelized hierarchical runs](#python-based-orfs-with-parallelized-hierarchical-runs)
1. [Support Zvk in T1 (RISC-V Vector coprocessor)](#support-zvk-in-t1-risc-v-vector-coprocessor)
1. [Spartan6 bitstream documentation](#spartan6-fpga-bitstream-documentation-for-f4pga)
1. [Document XADC and `DNA_PORT` blocks for Xilinx Series 7](#document-xadc-and-dna_port-blocks-for-xilinx-series-7-for-f4pga)
1. [Interactive Python interpreter for Synlig](#interactive-python-interpreter-for-synlig)
1. [Virtual lab environment for Tiny Tapeout](#virtual-lab-environment-for-tiny-tapeout)

## Create a GDS reader/writer in OpenROAD

GDS (or Graphic Design Stream) is used by OpenROAD to create visual representation of the physical layout. Currently, OpenROAD uses a hacky way to read and write GDS files. This hack involves the use of klayout. The aim of this project would be to implement read and write functions in OpenROAD itself and modify the GUI to account for the same

### Task Description

1. Get familiar with the OpenROAD documentation and source code 
    1. Examine the LEF and DEF classes (which have readers and writers already implemented)
1. Get familiar with the GDS-II format

1. Implement `gdsin` and `gdsout` classes in OpenROAD

1. Update the GUI source code to account for the changes

1. Review the feature PR with OpenROAD members

### Expected Outcomes

The goal is to implement a GDS-reader/writer in OpenROAD using OpenDB (ODB), which will serve as a reliable substitution to the hacky methods (involving klayout) that are currently employed.

### Required Skills

* Programming languages: C++, Python, a rudimentary knowledge of tcl
* Operating System Knowledge: Linux, Windows
* Nice to have: Knowledge on GDSII, knowledge on analog-circuit-design

### Difficulty

Medium: The task requires coding skills in both python and C++, with the latter being the language that the source code is written in. The main hurdle is getting familiar with the code.

_Duration_: 350 hours

_Mentor_: [@msaligane](https://github.com/msaligane)

### Further Reading

* [GDSII format](https://boolean.klaasholwerda.nl/interface/bnf/gdsformat.html)
* [OpenDB format](https://openroad.readthedocs.io/en/latest/main/src/odb/README.html)

## Implement a common-pythonic API for the OpenROAD flow in OpenFASoC

OpenFASoC uses OpenROAD’s RTL-to-GDSII flow, which makes use of tcl files to accomplish a fully No-Human-In-Loop flow. OpenFASoC is mostly written in python, with the outliers being the Makefiles used to trigger call the tcl scripts. The aim of the project would be to add the OpenROAD flow to existing common-python API (which currently implements verilog-generation and spice simulations) by making modules for each step of the flow.

### Task Description 

1. Create common pythonic modules for all steps of the OpenROAD flow (Setup, Synthesis, Floorplan, Placement, CTS, Routing, Finishing and Cleaning)

1. Create python scripts to replace the Makefiles present in the flow/ directory of each generator 

1. Replace top-level Makefiles in each generator directory with common-pythonic scripts

1. Update documentation and CI workflows to account for the changes

1. [Optional] Refactor pre-verilog generation (setup) code present in tempsense, cryo, and ldo-gen script files for clarity

### Expected Outcomes

The goal is to complete the currently existing the Common-Python API present in OpenFASoC (which supports Verilog Generation and Spice Simulations) by implementing the OpenROAD tcl-based flow in a similar way. This will also serve to bolster code consistency and allow for easier debugging by manner of Python's robust Warning and Error handling support.

### Required Skills

* Programming languages: Python, Make, Bash, a rudimentary knowledge of Markdown and C++
* Operating System Knowledge: Linux, Windows
* Nice to have: knowledge on analog-circuit-design

_Duration_: 350 hours

_Mentor_: [@msaligane](https://github.com/msaligane)

## Further reading

* [OpenFASoC's existing python API](https://github.com/idea-fasoc/OpenFASOC/blob/main/docs/source/common-python-api.rst)
* [OpenROAD flow](https://github.com/idea-fasoc/OpenFASOC/blob/main/docs/source/flow-tempsense.rst#rtl-to-gds-flow)

## Python based ORFs with parallelized hierarchical runs

OpenFASoC currently uses OpenROAD’s RTL-to-GDSII flow by supplying verilog source files alongwith constraint files. The goal of this project would be to implement Synthesis (APR and simulations) parallelly and hierarchically to generate a dataset, from which the best set of flow parameters can be chosen for a specific application (such as PPA - Power, Performance and Area) 


### Task Description 

1. Implement a python class containing global design parameters and flow configs
1. Implement modules containing information on the set of parameters generate the dataset on
1. Implement a machine learning algorithm to optimize parameters based on the application (as an example, Reinforcement Learning can be used)
1. Select best set of parameters for the final build

### Expected Outcomes 

The goal here is to implement a system that can sweep across a set of design parameters and pick an optimal design (based on the specified constraints) for the required use case. The use of Machine Learning will significantly improve the training time and the optimality of the final parameter set. 

### Required Skills

* Programming languages: Python, C++, Machine Learning, Make, Bash
* Operating System Knowledge: Linux, Windows
* Nice to have: Knowledge on Circuit Design, Knowledge on Power and Area Optimization in Circuits

### Difficulty

Medium/Hard: It is advisable to have knowledge on machine learning and hyperparameter tuning, alongwith a working knowledge on how to implement and optimise models in python

_Duration_: 350 hours

_Mentor_: [@msaligane](https://github.com/msaligane)

### Support Zvk in T1 (RISC-V Vector coprocessor)

T1 is a Cray-like long vector machine for RISC-V Vector.
Zvk is the RISC-V vector cryptographic specification. The goal of this project is adding ZvK support to T1, being able to execute Zvk instruction in T1.

### Task Description 

1. Adding corresponding decoding logic to T1.
1. Deciding the micro-architecture of Zvk, adding documentation.
1. Implementing the RTL in T1.
1. Testing Zvk in differnt configurations, adding CI to make it maintainable.

### Difficulty

Hard: Need strong capability in RTL designing and cryptographic knowledge. Need to understand the micro-architecture of vector processor. Need to write 1k lines of Scala code.

_Duration_: 175 hours

_Mentor_: [@sequencer](https://github.com/sequencer)

## Spartan6 FPGA bitstream documentation for F4PGA

Spartan6 is a popular FPGA from AMD (formerly Xilinx) which is still used in many boards on the market today.
For exactly this reason there is continued interest in creating an open source toolchain for this architecture.
There has already been some work in F4PGA with regard to this architecture, namely, it's possible to read the original bitstream and convert to a textual representation of its content in the form of what bits in which frame are active.
F4PGA tools can also generate a bitstream from a textual representation.
The missing part falls into the scope of project X-Ray where the meaning of the bits found in the bitstream has to be determined.
The idea is to extend the existing set of project X-Ray infrastructure/tools/fuzzers to document the information which bits correspond to what features of the Spartan6 architecture.

### Expected Outcome

As a result of this work some basic fuzzers required in X-Ray for a small Spartan6 FPGA (e.g. XC6SLX9) will be created.
One of them is the part fuzzer which produces the information about how many configuration columns and rows there are.
Another is the tilegrid fuzzer which lists what tiles the FPGA is built on.

### Skills Required

* Familiar with the following tools: Vivado, ISE
* Programming/scripting languages: TCL, Python, C++
* HDL languages: Verilog

### Difficulty

Hard: This project requires some deeper understanding of FPGA architectures.
Experience with the ISE tool and TCL scripting language is useful for this task.
Python and C++ are vital to create or enhance existing tools used in X-Ray.

_Duration_: 350 hours

_Mentor_: [@tmichalak](https://github.com/tmichalak)

## Document XADC and `DNA_PORT` blocks for Xilinx Series 7 for F4PGA

F4PGA's open source FPGA flow depends on so-called [architecture definitions](https://github.com/SymbiFlow/f4pga-arch-defs), which are hardware descriptions of specific FPGAs that enable using specific configurable and hard blocks.
Documentation of Xilinx 7-series hard blocks is covered by [project X-Ray](https://github.com/SymbiFlow/prjxray).
This documentation is however not complete, and feature-parity with closed tools requires more work in documenting additional FPGA blocks.

Among other dedicated hard-blocks performing functionality that cannot be implemented directly using the FPGA fabric, the Xilinx 7-series devices provide the `XADC` block and `DNA_PORT` block.
The former is a generic dual 12-bit A/C converter capable not only of sampling external voltages but also reading the device's internal sensors like the temperature sensor.
The latter block allows accessing unique device identification data a.k.a. "DNA".

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

## Interactive Python interpreter for [Synlig](https://github.com/chipsalliance/synlig)

Synlig is a SystemVerilog-capable front-end to Yosys.
Like many RTL design tools, currently Synlig relies on the TCL interpreter provided by Yosys.
More and more tools in the space are however adopting modern languages like Python as their interpreters which opens up a lot of powerful capabilities and integrations, and better fits the expected skillset of a more general software audience.
The goal of this project is to add its own, optional Python interpreter to Synlig, which would enable usage both interactively and through standalone Python scripts.

### Expected Outcome

As a result of this project, the following should be achieved:

* Built-in Python interpreter for Synlig (external interpreters can be used), with capabilities that match the current TCL interpreter
* Python bindings that allow Python scripting with capabilities that match the current TCL scripting possibilities

### Skills Required

* Programming languages: C++, Python, a rudimentary knowledge of TCL
* Nice to have: HDL languages (Verilog)

### Difficulty

Medium: The project requires getting acquainted with the codebase of Synlig, requires expertise in multiple programming languages and some knowledge about integration of third-party libraries with the project.

_Duration_: 350 hours

_Mentor_: [@tgorochowik](https://github.com/tgorochowik)

## Virtual Lab Environment for Tiny Tapeout

Semiconductor fabrication is an expensive endeavor that has traditionally been beyond the reach of most students and hobbyists (and even companies). In recent years, "democratization of semiconductors" and "semiconductor workforce development" are getting a great deal of attention, the goal being to make semiconductors and semiconductor education more accessible. Several technologies and initiatives are coming together on this common mission:

 - ChipIgnite is a program offered by [Efabless](https://efabless.com) providing inexpensive multi-project wafer fabrication.
 - [Tiny Tapeout](https://tinytapeout.com) subdivides the ChipIgnite silicon area into 250 smaller tiles that can be used individually at a very low cost.
 - The free online [Makerchip](https://makerchip.com) design environment by [Redwood EDA](https://redwoodeda.com) lowers the barrier to entry into digital circuit design.

Recently, these technologies have been used in [workforce development training](https://github.com/efabless/chipcraft---mest-course) to enable newcomers to learn digital logic design and fabricate their own Tiny Tapeouts in a relatively short period of time.

In these classes, learners utilize three levels of hardware modeling:

1. A simulation-based virtual lab environment. This is provided as open-source code that runs within Makerchip. It virtualizes the physical Tiny Tapeout boards showing input switch settings and output LEDs.
2. FPGA-based "Demo Boards" look and act like the ASIC boards learners will later receive but can be reprogrammed to support development.
3. The ultimate ASIC boards are fabricated and assembled, containing the learners' taped-out designs.

The virtual lab environment currently virtualizes the Tiny Tapeout board only. This board has I/Os that can interface with external [Pmod](https://digilent.com/reference/pmod/start) devices. This project will extend the virtual lab environment to virtualize various Pmod devices. The lab bench setup will be configured within the user's source code to define the use of Pmod devices and controllers for those Pmods. This project may include the development of some of those controllers and the infrastructure for selecting them. This lab environment is based on a more-general environment for FPGA development, and this work can be applied more generally in that environment as well.

### Task Description

1. Acquire the necessary hardware (Tiny Tapeout Demo boards, Pmods, cables). These can be purchased and shipped by mentors, but applicants should confirm shipping requirements with mentors before applying.)

1. Get familiar with the technologies listed under "Further Reading". This will be a substantial portion of the project.

1. Develop Pmod visualizations.

1. Develop mechanisms for lab bench configuration (Pmod selection).

1. Develop Pmod controllers.

1. Write clear and concise documentation.

### Expected Outcomes

A rich lab environment for developing Verilog-based designs for Tiny Tapeout and FPGA platforms.

### Required Skills

* TL-Verilog
* M5 (text processing language used with TL-Verilog)
* JavaScript (for visualization)
* GitHub
* FPGA development
* An ability to thrive in a rapidly evolving ecosystem.

### Difficulty

Medium/Hard: The project will expose the applicant to several emerging technologies.

_Duration_: 350 hours

_Mentors_: [@stevehoover](https://github.com/stevehoover), [@jeffdi](https://github.com/jeffdi), [@mattvenn](https://github.com/mattvenn)

### Further Reading

* Various specs within [Makerchip](https://makerchip.com) IDE including TL-Verilog spec, M5 spec, TL-Verilog Macros Guide, and Visual Debug Spec.
* [Tiny Tapeout](https://tinytapeout.com/)
* Current [workforce development course content](https://github.com/efabless/chipcraft---mest-course) including code templates
* [Virtual FPGA Lab](https://github.com/os-fpga/Virtual-FPGA-Lab)
* Current [Tiny Tapeout virtual lab environment](https://github.com/os-fpga/Virtual-FPGA-Lab/blob/tt/tlv_lib/tiny_tapeout_lib.tlv)
* [Pmods](https://digilent.com/reference/pmod/start)
