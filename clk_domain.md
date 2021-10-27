# clock relationship with pll_cpu_clk

```
apb_clk <- pll_cpu_clk by apb_clk_en_f
```

```
l2c_data_clk_bank_0_before_occ <- pll_cpu_clk by data_ram_clk_en_bank_0
```


# clk domain

## apb_clk

* x_rmu_top
* x_ct_clint_top
* x_plic_top


## axim_clk_en

## forever_core0_clk

## forever_cpuclk


## forever_jtgclk

wired to *pad_had_jtg_tclk*

* ct_had_common_top




## l2c_data_clk_bank_0
## l2c_tag_clk_bank_0