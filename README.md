# Verilog-Playground
Verilog Experiment Area

j1eforth-verilog

Translation of the j1eforth interactive Forth environment for FOMU translated from Silice to Verilog.

Resource usage is considerably reduced:

```
Info: Device utilisation:
Info:            ICESTORM_LC:  2672/ 5280    50%
Info:           ICESTORM_RAM:    18/   30    60%
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
