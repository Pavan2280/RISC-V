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

**C) Mux without vector & with vectors**
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

#### Task-4 : Sequential logic 
#### Task-5 : Pipelined logic
#### Task-6 : State
#### Task-7 : Hierarchy
