# Verilog-Playground
Verilog Experiment Area

## j1eforth-verilog

Translation of the j1eforth interactive Forth environment for FOMU translated from Silice to Verilog.

### Resources on the FOMU
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
