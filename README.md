# 32-bit RISC-V ALU in Logisim Evolution

A 32-bit RISC-V Arithmetic Logic Unit (ALU) designed and implemented using **Logisim Evolution**.

The project implements the main arithmetic, logical, comparison, shift, and upper-immediate operations used by the RISC-V instruction set. An instruction decoder is also used to automatically select the required ALU operation from a 32-bit RISC-V instruction.

## Supported Operations

| Operation | RISC-V Instruction |
|-----------|--------------------|
| ADD | `ADD` |
| SUB | `SUB` |
| Shift Left Logical | `SLL` |
| Set Less Than | `SLT` |
| Set Less Than Unsigned | `SLTU` |
| XOR | `XOR` |
| Shift Right Logical | `SRL` |
| Shift Right Arithmetic | `SRA` |
| OR | `OR` |
| AND | `AND` |
| Load Upper Immediate | `LUI` |
| Add Upper Immediate to PC | `AUIPC` |

## ALU Control Codes

| Control | Operation |
|---------|-----------|
| `0000` | ADD |
| `0001` | SUB |
| `0010` | SLL |
| `0011` | SLT |
| `0100` | SLTU |
| `0101` | XOR |
| `0110` | SRL |
| `0111` | SRA |
| `1000` | OR |
| `1001` | AND |
| `1010` | LUI |
| `1011` | AUIPC |

## Instruction Decoding

The circuit accepts a **32-bit RISC-V instruction** and extracts important instruction fields:

- `opcode = Instruction[6:0]`
- `funct3 = Instruction[14:12]`
- `funct7 = Instruction[31:25]`

For R-type operations, `funct7` and `funct3` are concatenated:

`{funct7, funct3}`

This produces a 10-bit value that is decoded to determine the required ALU operation.

A priority encoder generates the 4-bit ALU control signal, which controls the final multiplexer.

## Architecture

The basic data flow is:

`32-bit Instruction → Instruction Decoder → ALU Control → ALU → 32-bit Result`

The ALU contains separate blocks for arithmetic, logical, comparison, and shift operations. Their outputs are connected to a multiplexer controlled by the instruction decoder.

## Current Status

Implemented and tested:

- [x] ADD
- [x] SUB
- [x] SLL
- [x] SLT
- [x] SLTU
- [x] XOR
- [x] SRL
- [x] SRA
- [x] OR
- [x] AND
- [x] LUI
- [x] AUIPC
- [x] 32-bit instruction input
- [x] `funct3` extraction
- [x] `funct7` extraction
- [x] Opcode extraction
- [x] R-type instruction decoding
- [x] Automatic ALU operation selection
- [ ] I-type instruction support

## Software

Designed using **Logisim Evolution**.

## Project File

`RISC_V_32bit_ALU.circ`

## Author

**Muhammad Taha Ali**

Computer Systems Engineering
