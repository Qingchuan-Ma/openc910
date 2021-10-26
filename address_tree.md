
AXI_SRAM:           40'h0000_0000 ~ 40'h01ff_ffff
included in x_f_spsram_large:
mem_addr[24:4] means mem_addr[24:0] address sram space


AXI_ERR1:           40'h0200_0000 ~ 40'h0fff_ffff
included in x_f_spsram_32768x128_L:
mem_addr[18:4] means mem_addr[18:0] address err1 space

AHB:                40'h1000_0000 ~ 40'h1fff_ffff
    S2:                 40'h1000_0000 ~ 40'h1eff_ffff
        PS1(uart):          40'h1001_5000 ~ 40'h1001_5fff
        PS2(timer):         40'h1001_1000 ~ 40'h1001_1fff
        PS3(pmu):           40'h1001_6000 ~ 40'h1001_6fff
        PS4(intc):          40'h1001_0000 ~ 40'h1001_0fff, hang
        PS5(gpio):          40'h1001_9000 ~ 40'h1001_9fff
        PS6(clk_gen):       40'h1001_7000 ~ 40'h1001_7fff
        PS7(stimer):        40'h1001_8000 ~ 40'h1001_8fff
        PS8:                40'h1001_A000 ~ 40'h1001_Afff, hang
    S1:                 40'h1f00_0000 ~ 40'h1f01_ffff
    S3:                 40'h1f02_0000 ~ 40'h1fff_ffff
        x_err_gen


AXI_ERR2:           40'h2000_0000 ~ 40'hff_ffff_ffff
included in x_f_spsram_32768x128_L:
mem_addr[18:4] means mem_addr[18:0] address err1 space

