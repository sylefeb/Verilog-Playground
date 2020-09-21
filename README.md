# Verilog-Playground
My Verilog Coding Experimental Area

## j1eforth-verilog for FOMU

Translation of the j1eforth interactive Forth environment for FOMU (https://www.crowdsupply.com/sutajio-kosagi/fomu documentation https://workshop.fomu.im/en/latest/) translated from Silice to Verilog.

The original J1 CPU (https://www.excamera.com/sphinx/fpga-j1.html explanatory paper https://www.excamera.com/files/j1.pdf) along with the j1eforth interactive Forth environment (https://github.com/samawati/j1eforth) was written for an FPGA with access to 16384 x 16bit (256kbit) dual port single cycle block ram, whereas the FOMU has 120kbit of block ram. It does however have 1024kbit of single port ram (65536 x 16bit), which is more than sufficient for j1eforth, but it has 2 cycle latency.

j1eforth for FOMU was originally coded in Silice (https://github.com/sylefeb/Silice) due to my limited (i.e. NO) FPGA programming experience. Once this design was working, especially the timings to access the single port ram, I translated it ack to verilog, as an educational experience for myself.

For communicating via a terminal the tinyfpga_bx_usbserial (https://github.com/stef/nb-fomu-hw) was implemented to provide a 115200 baud UART.

## Using j1eforth-verilog on the FOMU

Download the source code from this repository. Ensure that you have the required toolchain installed. Compile (on Linux) with `./fomu_hacker_USB_SPRAM.sh` within the source directory.

Or download the precompiled `build.dfu` file from this repository.

Upload the compiled, or downloaded bitstream to your FOMU with `dfu-util -D build.dfu` and connect via your chosen terminal, for minicom `minicom -D /dev/ttyACM0` (ACM0 may need replacing with an appropriate number on your machine).

## Resources on the FOMU
Resource usage is considerably reduced compared to Silice https://github.com/sylefeb/Silice @sylefeb is investigating:

```
Info: Device utilisation:
Info:            ICESTORM_LC:  2420/ 5280    45%
Info:           ICESTORM_RAM:    19/   30    63%
Info:                  SB_IO:    12/   96    12%
Info:                  SB_GB:     8/    8   100%
Info:           ICESTORM_PLL:     0/    1     0%
Info:            SB_WARMBOOT:     0/    1     0%
Info:           ICESTORM_DSP:     0/    8     0%
Info:         ICESTORM_HFOSC:     0/    1     0%
Info:         ICESTORM_LFOSC:     0/    1     0%
Info:                 SB_I2C:     0/    2     0%
Info:                 SB_SPI:     0/    2     0%
Info:                 IO_I3C:     0/    2     0%
Info:            SB_LEDDA_IP:     0/    1     0%
Info:            SB_RGBA_DRV:     1/    1   100%
Info:         ICESTORM_SPRAM:     4/    4   100%
```

The J1 CPU adds 4 new instructions, 0= 0<> <> 1+ and these have been incorporated into the j1eforth environment as a test.

### Memory Map
* 0000 - 3fff Program code and data
* 4000 - 7fff RAM (written to with `addr !`, read by `addr @`
* f000 UART input/output (best to leave to j1eforth to operate via IN/OUT buffers)
* f001 UART Status (bit 1 = TX buffer full, bit 0 = RX character available, best to leave to h1eforth to operate via IN/OUT buffers)
* f002 RGB LED input/output
* f003 BUTTONS input

### Forth Words to try
* `cold` reset
* `words` list known Forth words
* `cr` output a carriage return
* `2a emit` output a * (character 2a (hex) 42 (decimal)
* `decimal` use decimal notation
* `hex` use hexadecimal notation

![j1eforth on FOMU](j1eforth-verilog.png)
