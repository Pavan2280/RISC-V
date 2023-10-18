# Objective 
> VLSI ASIC design involves creating custom circuits optimized for specific tasks using RTL (Register-Transfer Level) description. This involves designing digital logic using hardware description languages like VHDL or Verilog, converting it to gate-level representation through synthesis, and eventually translating it into a physical layout for fabrication. The process includes architectural design, logic implementation, verification, and testing, resulting in highly efficient and tailored integrated circuits.

# Outcomes
+ RTL Description
+ Logic Synthesis
+ Physical Design
+ Verification

# Minimum Requirements for installation 
- ubuntu 20 + 
- min. disk space 150 Gb 
- RAM at least 6 Gb

# Steps for installation
- Enter these commands in terminal 
```
git clone https://github.com/kunalg123/riscv_workshop_collaterals
cd riscv_workshop_collaterals
chmod 755 run.sh
./run.sh 
```

<a name="top"></a>
  
##### This Repository Guides you to complete the RISC-V-BASED MYTH Course Assignments - Guided by Kunal Ghosh

# Table of contents

<details>
<summary>DAY-1 : Introduction to RISC-V ISA and GNU compiler toolchain</summary>
<br>
  
+ Task-1 : C Program To Compute Sum From 1 to N (using gcc) & Spike Simulation And Debug (using RISCV)
    + Command to execute code using gcc
    ```
    gcc 1_n_sum.c
    ./a.out
    ```
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -o1 mabi=lp64 -march=rv64i -o 1_n_sum.o 1_n_sum.c
    spike pk 1_n_sun.o
    ```
    ![#4](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8b4e47d3-f3ba-40e1-b26d-166ee93ce174) 

+ Task-2 : To debug the ALP generated by the compiler
    ```
    spike -d pk 1_n_sun.o
    ```
    ![de](https://github.com/Pavan2280/pes_asic_class/assets/131603225/ac22b9e7-6c71-423a-bfd7-a445ec226e95)

+ Task-3 : Contents of main using different optimizer
   - Using 1 : -O1 optimizer
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -o1 mabi=lp64 -march=rv64i -o 1_n_sum.o 1_n_sum.c
    riscv64-unknown-elf-objdump -d 1_n_sum.o | less
    ```
    ![o1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/2765fb0e-439d-404d-8b39-ef2089ca746b)
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o 1_n_sum.o 1_n_sum.c
    riscv64-unknown-elf-objdump -d 1_n_sum.o | less
    ```
   -  Using 2 : -Ofast optimizer
    ![ofast](https://github.com/Pavan2280/pes_asic_class/assets/131603225/cac8e8f0-1def-482b-9cbe-348f6ed8dc33)

+ Task-4 : Lab For Signed And Unsigned Numbers
    + Command to execute code using gcc
    ```
    gcc us_highest.c
    ./a.out
    ```
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o us_highest.o us_highest.c
    spike pk us_highest.o
    ```
    ![#5](https://github.com/Pavan2280/pes_asic_class/assets/131603225/2f5ccf76-3dd3-4261-ad80-03ccf886ba55)
    ![#5_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/a281e314-5894-4844-b281-528586984667)
    ![#5_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/693f403f-eee9-4a21-a46c-ee0e50dc461e)
    ![#5_3_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/b3e05a8e-8305-427d-9e3d-86add6fffdd9)
    ![#5_3_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/64d22154-52e0-492a-97e7-39287bf0dc0c)
    ![#5_3_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/73b13dab-457d-4739-9e3f-386a9f6ead6f)
    ![#5_4_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/eb62c0b2-f47d-4aef-8858-207a69387a3d)
    ![#5_4_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8c8ae69b-1158-4b69-8d57-fc97a51afc7f)
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o s_highest.o s_highest.c
    spike pk s_highest.o
    ```
    ![#6_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d3f46dd8-f962-47c8-8603-f5bcf391e827)
    ![#6_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/ffd2fced-a464-45e8-be37-451147b8420a)
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o signed_highest.o signed_highest.c
    spike pk signed_highest.o
    ```
    ![#7_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/a1994ddc-1b9c-4497-8984-8b1dcddc66ff)
    ![#7_2](https://github.com/Pavan2280/pes_asic_class/assets/131603225/d0ee8cd2-162a-4f00-b285-2b95f48bce44)

[Back to Top](#top)
</details>

<details>
<summary>DAY-2 : Introduction to ABI and basic verification flow</summary>
<br>
  
+ Task-1 : Sum 1 to N Using ASM and simulating C program with function call
    + Command to execute code using riscv
    ```
    riscv64-unknown-elf-gcc -ofast mabi=lp64 -march=rv64i -o 1_9custom.o 1_9custom.c load.s
    spike pk 1_9custom.o
    riscv64-unknown-elf-objdump -d 1_9custom.o | less
    ```  
    ![#8](https://github.com/Pavan2280/pes_asic_class/assets/131603225/f1400495-8618-470f-9b3a-aa7c61b8eb6e)
    ![#8_1](https://github.com/Pavan2280/pes_asic_class/assets/131603225/8311e3f6-fa0e-4eb7-84c1-7ef8488f6ea3)
    ![8_4_new](https://github.com/Pavan2280/pes_asic_class/assets/131603225/e88722d5-63b8-41e2-9e41-35c9bbf87080)

+  Task-2 : Lab To Run C-Program On RISC-V CPU
    ```
    chmod 777 rv32im.sh
    ./rv32im.sh
    ```
    ![#8_3](https://github.com/Pavan2280/pes_asic_class/assets/131603225/519d8386-d509-40d6-bfca-b1817b4d2bd9)

[Back to Top](#top)
</details>

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/9a131993-315c-4406-80fb-0da36370b966)

<details>
<summary>DAY-3 : Digital Logic with TL-Verilog in Makerchip IDE</summary>
<br>

#### Task-1 : Logic Gates

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/24cfbcd8-3ff2-4cae-b4fa-488e5c77af5c)

#### Task-2 : Lab - Makerchip platfrom
To use Makerchip IDE, you need to visit makerchip website at [http://makerchip.com/](http://makerchip.com/) and launch Makerchip IDE
To access a specific example, please follow these steps:
1) **Navigate to the 'Learn' section**
2) **Click on 'Examples'**
3) **Load 'FGPA Multiplier' Example**

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/b7008e12-b9dc-4dbb-a7f2-fcdf84facfd9)

4) **Load FGPA Multiplier Example**

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/6a9a1ac2-de7f-4402-b979-c77ab2911faf)

#### Task-3 : Lab - Combitional logic
**A) Inverter**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes(On line 16,in place of `//...` type `$out = ! $in;`)**
4) **Compile(Ctrl+E)**

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/bc069194-ee10-400a-8a1f-c86a3424ae10)

**B) XOR Gate**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
$out = ! $in;
$out1 = ($in1 ^ $in2);
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/0d8f1e78-5e59-45a7-ac5c-ff1cefa75dcb)

**C) Vectors**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
$out[4:0] = $in1[3:0] + $in2[3:0];
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/2271ebb8-9c56-427b-899f-c3bea738496c)

**D) Mux without vector & with vectors**
1) **Click on 'Examples'**
2) **Load Default Template**
   
3a) **Go to editor and make changes**
```
$out = $sel ? $in1 : $in2;
```
4a) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/a6420afc-2c40-4e8c-890c-c1d5f24d8e6b)

3b) **Go to editor and make changes**
```
$out[7:0] = $sel ? $in1[7:0] : $in2[7:0];
```
4b) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/b97722f5-73ac-4c4b-ac02-0a4e04ce1220)

**E) Simple Claculator**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$val1[31:0] = $rand1[3:0]; 
$val2[31:0] = $rand2[3:0];
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum);
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/0cb6dd50-4cea-420b-9287-e160c143e42b)

#### Task-4 : Sequential logic 

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/0d548af2-e42f-48fd-9a33-fe47df3775fb)

**A) Fibonacci series**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$fib[31:0] = $reset ? 1 : (>>1$fib + >>2$fib); 
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/0fe24200-ccfd-4d99-9c40-83ecb6dc277c)

**B) Up-Counter**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$num[2:0] = $reset ? 0 : (>>1$num + 1); 
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/272b36d5-3abc-467b-9fac-2494ab5d338e)

**C) Sequential Calculator**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
$val1[31:0] = (>>1$out); 
$val2[31:0] = $rand2[3:0]; 
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum); 
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/a97fcc7c-1ed6-48e2-b1c9-b46d89637dce)

#### Task-5 : Pipelined logic
**A) A simple pipeline through Pythagorean example**
1) **Click on 'Examples'**
2) **Load Default Template**   
3) **Go to editor and make changes**
```
`include "sqrt32.v"
|calc
      @1
         $aa_sq[31:0] = $aa[3:0] * $aa;
         $bb_sq[31:0] = $bb[3:0] * $bb;
      @2
         $cc_sq[31:0] = $aa_sq + $bb_sq;
      @3
         $cc[31:0] = sqrt($cc_sq);
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/5ae27b57-c976-4ceb-b43f-995619ac538e)

**B) Pipeline Implementation**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|comp
      @1
         $err1 = $bad_input || $illegal_op;
      @2
         $err2 = $err1 || $over_flow;
      @3
         $err3 = $div_by_zero || $err2;
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/1c1d7113-0145-4e71-89d1-76731062eaa9)


#### Task-6 : Validity
+ Easier debug
+ Cleaner design
+ Better error checking
+ Automated clock gating

**A) 2 cycle calculator with validity**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $out [31:0] = $reset ? 32'b0 :
                      ($op[1:0] == 2'b00) ? $sum :
                      ($op[1:0] == 2'b01) ? $diff :
                      ($op[1:0] == 2'b10) ? $prod :
                                              $qut ;
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/bd992f12-ba84-4ca9-8460-4f0c94ef1576)

**B) Distance Calculator**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|calc
      @1
         $reset = *reset;
         
      ?$valid
         @1
            $aa_sq[31:0] = $aa[3:0] * $aa;
            $bb_sq[31:0] = $bb[3:0] * $bb;;
         @2
            $cc_sq[31:0] = $aa_sq + $bb_sq;;
         @3
            $cc[31:0] = sqrt($cc_sq);
      @4
         $total_distance[63:0] =
            $reset ? 0 :
            $valid ? >>1$total_distance + $cc :
                     >>1$total_distance;
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/bca945ee-92ae-4e31-a81c-a30536b50caf)

**A) Calulator Memory**
1) **Click on 'Examples'**
2) **Load Default Template**
3) **Go to editor and make changes**
```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $mem[31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b101) ? $val1 : >>2$mem ;
         
         $out [31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b000) ? $sum :
                      ($op[2:0] == 3'b001) ? $diff :
                      ($op[2:0] == 3'b010) ? $prod :
                      ($op[2:0] == 3'b011) ? $qut  :
                      ($op[2:0] == 3'b100) ? >>2$mem : >>2$out ;
```
4) **Compile(Ctrl+E)**
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/7062601b-e0a7-4e9e-80c7-2d34a7a62abc)

[Back to Top](#top)

</details>

<details>
<summary>DAY 4 : Basic RISC-V CPU Micro Architecture</summary>
<br>

# RISC-V Architecture Block Diagram

![image](https://github.com/Pavan2280/RISC-V/assets/131603225/1695d5f6-eab9-4279-9419-b2817800b002)

## Overview
This RISC-V Architecture Block Diagram illustrates the fundamental components and their interactions within a computer system based on the RISC-V instruction set architecture. RISC-V is a modular and customizable architecture, providing a versatile framework for designing processors tailored to specific application requirements.

## Components
1. **CPU (Central Processing Unit)**
   - *Description*: The CPU serves as the core of the RISC-V processor, responsible for executing instructions. It includes multiple stages:
     - Instruction Fetch (IF): Fetches instructions from memory.
     - Instruction Decode (ID): Decodes the fetched instructions.
     - Execution (EX): Performs arithmetic and logic operations.
     - Memory (MEM): Manages data memory access.
     - Write Back (WB): Writes results back to registers.

2. **Instruction Memory**
   - *Description*: This memory component stores the program's instructions that the CPU fetches and executes. It's essential for the program's proper execution.

3. **Data Memory**
   - *Description*: Data Memory stores data used by the CPU during program execution. It is crucial for data manipulation and storage.

4. **Registers**
   - *Description*: Registers are a set of general-purpose storage units used for temporary data storage and manipulation by the CPU. They play a pivotal role in instruction execution.

5. **Control Unit**
   - *Description*: The Control Unit manages control signals and coordinates the activities of the CPU's components, ensuring the proper execution of instructions.

6. **ALU (Arithmetic Logic Unit)**
   - *Description*: The ALU performs arithmetic and logic operations as directed by the CPU's instructions. It is the computational workhorse of the processor.

7. **Instruction Decoder**
   - *Description*: The Instruction Decoder interprets and decodes instructions fetched from memory. It translates instructions into actions for the CPU to execute.

8. **Cache Memory**
   - *Description*: Cache Memory provides fast access to frequently used instructions and data. It helps improve the system's overall performance by reducing memory access times.

9. **Bus Interface**
   - *Description*: The Bus Interface facilitates data transfer between the CPU, memory, and peripherals. It ensures efficient communication within the system.

10. **Peripherals**
    - *Description*: Peripherals are external devices such as input/output controllers, timers, and more. They connect to the CPU, enhancing the system's functionality by allowing interaction with the outside world.

For the consecutive labs, we will use the "RISC-V lab starting point code" from https://github.com/stevehoover/RISC-V_MYTH_Workshop.

Use the following links : [Link for the starter code](https://myth.makerchip.com/sandbox?code_url=https:%2F%2Fraw.githubusercontent.com%2Fstevehoover%2FRISC-V_MYTH_Workshop%2Fmaster%2Frisc-v_shell.tlv#)

All the code files are located within the "DAY4" folder : [Link to DAY4 ](https://github.com/Pavan2280/RISC-V/tree/main/DAY4)

#### Task-1 : Program Counter
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/ee23ca5b-0eaf-43a5-94ee-e992caa385c3)

#### Task-2 : Instruction Fetch
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/7a013f50-0de4-4e51-99ae-61950c45ec13)

#### Task-3 : Instruction Decode
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/7b8a3ee1-d2e8-4cb3-8d73-ea98311150f1)

#### Task-4 : Instruction Decode with validity
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/446d2df0-9793-4b2f-9654-38bbabeac788)

#### Task-5 : Individual Instruction decode
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/02822525-10bf-497d-87af-2306d47ef9a9)

#### Task-6 : Register File Read
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/c6946fc3-2dc0-40b7-adf0-40c1ba37289d)

#### Task-7 : ALU
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/d4402cd0-9ff7-4071-a0f6-b8a71bccb501)

#### Task-8 : Register File Write
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/45f8fea1-7db9-4ede-9c1d-d082f03764cc)

#### Task-9 : Branch Instructions
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/1ec20ce2-3dcf-4a1d-8941-48f3ea3ebaac)

#### Task-10 : Testbench to check functionality
![image](https://github.com/Pavan2280/RISC-V/assets/131603225/e00a3113-f18e-453d-9820-d4327fdf1bd0)

[Back to Top](#top)

</details>

<details>
<summary>DAY 5 : Complete Pipelined RISC-V Micro Architecture </summary>
<br>

[Back to Top](#top)

</details>
