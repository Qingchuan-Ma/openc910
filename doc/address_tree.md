```
AXI_SRAM:           40'h0000_0000 ~ 40'h01ff_ffff
included in x_f_spsram_large:
mem_addr[24:4] means mem_addr[24:0] address sram space 32 MB


AXI_ERR1:           40'h0200_0000 ~ 40'h0fff_ffff
included in x_f_spsram_32768x128_L:
mem_addr[18:4] means mem_addr[18:0] address err1 space 0.5 MB

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
    S1(mem_ctrl):           40'h1f00_0000 ~ 40'h1f01_ffff
    S3:                 40'h1f02_0000 ~ 40'h1fff_ffff
        x_err_gen


AXI_ERR2:           40'h2000_0000 ~ 40'hffff_ffff
included in x_f_spsram_32768x128_L:
mem_addr[18:4] means mem_addr[18:0] address err1 space 0.5 MB


assign pad_cpu_apb_base = 40'b000_0000; // apb_base is registered
assign sysio_ciu_apb_base[39:0] = {apb_base[12:0], 27'b0};
    
    send to sysio_ciu_apb_base module;
    generate apbif_sel and apbif_addr;
    assign raq_apbif_sel = raq_pop_araddr[ADDRW-1:27] == sysio_ciu_apb_base[ADDRW-1:27];

    `define PLIC_BASE_START  1'b0
    `define CLINT_BASE_START 11'h400
    `define HAD_BASE_START   11'h401
    `define L2PMP_BASE_START 11'h402
    `define RMR_BASE_START   11'h403

    assign sel_plic  = (apbif_addr[26] == `PLIC_BASE_START);
    assign sel_clint = (apbif_addr[26:16] == `CLINT_BASE_START);
    assign sel_had   = (apbif_addr[26:16] == `HAD_BASE_START);
    assign sel_l2pmp = (apbif_addr[26:16] == `L2PMP_BASE_START);
    assign sel_rmr   = (apbif_addr[26:16] == `RMR_BASE_START);

    PLIC:       40'hb000_0000 ~ 40'hb3ff_ffff  (64M)
    CLINT:      40'hb400_0000 ~ 40'hb400_ffff  (64K)
    HAD:        40'hb401_0000   
    L2PMP:      40'hb402_0000   [15:14] select core
    RMR:        40'hb403_0000


assign sysio_xx_apb_base[39:0] = {apb_base[12:0], 27'b0};
    
    send to x_ct_biu_top in x_ct_top_0 module;
    generate biu_cp0_apb_base;

    assign mapbaddr_value[63:0] = {{24{biu_cp0_apb_base[39]}}, biu_cp0_apb_base[39:0]};

    C910 extended register MAPBADDR
```
