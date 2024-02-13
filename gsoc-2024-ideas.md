# CHIPS Alliance GSoC 2024 project ideas 

1. [Create a GDS reader/writer in OpenROAD](#create-a-gds-reader-writer-in-openroad)
1. [Implement a common-pythonic API for the OpenROAD flow in OpenFASoC](#implement-a-common-pythonic-api-for-the-openroad-flow-in-openfasoc)
1. [Python based ORFs with parallelized hierarchical runs](#python-based-orfs-with-parallelized-hierarchical-runs)

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

### Support Zvk in T1(RISC-V Vector coprocessor)
T1 is a Cray-like long vector machine for RISC-V Vector. Zvk is the RISC-V vector cryptographic specification. The goal of this project is adding ZvK support to T1, being able to execute Zvk instruction in T1.

### Task Description 

1. Adding corresponding decoding logic to T1.

1. Deciding the micro-architecture of Zvk, adding documentation.

1. Implementing the RTL in T1.

1. Testing Zvk in differnt configurations, adding CI to make it maintainable.

### Difficulty

Hard: Need strong capability in RTL designing and cryptographic knowledge. Need to understand the micro-architecture of vector processor. Need to write 1k lines of Scala code.

_Duration_: 175 hours

_Mentor_: [@sequencer](https://github.com/sequencer)
