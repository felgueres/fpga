### Notes from learning Verilog on a FPGA

Opensource toolchain: https://projectf.io/posts/building-ice40-fpga-toolchain/

Synthesize Verilog to Hardware mapping  
```bash
yosys -p "read_verilog test.v; synth_ice40 -json test.json"
```

Place and route design  
```bash
nextpnr-ice40 --hx1k --pcf Go_Board_Constraints.pcf --package vq100 --json test.json --asc test.txt
```

Generate binary from design  
```bash
icepack test.txt test.bin
```

Program design into chip  
```bash
sudo iceprog test.bin
```
