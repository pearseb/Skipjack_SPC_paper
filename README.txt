
First, I prepare the SEAPODYM data...
 produces:
  - absolute_values_SEAPODYM_WCPO.txt
  - anomalous_values_SEAPODYM_WCPO.txt
 using 
  - "prepare_for_gam_skipjack_SEAPODYMforcing.Rmd" 
 which reads:
  - skipjack_biomass_by_age.nc
  - forcings/ipo_jra55np_1x30d_sst_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_mld_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_zeu_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_pp75_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_uo_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_vo_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_T_L1_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_T_L2_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_T_L3_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_O2_L1_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_O2_L2_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_O2_L3_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_U_L1_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_U_L2_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_U_L3_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_V_L1_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_V_L2_1958_2022.nc
  - forcings/ipo_jra55np_1x30d_V_L3_1958_2022.nc

This is done on my local machine because the standard R packages on Gadi do not have netcdf and I need to read netCDFs in.
After producing these two files, upload them to Gadi at /g/data/es60/SEAPODYM/pearse_GAMs/


Second, I process all the forcings into their respective IMFs on the ARE on Gadi with ipython using the pyEMD package...
This step takes many hours, days...

   produces:
    - SEAPODYM_imfs_sst_CEEMDAN.nc
    - SEAPODYM_imfs_mld_CEEMDAN.nc
    - SEAPODYM_imfs_zeu_CEEMDAN.nc
    - SEAPODYM_imfs_pp_CEEMDAN.nc
    - SEAPODYM_imfs_pp75_CEEMDAN.nc
    - SEAPODYM_imfs_uo_CEEMDAN.nc
    - SEAPODYM_imfs_vo_CEEMDAN.nc
    - SEAPODYM_imfs_T_L1_CEEMDAN.nc
    - SEAPODYM_imfs_T_L2_CEEMDAN.nc
    - SEAPODYM_imfs_T_L3_CEEMDAN.nc
    - SEAPODYM_imfs_O2_L1_CEEMDAN.nc
    - SEAPODYM_imfs_O2_L2_CEEMDAN.nc
    - SEAPODYM_imfs_O2_L3_CEEMDAN.nc
    - SEAPODYM_imfs_U_L1_CEEMDAN.nc
    - SEAPODYM_imfs_U_L2_CEEMDAN.nc
    - SEAPODYM_imfs_U_L3_CEEMDAN.nc
    - SEAPODYM_imfs_V_L1_CEEMDAN.nc
    - SEAPODYM_imfs_V_L2_CEEMDAN.nc
    - SEAPODYM_imfs_V_L3_CEEMDAN.nc
   using:
    - decomposition.ipynb
   which reads:
    - forcings_netCDF/ipo_jra55np_1x30d_sst_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_mld_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_zeu_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_pp_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_pp75_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_uo_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_vo_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_T_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_T_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_T_L3_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_O2_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_O2_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_O2_L3_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L3_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_V_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_V_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_V_L3_1958_2022.nc


Third, I prepare the forcings for reading into R on Gadi...

   produces:
    - forcings_without_IMFs_months.csv
    - forcings_without_IMFs_seasons.csv
    - Nauru_SST_IMF_decomposition.png
    - IMFs_correlation_sst_mld_zeu_pp75_uo_vo.png
    - IMFs_correlation_TL1_TL2_TL3_O2L1_O2L2_O2L3.png
    - IMFs_correlation_UL1_UL2_UL3_VL1_VL2_VL3.png
    - STD_of_key_predictors.png
   using:
    - prepare_IMFs_for_GAMs.ipynb 
   which reads:
    - forcings_netCDF/ipo_jra55np_1x30d_sst_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_mld_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_zeu_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_pp_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_pp75_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_uo_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_vo_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_T_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_T_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_T_L3_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_O2_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_O2_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_O2_L3_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L3_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_V_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_V_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_V_L3_1958_2022.nc
    - SEAPODYM_imfs_sst_CEEMDAN.nc
    - SEAPODYM_imfs_mld_CEEMDAN.nc
    - SEAPODYM_imfs_zeu_CEEMDAN.nc
    - SEAPODYM_imfs_pp_CEEMDAN.nc
    - SEAPODYM_imfs_pp75_CEEMDAN.nc
    - SEAPODYM_imfs_uo_CEEMDAN.nc
    - SEAPODYM_imfs_vo_CEEMDAN.nc
    - SEAPODYM_imfs_T_L1_CEEMDAN.nc
    - SEAPODYM_imfs_T_L2_CEEMDAN.nc
    - SEAPODYM_imfs_T_L3_CEEMDAN.nc
    - SEAPODYM_imfs_O2_L1_CEEMDAN.nc
    - SEAPODYM_imfs_O2_L2_CEEMDAN.nc
    - SEAPODYM_imfs_O2_L3_CEEMDAN.nc
    - SEAPODYM_imfs_U_L1_CEEMDAN.nc
    - SEAPODYM_imfs_U_L2_CEEMDAN.nc
    - SEAPODYM_imfs_U_L3_CEEMDAN.nc
    - SEAPODYM_imfs_V_L1_CEEMDAN.nc
    - SEAPODYM_imfs_V_L2_CEEMDAN.nc
    - SEAPODYM_imfs_V_L3_CEEMDAN.nc


Fourth, I perform GAM model building in R...

1. produces:
    - gam_abso_larvaeTF_all.rds     --> GAM trained on all oceanographic inputs, predicts log10(x+1) absolute larvae
    - gam_anom_larvaeTF_all.rds     --> GAM trained on all oceanographic inputs, predicts log10(x+1) anomalous larvae
    - gam_abso_juvenileTF_all.rds   --> GAM trained on all oceanographic inputs, predicts log10(x+1) absolute juveniles
    - gam_anom_juvenileTF_all.rds   --> GAM trained on all oceanographic inputs, predicts log10(x+1) anomalous juveniles
    - gam_abso_juvenileTF_allL.rds  --> GAM trained on all oceanographic inputs + larvae, predicts log10(x+1) absolute juveniles
    - gam_anom_juvenileTF_allL.rds  --> GAM trained on all oceanographic inputs + larvae, predicts log10(x+1) anomalous juveniles
    - gam_abso_juvenileTF_allpL.rds --> GAM trained on all oceanographic inputs + predicted larvae, predicts log10(x+1) absolute juveniles
    - gam_anom_juvenileTF_allpL.rds --> GAM trained on all oceanographic inputs + predicted larvae, predicts log10(x+1) anomalous juveniles
    - gam_abso_adultTF_all.rds      --> GAM trained on all oceanographic inputs, predicts log10(x+1) absolute adults
    - gam_anom_adultTF_all.rds      --> GAM trained on all oceanographic inputs, predicts log10(x+1) anomalous adults
    - gam_abso_adultTF_allJ.rds     --> GAM trained on all oceanographic inputs + juveniles, predicts log10(x+1) absolute adults
    - gam_anom_adultTF_allJ.rds     --> GAM trained on all oceanographic inputs + juveniles, predicts log10(x+1) anomalous adults
    - gam_abso_adultTF_allpJ.rds    --> GAM trained on all oceanographic inputs + predicted juveniles, predicts log10(x+1) absolute adults
    - gam_anom_adultTF_allpJ.rds    --> GAM trained on all oceanographic inputs + predicted juveniles, predicts log10(x+1) anomalous adults
    - lm_abso_larvaeTF_diagnostics.png
    - lm_anom_larvaeTF_diagnostics.png
    - lm_abso_juvenileTF_diagnostics.png
    - lm_anom_juvenileTF_diagnostics.png
    - lm_abso_adultTF_diagnostics.png
    - lm_anom_adultTF_diagnostics.png
   using:
    - skipjack_GAMs_SEAPODYM.Rmd
   which reads:
    - absolute_values_SEAPODYM_WCPO.txt
    - anomalous_values_SEAPODYM_WCPO.txt


2. produces:
    - Table 2 (forecast skill)
   using:
    - skipjack_GAMs_SEAPODYM_skillassessment.Rmd
   which reads:
    - absolute_values_SEAPODYM_WCPO.txt
    - anomalous_values_SEAPODYM_WCPO.txt
    - gam_abso_larvaeTF_all.rds
    - gam_anom_larvaeTF_all.rds
    - gam_abso_juvenileTF_all.rds
    - gam_abso_juvenileTF_allL.rds
    - gam_abso_juvenileTF_allpL.rds
    - gam_anom_juvenileTF_all.rds
    - gam_anom_juvenileTF_allL.rds
    - gam_anom_juvenileTF_allpL.rds
    - gam_abso_adultTF_all.rds
    - gam_abso_adultTF_allL.rds
    - gam_abso_adultTF_allpL.rds
    - gam_anom_adultTF_all.rds
    - gam_anom_adultTF_allL.rds
    - gam_anom_adultTF_allpL.rds


3. produces:
    - Table 3
    - gam_FS5_global_T_L1.csv   -->  Global univariate relationship between transformed biomass (log10(x+1)) and T_L1 (x)
    - gam_FS5_global_sst.csv    -->  Global univariate relationship between transformed biomass (log10(x+1)) and SST (x)
    - gam_FS5_global_U_L3.csv   -->  Global univariate relationship between transformed biomass (log10(x+1)) and U_L3 (x)
    - gam_FS5_global_O2_L2.csv  -->  Global univariate relationship between transformed biomass (log10(x+1)) and O2_L2 (x)
    - gam_FS5_global_zeu.csv    -->  Global univariate relationship between transformed biomass (log10(x+1)) and zeu (x)
    - gam_FS5_global_T_L2.csv   -->  Global univariate relationship between transformed biomass (log10(x+1)) and T_L2 (x)
    - gam_FS5_spatial_T_L1_sd.csv   -->  Local relationships between transformed biomass (log10(x+1)) and 1 STD of T_L1 (x)
    - gam_FS5_spatial_sst_sd.csv    -->  Local relationships between transformed biomass (log10(x+1)) and 1 STD of SST (x)
    - gam_FS5_spatial_U_L3_sd.csv   -->  Local relationships between transformed biomass (log10(x+1)) and 1 STD of U_L3 (x)
    - gam_FS5_spatial_O2_L2_sd.csv  -->  Local relationships between transformed biomass (log10(x+1)) and 1 STD of O2_L2 (x)
    - gam_FS5_spatial_zeu_sd.csv    -->  Local relationships between transformed biomass (log10(x+1)) and 1 STD of zeu (x)
    - gam_FS5_spatial_T_L2_sd.csv   -->  Local relationships between transformed biomass (log10(x+1)) and 1 STD of T_L2 (x)
    - gam_FS5_spatial_T_L1_0.5degC.csv   -->  Local relationships between transformed biomass (log10(x+1)) and 0.5 degC of T_L1 (x)
    - gam_FS5_spatial_sst_0.5degC.csv    -->  Local relationships between transformed biomass (log10(x+1)) and 0.5 degC of SST (x)
    - gam_FS5_spatial_U_L3_0.025ms.csv   -->  Local relationships between transformed biomass (log10(x+1)) and 0.025 m/s of U_L3 (x)
    - gam_FS5_spatial_O2_L2_10mmolm3.csv -->  Local relationships between transformed biomass (log10(x+1)) and 10 mmol/m3 of O2_L2 (x)
    - gam_FS5_spatial_zeu_10m.csv        -->  Local relationships between transformed biomass (log10(x+1)) and 10 m of zeu (x)
    - gam_FS5_spatial_T_L2_0.5degC.csv   -->  Local relationships between transformed biomass (log10(x+1)) and 0.5 degC of T_L2 (x)
    - anomalous_values_GAM_FS5terms_WCPO.csv --> same as anomalous_values_SEAPODYM_WCPO.txt, but with predicted biomass and terms
   using:
    - skipjack_GAMs_SEAPODYM_predictorimportance.Rmd
   which reads:
    - absolute_values_SEAPODYM_WCPO.txt
    - anomalous_values_SEAPODYM_WCPO.txt


4. produces:
    - ElNino_fingerprint_predictor_effects.png
    - ElNino_fingerprint_predictors.png
   using:
    - ElNino_fingerprint.ipynb
   which reads:
    - anomalous_values_GAM_FS5terms_WCPO.csv


5. produces:
    - anomalous_values_GAM_predictions_HF.csv
    - anomalous_values_GAM_predictions_MF.csv
    - anomalous_values_GAM_predictions_LF.csv
    - anomalous_values_GAM_predictions_T.csv
   using:
    - skipjack_GAMs_SEAPODYM_IMFs_predictions.Rmd
   which reads:
    - forcings_minus_IMFs_seasons.csv
    - anomalous_values_SEAPODYM_WCPO.txt

6. produces:
    - anomalous_values_GAM_predictions_HF.nc
    - anomalous_values_GAM_predictions_MF.nc
    - anomalous_values_GAM_predictions_LF.nc
    - anomalous_values_GAM_predictions_T.nc
   using:
    - convert_csv_to_netCDF.ipynb
   which reads:
    - anomalous_values_GAM_predictions_HF.csv
    - anomalous_values_GAM_predictions_MF.csv
    - anomalous_values_GAM_predictions_LF.csv
    - anomalous_values_GAM_predictions_T.csv

7. produces:
    - Global_effects.png                                    --> Figure 2 
    - Spatial_effects.png                                   --> Figure 3
    - Spatial_effects_m1STD.png 
    - Spatial_effects_predictorSTDs.png
    - Correlation_SST_TL1.png                               --> Supplementary Figure X
   using:
    - Global_Spatial_effects.ipynb 
   which reads:
    - gam_FS5_global_T_L1.csv
    - gam_FS5_global_SST.csv
    - gam_FS5_global_U_L3.csv
    - gam_FS5_global_O2_L2.csv
    - gam_FS5_global_zeu.csv
    - gam_FS5_global_T_L2.csv
    - gam_FS5_global_T_L1_sd.csv
    - gam_FS5_global_SST_sd.csv
    - gam_FS5_global_U_L3_sd.csv
    - gam_FS5_global_O2_L2_sd.csv
    - gam_FS5_global_zeu_sd.csv
    - gam_FS5_global_T_L2_sd.csv
    - forcings_netCDF/ipo_jra55np_1x30d_sst_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_mld_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_T_L1_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_U_L3_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_O2_L2_1958_2022.nc
    - forcings_netCDF/ipo_jra55np_1x30d_V_L1_1958_2022.nc


8. produces:
    - StandardDeviaton_AdultAnomalies_IMFs.png
    - StandardDeviaton_Oceanography_IMFs_midfreq.png
    - StandardDeviaton_Oceanography_IMFs_lowfreq.png
    - StandardDeviaton_Oceanography_IMFs_trend.png
    - LinearTrends_Oceanography_IMFs.png
    - CorrelationsWithENSO_Oceanography_IMFs_midfreq.png
    - SlopesWithENSO_Oceanography_IMFs_midfreq.png
    - CorrelationsWithIPO_Oceanography_IMFs_lowfreq.png
    - SlopesWithIPO_Oceanography_IMFs_lowfreq.png
    - CorrelationsWithCO2_Oceanography_IMFs_trends.png
    - SlopesWithCO2_Oceanography_IMFs_trends.png
    - ENSO_IPO_CorrelationsSlopes_AdultAnomalies.png        --> Figure 4
    - EffectsOfENSO_Oceanography_IMFs_midfreq.png           --> Figure 5
    - EffectsOfIPO_Oceanography_IMFs_lowfreq.png            --> Figure 6
    - EffectsOfCO2_Oceanography_IMFs_trends.png
    - effect_ENSO_on_Skipjack_allpredictors.nc
    - effect_IPO_on_Skipjack_allpredictors.nc
    - effect_CC_on_Skipjack_allpredictors.nc
    - ENSO_IPO_CorrelationsSlopes_RealAdultAnomalies.png    --> Supplementary Figure X
    - LongTermTrends_fingerprint_predictor_effects.png      --> Figure 7
   using:
    - Global_Spatial_effects_IMFs.ipynb 
   which reads:
    - anom_GAM_predictions_HF.csv
    - anom_GAM_predictions_MF.csv
    - anom_GAM_predictions_LF.csv
    - anom_GAM_predictions_T.csv
    - anom_df_pacific_small_PP75_seasons_FS5terms.csv
    - ONI.txt
    - CO2.txt
    - derived_IPO.nc


9. produces:
    - 
   using:
    -  
   which reads:
    - 




In the paper...

Step 1 creates:
 - Table 2
Step 2 creates:
 - Table 3
Step 3 creates:
 - Supplementary Figures X and X
Step 5 creates:
 - Figures 2 and 3
 - Supplementary Figure X
Step 6 creates:
 - Figures 4, 5, 6 and 7
 - Supplementary Figures X and X
