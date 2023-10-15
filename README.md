![image](https://github.com/Pavan2280/RISC-V/assets/131603225/9a131993-315c-4406-80fb-0da36370b966)

# ASIC Flow Course Assignments - Guided by Kunal Ghosh
# Table of contents
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

</details>

<details>
<summary>DAY 4 : Basic RISC-V CPU Micro Architecture</summary>
<br>

</details>

<details>
<summary>DAY 5 : Complete Pipelined RISC-V Micro Architecture </summary>
<br>

</details>
