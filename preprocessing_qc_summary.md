# Preprocessing QC Summary

## Overall Status

- Generated on: `2026-04-20T23:53:07.697418+00:00`
- Crime source month columns available: `167` (`201004` to `202402`)
- Selected target months: `201903` to `202402` (`60` months)
- Verified burglary minor categories: `BURGLARY BUSINESS AND COMMUNITY, DOMESTIC BURGLARY, RES BURGLARY OF A HOME, RES BURGLARY OF UNCONNECTED BUILDING`

## Raw-Data Quality

- Raw crime file rows: `127,017`
- Raw crime duplicate `LSOA Code + Major Category + Minor Category` keys: `0`
- Selected crime month cells with null values: `0`
- Selected crime month cells with negative values: `0`
- Census `2021` sheet coverage: each of the 6 workbooks has `4,994` unique `LSOA code` rows, with `0` duplicate keys and `0` null keys
- IMD file coverage: `32,844` unique `LSOA code (2011)` rows, with `0` null keys
- Exact-fit lookup coverage: non-null `LSOA11CD` and `LSOA21CD` keys, with full `LSOA21CD` coverage for the `4,988` crime-covered LSOAs

## Analysis Universe Note

- The final exported analysis universe is the `4,988` crime-covered LSOAs present in the Feb 2024 crime snapshot.
- The `2021` Census workbooks contain `4,994` LSOAs because they include `6` City of London rows that are absent from the current crime snapshot.
- Those `6` Census-only City of London rows are excluded by design as a source-coverage difference, not treated as a preprocessing error.

## Row Counts

| Output | Rows |
| --- | --- |
| crime_burglary_lsoa2021_base.csv | 4988 |
| census_lsoa2021_feature_components.csv | 4988 |
| imd2019_lsoa2021_features.csv | 4988 |
| lsoa2021_burglary_analysis_master.csv | 4988 |
| lsoa2021_burglary_model_input_v1.csv | 4988 |

## Coverage Checks

- Crime -> census direct join coverage: `4988 / 4988`
- Crime -> exact-fit / IMD coverage: `4988 / 4988`
- IMD coverage after reconciliation: matched `4988`, unmatched `0`, percentage matched `100.00%`
- 2021 LSOAs requiring multi-source IMD aggregation: `22`

## Uniqueness Checks

| Check | Count |
| --- | --- |
| crime_base duplicate lsoa_code_2021 | 0 |
| census duplicate lsoa_code_2021 | 0 |
| imd duplicate lsoa_code_2021 | 0 |
| analysis_master duplicate lsoa_code_2021 | 0 |
| model_input duplicate lsoa_code_2021 | 0 |

## Value Checks

| Share Field | Out-of-range values |
| --- | --- |
| share_age_15_24 | 0 |
| share_age_25_34 | 0 |
| share_age_65_plus | 0 |
| share_owned_mortgage_or_shared | 0 |
| share_social_rented | 0 |
| share_private_rented | 0 |
| share_purpose_built_flat | 0 |
| share_converted_or_shared_household | 0 |
| share_all_flats | 0 |
| share_unemployed_16plus | 0 |
| share_no_qualifications | 0 |
| share_level4_plus | 0 |
| share_higher_managerial_professional | 0 |

## Missingness for Retained Explanatory Features

| Feature | Missing values |
| --- | --- |
| share_age_15_24 | 0 |
| share_age_25_34 | 0 |
| share_age_65_plus | 0 |
| share_owned_mortgage_or_shared | 0 |
| share_social_rented | 0 |
| share_private_rented | 0 |
| share_purpose_built_flat | 0 |
| share_converted_or_shared_household | 0 |
| share_unemployed_16plus | 0 |
| share_no_qualifications | 0 |
| share_level4_plus | 0 |
| share_higher_managerial_professional | 0 |
| imd_income_score_2019 | 0 |
| imd_employment_score_2019 | 0 |
| imd_education_score_2019 | 0 |
| imd_health_score_2019 | 0 |
| imd_barriers_score_2019 | 0 |
| imd_living_environment_score_2019 | 0 |

## Denominator Events

| Source table | Derived field | Zero denominator rows | Missing denominator rows |
| --- | --- | --- | --- |
| Age workbook | share_age_15_24 | 0 | 0 |
| Age workbook | share_age_25_34 | 0 | 0 |
| Age workbook | share_age_65_plus | 0 | 0 |
| Tenure workbook | share_owned_mortgage_or_shared | 0 | 0 |
| Tenure workbook | share_social_rented | 0 | 0 |
| Tenure workbook | share_private_rented | 0 | 0 |
| Accommodation workbook | share_purpose_built_flat | 0 | 0 |
| Accommodation workbook | share_converted_or_shared_household | 0 | 0 |
| Accommodation workbook | share_all_flats | 0 | 0 |
| Economic activity workbook | share_unemployed_16plus | 0 | 0 |
| Qualifications workbook | share_no_qualifications | 0 | 0 |
| Qualifications workbook | share_level4_plus | 0 | 0 |
| NSSEC workbook | share_higher_managerial_professional | 0 | 0 |
| Analysis master | burglary_rate_per_1000 | 0 | 0 |

## Screening Decisions

### Retained Predictors

| Field | Decision |
| --- | --- |
| share_age_15_24 | Retained v1 predictor |
| share_age_25_34 | Retained v1 predictor |
| share_age_65_plus | Retained v1 predictor |
| share_owned_mortgage_or_shared | Retained v1 predictor |
| share_social_rented | Retained v1 predictor |
| share_private_rented | Retained v1 predictor |
| share_purpose_built_flat | Retained v1 predictor |
| share_converted_or_shared_household | Retained v1 predictor |
| share_unemployed_16plus | Retained v1 predictor |
| share_no_qualifications | Retained v1 predictor |
| share_level4_plus | Retained v1 predictor |
| share_higher_managerial_professional | Retained v1 predictor |
| imd_income_score_2019 | Retained v1 predictor |
| imd_employment_score_2019 | Retained v1 predictor |
| imd_education_score_2019 | Retained v1 predictor |
| imd_health_score_2019 | Retained v1 predictor |
| imd_barriers_score_2019 | Retained v1 predictor |
| imd_living_environment_score_2019 | Retained v1 predictor |

### Audit-only Fields

| Field | Decision |
| --- | --- |
| lsoa_code_2021 | Audit-only field |
| lsoa_name | Audit-only field |
| local_authority_code | Audit-only field |
| local_authority_name | Audit-only field |
| burglary_5y_sum | Audit-only field |
| burglary_annualised | Audit-only field |
| population_total_2021 | Audit-only field |
| households_total_2021 | Audit-only field |
| residents_16_plus_total | Audit-only field |
| qualifications_16_plus_total | Audit-only field |
| nssec_16_plus_total | Audit-only field |

### Excluded Fields and Reasons

| Field | Reason |
| --- | --- |
| share_all_flats | Derived but excluded from v1 because it overlaps with flat subcomponents. |
| Index of Multiple Deprivation (IMD) Score | Excluded because the overall IMD score embeds the crime domain. |
| Crime Score | Excluded to avoid leakage and circularity with the burglary target. |
| IMD ranks / deciles | Excluded because continuous scores are more informative than ordinal summaries. |
| burglary_5y_sum | Audit-only target construction field, not the final rate outcome. |
| burglary_annualised | Audit-only target construction field, not the final rate outcome. |
| population_total_2021 | Rate denominator and audit field, not a v1 predictor. |
| households_total_2021 | Housing share denominator retained for audit only. |
| residents_16_plus_total | Economic activity denominator retained for audit only. |
| qualifications_16_plus_total | Qualifications denominator retained for audit only. |
| nssec_16_plus_total | NS-SEC denominator retained for audit only. |
| lsoa_name | Label retained for audit and mapping only. |
| local_authority_code | Administrative identifier retained for audit and mapping only. |
| local_authority_name | Administrative label retained for audit and mapping only. |



