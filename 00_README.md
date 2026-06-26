# 5-stage-pipeline-processor
# 5-Stage Pipelined RISC-V Processor

## Project Overview

This project implements a **5-stage pipelined RISC-V processor** using the Verilog Hardware Description Language (HDL). The processor follows the classic IF–ID–EX–MEM–WB pipeline architecture and supports arithmetic, immediate, memory, and branch instructions. The design also includes a forwarding unit for data hazard resolution and a testbench for functional verification.

### Key Features

* **Pipeline Architecture**: Implements a classic 5-stage pipelined processor for improved instruction throughput.

* **Supported Instructions**:

  * **Arithmetic Operations**

    * `ADD`
    * `SUB`
    * `AND`
    * `OR`
    * `SLT` (Set Less Than)
  * **Immediate Operations**

    * `ADDI`
  * **Memory Operations**

    * `LW` (Load Word)
    * `SW` (Store Word)
  * **Branch Instructions**

    * `BEQ` (Branch if Equal)

* **Hazard Handling**

  * Data hazard resolution using a **Forwarding Unit**
  * 3-to-1 forwarding multiplexers in the Execute stage

* **Memory Organization**

  * Separate Instruction Memory and Data Memory (Harvard Architecture)

* **Testbench**

  * Includes a Verilog testbench with instruction loading through `memfile.hex` and waveform verification using GTKWave.

## Getting Started

### Prerequisites

To run this project, you will need:

* A Verilog simulator (e.g., ModelSim, Vivado, or Icarus Verilog)
* GTKWave for waveform visualization

### Running the Simulation

1. Clone the repository:

```bash
git clone <repository_url>
cd <repository_name>
```

2. Compile all Verilog source files and the testbench using your simulator.

3. Run the simulation to generate the waveform file.

4. Open the generated `dump.vcd` file in GTKWave to analyze pipeline execution.

## How It Works

### Pipeline Stages

The processor implements a **5-stage pipeline**:

1. **Instruction Fetch (IF)** – Fetches instructions from Instruction Memory.
2. **Instruction Decode (ID)** – Decodes instructions, reads register operands, and generates control signals.
3. **Execute (EX)** – Performs ALU operations, computes branch targets, and resolves data hazards using forwarding.
4. **Memory Access (MEM)** – Executes load/store operations through Data Memory.
5. **Write Back (WB)** – Writes the final result back to the Register File.

### Control Unit

The control unit generates the required control signals for each pipeline stage, while the forwarding unit minimizes data hazards during execution.

## Testing and Verification

* The processor is verified using a Verilog testbench and instruction memory (`memfile.hex`).
* Verification covers:

  * Arithmetic instructions
  * Immediate instructions
  * Load and Store operations
  * Branch execution
  * Data forwarding
* GTKWave waveforms are used to verify correct pipeline execution.
