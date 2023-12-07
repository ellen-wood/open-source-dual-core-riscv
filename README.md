# open-source-dual-core-riscv

This is a collaborative project to develop an Open Source Dual Core RISCV.

Processors based on subservient with its debug interface and register-files in RAM: https://github.com/olofk/serv

We plan to add the Mult/Div extension and the Compressed instruction set extension. Then use UART->WB bridge IP to control upload code and debugging from a single UART. Wouldn't use the official RISCV debug scheme. We can do everything needed with the debug wishbone if we add clock gating.

The idea is to get everything working on SERV first, before trying to upgrade to QERV, which is 4 bit per clock cycle rather than 1 bit, meaning 3x faster and <20% area increase. 4x Higher memory bandwidth. 

https://github.com/olofk/qerv 

https://www.qamcom.com/qamcom-boosts-risc-v/

Resources/References:

Servant - works with SERV and QERV. Reference platform for SERV. Separate memories (SRAM) for register file and for main memory. No debug / upload facility to memory. Memory is 8 bit wide for SERV, 32 bit wide for QERV (to cope with additional bandwidth): https://serv.readthedocs.io/en/latest/servant.html

Subservient - (only works for SERV not QERV). Extra feature #1 vs Servant is combined main memory and register file inside the same RAM. Extra feature #2 is debug interface to upload code via  WB: https://github.com/olofk/subservient/

Wishbone to Bus Protocol - this lets us upload code over UART. Works well. https://zipcpu.com/blog/2017/06/08/simple-wb-master.html 
			
