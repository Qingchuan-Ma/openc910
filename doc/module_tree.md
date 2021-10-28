# soc struct

```
|--x_soc
    |--x_axi_interconnect
    |--x_axi_fifo
        |--x_counter_entry0
        |--...
        |--x_counter_entry7
        |--x_axi_fifo_entry0 (smart_run/logical/axi/axi_fifo_entry.v)
        |--...
        |--x_axi_fifo_entry7
    |--x_axi_slave128 (smart_run/logical/axi/axi_slave128.v)
        |--x_f_spsram_large (smart_run/logical/mem/f_spsram_large.v)
            |--ram0 (smart_run/logical/mem/ram.v)
                |--ADDR_WIDTH = 21 (2 MB space), total 32 MB
                |--1 ram (data 8 bit, addr 21 bit)
                |--16 ram (once addr read/write 16*8(128) bit (4 words))
                |--so only send addr mem_addr[24:4]
            |--ram15
    |--x_axi_err (smart_run/logical/axi/axi_err128.v)
        |--x_f_spsram_32768x128_L (smart_run/logical/mem/|--f_spsram_32768x128.v)
            |--ram0
                |--ADDR_WIDTH = 15 (32 KB space), total 0.5 MB
                |--so only send addr mem_addr[18:4]
            |--ram15
    |--x_axi_err1
        |--x_f_spsram_32768x128_L (smart_run/logical/mem/|--f_spsram_32768x128.v)
            |--ram0
                |--ADDR_WIDTH = 15 (32 KB space), total 0.5 MB
                |--so only send addr mem_addr[18:4]
            |--ram15
    |--x_axi2ahb (smart_run/logical/axi/axi2ahb.v)
    |--x_ahb (smart_run/logical/ahb/ahb.v)
    |--x_mem_ctrl (smart_run/logical/mem/mem_ctrl.v)
        |--ram0 (smart_run/logical/mem/ram.v)
        |--...
        |--ram15
    |--x_apb (smart_run/logical/apb/apb.v)
        |--x_ahb2apb (smart_run/logical/ahb/ahb2apb.v)
        |--x_apb_bridge (smart_run/logical/apb/apb_bridge.v)
        |--x_uart (smart_run/logical/uart/uart.v)
            |--x_uart_apb_reg
            |--x_uart_baud_gen
            |--x_uart_ctrl
            |--x_uart_trans
            |--x_uart_receive
        |--x_timer (smart_run/logical/common/timer.v)
            |--timer_1 (smart_run/logical/common/timer.v)
            |--...
            |--timer_4
        |--x_stimer
            |--timer_1
            |--...
            |--timer_4
        |--x_gpio (smart_run/logical/gpio/gpio.v)
            |--x_gpio_apbif
            |--x_gpio_ctrl
        |--x_clk_gen (smart_run/logical/common/clk_gen.v)
        |--x_pmu (smart_run/logical/pmu/pmu.v)
            |--x_cpu2pmu_sync1
            |--x_cpu2pmu_sync2
            |--x_tap2_sm
            |--x_jtag2pmu_sync
    |--x_err_gen (smart_run/logical/common/err_gen.v)
    |--x_cpu_sub_system_axi (smart_run/logical/common/cpu_sub_system_axi.v)
        |--wid_for_axi4 （smart_run/logical/common/wid_for_axi4.v）
            |--x_wid_entry_0 (smart_run/logical/common/wid_entry.v)
            |--...
            |--x_wid_entry_31
        |--x_rv_integration_platform (smart_run/logical/common/rv_integration_platform.v)
            |--x_cpu_top (C910_RTL_FACTORY/gen_rtl/cpu/rtl/openC910.v)

```

# cpu struct

```
|--x_cpu_top
    |--x_rmu_top
    |--x_ct_top_0
    |--x_ct_top_1
    |--x_ct_ciu_top
        |--x_ct_piu0_other_io
        |--x_ct_piu1_other_io
        |--x_ct_piu2_other_io
        |--x_ct_piu3_other_io
        |--x_ct_piu0_top
        |--x_ct_piu1_top
        |--x_ct_piu2_top_dummy
        |--x_ct_piu3_top_dummy
        |--x_ct_piu4_top_dummy
        |--x_ct_ciu_bmbif
        |--x_ct_ciu_snb_0
        |--x_ct_ciu_snb_1
        |--x_ct_ciu_vb
        |--x_ct_ciu_ebiuif
        |--x_ct_ciu_l2cif
        |--x_ct_ciu_ctcq
        |--x_ct_ciu_ncq
        |--x_ct_ebiu_top
        |--x_ct_ciu_regs
        |--x_ct_ciu_apbif
            |--x_apbif_gated_clk
        |--x_ciu_top_gated_clk
    |--x_ct_l2c_top
        |--x_ct_l2c_sub_bank_0
        |--x_ct_l2c_sub_bank_1
        |--x_ct_l2c_prefetch
    |--x_ct_clint_top
        |--x_ct_clint_func
    |--x_plic_top
        |--x_csky_apb_1tox_matrix
        |--x_plic_sec_busif
        |--x_plic_ctrl
        |--x_plic_hreg_busif
        |--x_plic_kid_busif
        |--x_plic_hart_arb
        |--x_plic_cov
    |--x_ct_mp_rst_top
    |--x_ct_mp_clk_top
        |--apb_clk_buf
        |--x_data_bist_gated_clk
        |--data_bank0_clk_buf
        |--data_bank1_clk_buf
        |--tag_bank0_clk_buf
        |--tag_bank1_clk_buf
    |--x_ct_sysio_top
        |--x_ct_sysio_in_gated_clk
        |--x_ct_sysio_core0
        |--x_ct_sysio_core1
    |--x_ct_had_common_top
        |--x_ct_had_sm
        |--x_ct_had_io
        |--x_ct_had_serial
        |--x_ct_had_ir
        |--x_ct_had_etm
        |--x_ct_had_common_regs
        |--x_ct_had_common_dbg_info
```


# core struct

```
|--x_ct_top_0
    |--x_ct_core
    |--x_ct_mmu_top
        |--x_utlb_gateclk
        |--x_ct_mmu_iutlb
        |--x_ct_mmu_dutlb
        |--x_ct_mmu_regs
        |--x_ct_mmu_tlboper
        |--x_ct_mmu_arb
        |--x_ct_mmu_jtlb
        |--x_ct_mmu_ptw
        |--x_ct_mmu_sysmap_0
        |--...
        |--x_ct_mmu_sysmap_4
    |--x_ct_pmp_top
        |--x_pmp_gated_clk
        |--x_ct_pmp_regs
        |--x_ct_pmp_acc0
        |--...
        |--x_ct_pmp_acc4
    |--x_ct_biu_top
        |--x_ct_biu_req_arbiter
        |--x_ct_biu_read_channel
        |--x_ct_biu_write_channel
        |--x_ct_biu_snoop_channel
        |--x_ct_biu_lowpower
        |--x_ct_biu_csr_req_arbiter
        |--x_ct_biu_other_io_sync
    |--x_ct_had_private_top
        |--x_ct_had_bkpta
        |--x_ct_had_bkptb
        |--x_ct_had_ctrl
        |--x_ct_had_ddc_ctrl
        |--x_ct_had_ddc_dp
        |--x_ct_had_pcfifo
        |--x_ct_had_regs
        |--x_ct_had_trace
        |--x_ct_had_event
        |--x_ct_had_dbg_info
        |--x_ct_had_nirv_bkpt
        |--x_ct_had_private_ir
    |--x_ct_hpcp_top
        |--x_ct_hpcp_adder_sel_3
        |--...
        |--x_ct_hpcp_adder_sel_18
        |--x_ct_hpcp_cntinten_0
        |--...
        |--x_ct_hpcp_cntinten_31
        |--x_ct_hpcp_cntof_0
        |--...
        |--x_ct_hpcp_cntof_31
        |--x_hpcp_mhpmevent3
        |--...
        |--x_hpcp_mhpmevent18
        |--x_hpcp_mcycle
        |--x_hpcp_minstret
        |--x_hpcp_mhpmcnt3
        |--x_hpcp_mhpmcnt18
    |--x_ct_rst_top
    |--x_ct_clk_top
        |--core_clk_buf
```


## ct_core
```
|--x_ct_core
    |--x_ct_ifu_top
        |--x_ct_ifu_addrgen
        |--x_ct_ifu_bht
        |--x_ct_ifu_btb
        |--x_ct_ifu_l0_btb
        |--x_ct_ifu_sfp
        |--x_ct_ifu_ibctrl
        |--x_ct_ifu_ibdp
        |--x_ct_ifu_ibuf
        |--x_ct_ifu_icache_if
        |--x_ct_ifu_ifctrl
        |--x_ct_ifu_ifdp
        |--x_ct_ifu_ind_btb
        |--x_ct_ifu_ipb
        |--x_ct_ifu_ipctrl
        |--x_ct_ifu_ipdp
        |--x_ct_ifu_l1_refill
        |--x_ct_ifu_lbuf
        |--x_ct_ifu_pcfifo_if
        |--x_ct_ifu_pcgen
        |--x_ct_ifu_ras
        |--x_ct_ifu_vector
        |--x_ct_ifu_debug
    |--x_ct_idu_top
        |--x_ct_idu_id_ctrl
        |--x_ct_idu_id_dp
        |--x_ct_idu_id_fence
        |--x_ct_idu_ir_ctrl
        |--x_ct_idu_ir_dp
        |--x_ct_idu_ir_rt
        |--x_ct_idu_ir_frt
        |--x_ct_idu_ir_vrt
        |--x_ct_idu_is_ctrl
        |--x_ct_idu_is_dp
        |--x_ct_idu_is_aiq0
        |--x_ct_idu_is_aiq1
        |--x_ct_idu_is_biq
        |--x_ct_idu_is_lsiq
        |--x_ct_idu_is_sdiq
        |--x_ct_idu_is_viq0
        |--x_ct_idu_is_viq1
        |--x_ct_idu_rf_ctrl
        |--x_ct_idu_rf_dp
        |--x_ct_idu_rf_fwd
        |--x_ct_idu_rf_prf_pregfile
        |--x_ct_idu_rf_prf_eregfile
        |--x_ct_idu_rf_prf_vregfile_fr
        |--x_ct_idu_rf_prf_vregfile_vr0
        |--x_ct_idu_rf_prf_vregfile_vr1
    |--x_ct_iu_top
    |--x_ct_vfpu_top
    |--x_ct_lsu_top
    |--x_ct_cp0_top
    |--x_ct_rtu_top
```


# axi read address channel:

```
cpu->x_axi_fifo->x_axi_interconnect/x_axi_slave128/x_axi_err/x_axi2ahb/x_axi_err1

```

```
x_axi_interconnect, select:
    sram:   x_axi_slave128
    err1:   x_axi_err
    ahb:    x_axi2ahb -> x_ahb (generate signal biu_pad_haddr)
    err2:   x_axi_err1
by signal fifo_pad_araddr
```

```
x_ahb, select:
    s1:     x_mem_ctrl
    s2:     x_apb -> ahb2apb (generate signal apb_haddr)
    s3:     x_err_gen
by signal biu_pad_haddr
```

```
x_apb_bridge, select:
    ps1:    x_uart
    ps2:    x_timer
    ps3:    x_pmu
    ps4:    intc
    ps5:    x_gpio
    ps6:    x_clk_gen
    ps7:    x_stimer
    ps8:    hang
by apb_haddr
```

# diagram


```




```