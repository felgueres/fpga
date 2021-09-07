Workflow notes

Opensource toolchain: https://projectf.io/posts/building-ice40-fpga-toolchain/

Synthesize Verilog to Hardware mapping  
$ yosys -p "read_verilog test.v; synth_ice40 -json test.json"

Place and route design  
$ nextpnr-ice40 --hx1k --pcf Go_Board_Constraints.pcf --package vq100 --json test.json --asc test.txt

Generate binary from design  
$ icepack test.txt test.bin

Program design into chip  
$ sudo iceprog test.bin
