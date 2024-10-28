# RISC-V

## Overview

This project consists of three scripts namely assembler_risv.cpp, pipeline_riscv.cpp and nonPipeline_risv.cpp. Assembler Script converts RISC-V instruction to Machine Language. Pipeline or Non-Pipeline script can be used to process the Machine Language produces by the assembler to generate the output. 

## Supported Instructions

The assembler supports the following instructions, grouped by their types:

### R-Type Instructions
- `add` - Addition
- `sub` - Subtraction
- `and` - And
- `or`  - Or
- `xor` - Xor
- `sll` - Shift Left Logical
- `srl` - Shift Right Logical
- `mul` - Multiplication

### I-Type Instructions
- `addi` - Addition Immediate
- `xori` - Xor Immediate
- `ori` - Or Immediate
- `andi` - And Immediate
- `slli` - Shift Left Logical Immediate
- `srli` - Shift Right Logical Immediate

### L-Type Instructions (Load)
- `lb` - Load Byte
- `lh` - Load Half
- `lw` - Load Word
- `lbu` - Load Byte (U)
- `lhu` - Load Half (U)

### S-Type Instructions (Store)
- `sb` - Store Byte
- `sh` - Store Half
- `sw` - Store Word 

### J-Type Instruction
- `jal` - Jump and Link

### B-Type Instructions (Branch)
- `beq` - Branch ==
- `bne` - Branch !=
- `blt` - Branch <
- `bge` - Branch >=
- `bltu` - Branch < (U)
- `bgeu` - Branch >= (U)

### U-Type Instruction
- `lui` - Load Upper Immediate

## Getting Started

### Prerequisites
- C++ Compiler (e.g., g++, clang++)

### Compilation
- First create a input file inside the testing folder with ".s" extension
- Write the input file name in the main function of pipeline_riscv.cpp or nonPipeline_risv.cpp
- At the same type write the same file name with ".o" extension
- Note : The file name with ".o" extension will created along the way. No need for the user to create it.
- Then compile the pipeline_riscv.cpp or nonPipeline_riscv.cpp which ever the user want to use.
- To compile, you can run the following command: (assuming pipeline_risv.cpp is being used)

```bash
g++ -o pipeline_riscv pipeline_riscv.cpp
```

Once compiled, the binary file will be generated inside the testing folder with ".o" extension. <br>
The output can be checked by printing the register and memory location used. <br>
To check the output user have to use the `cout` inside the main function by himself/herself. <br> 
<br><br>

### Example Input

#### Rules to Write Input File
- Total of 32 Register are available (0-31).
- To access register use `x` foolowed by number. Example : `x4` for 4th Register  .
- Use only lower case for the instruction, give space to distinguish and use `,` to after register. 
- Label naming is not case senitive, but kindly use lower case only
- Negative Immediate is NOT SUPPORTED , kindly use `sub` for the same

```assembly
lw x18, 0(x0)

l:
    andi x28, x18, 1
    add x19, x19, x28
    srli x18, x18, 1
    beq x18, x0, r
    jal x5, l
r:
    sw x19, 1(x0)
```

### Example Main Function

The main function assuming the file name of above is `setBit` . As the user can see the value that needs to be used as input written in the memory before assembler is invoked. And the final values will stored in the memory location and register is printed using the `cout` after pipeline is invoked.<br>
- Register are named `myRegister`
- Memory is named `myMemory` <br>
```main
int main(){
    string s1 = "setBit.s";
    string s2 = "setBit.o";

    myMemory[0]=5;

    assembler a(s1);
    pipeline p(s2);

    cout<<myMemory[1]<<endl;
}
```
## Other Features
- Inside the 

## Contributing

If you'd like to contribute to this project, feel free to submit a pull request or open an issue.
