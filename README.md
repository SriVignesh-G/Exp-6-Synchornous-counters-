# Name: Sri Vignesh G
# Ref.No: 23012556 

# Exp-6: Synchornous counters up counter and down counter 
## AIM: 
To implement 3 bit up and down counters and validate functionality.
## Equipments Required:
Hardware Required: PC, Cyclone II , USB flasher
Software Required: Quartus prime
## THEORY 

### UP COUNTER 
The counter is a digital sequential circuit and here it is a 3 bit counter, which simply means it can count from 0 to 7 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.
The Q outputs of each flip-flop will serve as the respective binary bits of the final, three-bit count:
three-bit “Up” Counter

![ex6 up 3bit ](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/01aef94a-5947-477d-9c0f-0ce9966ef9c3)


### DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 3-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
three-bit "Down" Counter

![ex 6 down 3bit](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/b1abfe02-5158-4998-882a-991d1da9861f)



## Procedure
1. Create a new project in Quartus II software.
2. Name the project as uc for upcounter and dc for downcounter.
3. Create a new Verilog HDL file in the project file.
4. Name the module as dc and uc for downcounter and upcounter.
5. Within the module declare input and output variables.
6. Complete the program.
7. End the module.

## PROGRAM 
### UP COUNTER
```
module uc(clk, A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((A[0])&(A[1]))^A[2]);
A[1]=(A[0])^A[1];
A[0]=A[0]^1;
end
endmodule
```
### DOWN COUNTER
```
module dc(clk,A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((~A[0])&(~A[1]))^A[2]);
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule
```

## RTL LOGIC UP COUNTER AND DOWN COUNTER  
### UP COUNTER
![UP RTL](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/c10dcafc-09a7-48d8-9812-fc4f21cb1c10)
### DOWN COUNTER
![down rtl](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/0c1de3df-898d-4615-a517-1c60c5447608)

## TIMING DIGRAMS FOR COUNTER  
### UP COUNTER
![up td](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/e0283351-7f9e-4129-b05a-316b2b059235)
### DOWN COUNTER
![down td](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/d4a1ac80-4851-44de-8ccf-1bc43504a2a2)

## TRUTH TABLE
### UP COUNTER
![image](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/5ea737c6-05ac-40a7-8224-e1af6e2f59a4)


### DOWN COUNTER
![image](https://github.com/SriVignesh-G/Exp-6-Synchornous-counters-/assets/147576510/44ec7227-d932-4923-ab9c-d42740312419)



### RESULTS 
Thus we have verified the truthtable of 3-bit up and down counter using verilog.
