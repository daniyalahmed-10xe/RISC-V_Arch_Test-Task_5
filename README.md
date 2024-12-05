# <center> RISC-V Arch Test </center>

## *<center> Implementation of Task 5 </center>*

#### Question Statement:

###### *Write a test for VM in spike/sail (Virtual Memory task - SV32)*

1. Pre-requisites:
	- Read RISCV privileged architecture spec for Virtrual Memory.
	- Read about mstatus, mtvec, mcause, mepc CSRs and different operating modes (Machine, Supervisor and User modes).

2. Write an assembly function to setup the page table entry, Function must have following arguments:
	- Virtual address.
	- Physical address.
	- Permissions.
	- level: Either 0 or 1. This sets the PTE specified by the level parameter.

3. Write assembly test:
	- Start in M mode. Setup the PTEs for Instruction memory address (or DMem: load/store addresses).
	- Setup your trap-handler to handle the exception appropriately.
	- Set satp appropriately to enable virtualization with SV32 translation scheme.
	- Goto S/U mode by mret such that mepc contain the Virtual address. (Translation must be enabled).
	- Try accessing the addresses with and without PTE (RWX) permissions: check the CSRs (mstatus, mcause, mepc) for the corresponding page-fault.

#### Build & Run:

###### *Compile Assembly File to Elf:*

```shell
riscv64-unknown-elf-gcc -march=rv32g -mabi=ilp32 -nostdlib -T link.ld task5.S -o test.elf
```
###### *Create a Disassembly:*

```shell
riscv64-unknown-elf-objdump -D test.elf > test.disass
```

###### *Simulate on Spike & Generate Logfile:*

```shell
spike --isa=rv32gc -l --log-commits test.elf 1> spike.out 2> spike.log
```

###### *Simulate on Sail & Generate Logfile:*

```shell
riscv_sim_RV32 test.elf --trace=step 2> sail.out 1> sail.log
```

#### Documentation:

###### *Source Code Available at:*
-	<span style = 
			"color: rgb(255, 64, 92);
			background: rgb(228, 228, 228);
			padding: 4px 12px;
			border-radius: 10px"
		> /Code/task5.S
	</span>

###### *Log Files Available at:*
-	<span style = 
			"color: rgb(255, 64, 92);
			background: rgb(228, 228, 228);
			padding: 4px 12px;
			border-radius: 10px"
		> /Code/spike.log
	</span>
-	<span style = 
			"color: rgb(255, 64, 92);
			background: rgb(228, 228, 228);
			padding: 4px 12px;
			border-radius: 10px"
		> /Code/sail.log
	</span>

###### *Report Available at:*
-	<span style = 
			"color: rgb(255, 64, 92);
			background: rgb(228, 228, 228);
			padding: 4px 12px;
			border-radius: 10px"
		> /Report/RISC-V_Arch_Test_Task_5_Report.docx
	</span>

###### *Output Screenshots Available at:*
-	<span style = 
			"color: rgb(255, 64, 92);
			background: rgb(228, 228, 228);
			padding: 4px 12px;
			border-radius: 10px"
		> /Screenshots
	</span>