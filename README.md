# RIDL-drive modeling project

## Content

``` txt
.
├── README.md
├── data
│   ├── processed
│   │   ├── RIDL-drive_discrete
│   │   ├── RIDL-drive_heterozygotes_survival
│   │   ├── RIDL-drive_mosquito
│   │   ├── RIDL-drive_mosquito_LDGR
│   │   ├── RIDL-drive_mosquito_fitness
│   │   ├── RIDL-drive_resistance
│   │   ├── RIDL_mosquito_LDGR
│   │   ├── RIDL_mosquito_fitness
│   │   ├── SIT_discrete
│   │   ├── SIT_mosquito
│   │   ├── SIT_mosquito_LDGR
│   │   └── SIT_mosquito_fitness
│   └── raw
│       ├── RIDL-drive_discrete
│       ├── RIDL-drive_heterozygotes_survival
│       ├── RIDL-drive_mosquito
│       ├── RIDL-drive_mosquito_LDGR
│       ├── RIDL-drive_mosquito_fitness
│       ├── RIDL-drive_resistance
│       ├── RIDL_mosquito_LDGR
│       ├── RIDL_mosquito_fitness
│       ├── SIT_discrete
│       ├── SIT_mosquito
│       ├── SIT_mosquito_LDGR
│       └── SIT_mosquito_fitness
└── models
    ├── discrete.slim
    ├── mosquito.slim
    └── mosquito_het_survival.slim
```

## SLiM Model description

- `discrete.slim`: panmictic discrete generation model
- `mosquito.slim`: basic panmictic mosquito (overlapping generation) model
- `mosquito_het_survival.slim`: panmictic mosquito (overlapping generation) model considering the heterozygotes survival rate

## Data description

The `*.csv` files in the raw data adhere to the following naming convention:

```txt
[Transgene type]_[Param 1]-[Param 1 value]-[Param 2]-[Param 2 value]-..._[Repetition number].csv
```

where:

- `[Transgene type]` indicates the type of transgene element applied in the simulation. It should be `RIDL-drive`, `RIDL`, or `SIT`.
- `[Param]`s and `[Param value]`s indicate some important parameters and their values in the simulation. Here are some `[Param]`s:
  - `drop`: drop ratio (a positive float number in)
  - `eff`: drive efficiency (a float number in $[0.0,1.0]$)
  - `fit`: drive (RIDL/SIT) homozygotes fitness (a float number in $[0.5,1.0]$)
  - `ldgr`: low-density growth rate (a float positive number)
  - `r2`: germline resistance rate (a float number in $[0.0,0.5]$)
  - `hets`: heterozygotes survival rate (a float number in $[0.0,0.5]$)
  - `curve`: density-dependent growth curve type ( `concave` / `linear` / `convex` )
  - `type`: rescue drive type ( `normal` / `haplolethal` / `recessivelethal` )
- `[Repetition number]` is a positive integer (1~20), representing one of the 20 simulations with identical parameters.

## Errata

- There is a `fertile_female_size` column in `*.csv` files from some mosquito model simulations. The values are always 1 due to a wrong output. These columns are not used in our project, because all females are fertile in the mosquito model. The `female_size` columns give the total number (and also, the correct number of fertile ones) of females. This error is fixed in the current version of models.
