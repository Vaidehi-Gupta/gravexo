# gravexo
This repository contains input dataset, results obtained and intermediate verifications performed to understand the LISA-detectable population of Exoplanets and Drown Dwarfs orbiting Double White Dwarf binaries.

### The realization numbers can be mapped to their respective keys using this:
__1: "s433", 2: "s442", 3: "s352", 4: "s444", 5: "s555", 6: "s633"__

A comprehensive description of the folders and files is as follows:

## 1. Realizations: 
&#10146; This folder has the exact files used as priors for every step – triples setup, search runs, evidence runs and posterior runs.
There are six folders. \
&#10146; Realization 1 (s433) is the one we are discarding. \
&#10146; Realization 6 (s633) was chosen to replace Realization 1 (s433).

## 2. CSV Files
### 2a. CSVs_prior :
&#10146; `total_prior.csv` : This is the number of sources in each of the prior file.\
&#10146; `e3_morethan_985_prior.csv` : This was done just to see if the number of SSO with eccentricity of the orbit greater than 0.985 is consistent across all realizations. It was a sanity check because I thought I saw too many of those for one realization. It turned out to be consistent and everything is fine.
### 2b. CSVs_triples :
&#10146; `sources_in_triples_setup_output.csv` : This is the number of sources in each scenario for every realization in the output file for triples setup.
### 2c. CSVs_search :
&#10146; `total_search.csv` : This is the total number of sources in each scenario for every realization in the output file for search runs. They can be seen in detail in `FINAL_RUN_search_info_output_6_Realizations.h5` file. \
&#10146; `total_search_exo.csv` : This is also from the same file as above, but with sources in the mass range 0 to 16 MJ. \
&#10146; `total_search_bds.csv` : This is also from the same file as above, but with sources in the mass greater than 16 MJ. \
&#10146;  `total_search_exo_det.csv` and  `total_search_bds_det.csv` : The result of search runs can’t really tell us about detectability, but this was an attempt to look at number with `logl_max_mcmc < -2`. These files are not really used much anywhere.
### 2d. CSVs_exo_evidence :
&#10146; `total_evidence_exo.csv` file has the number of sources across each scenario for all realizations, for which evidence calculations were done – this includes sure, marginal and non-detectable sources.\
&#10146; `sure_evidence_exo.csv file` has the number of sources across each scenario for all realizations, with `2logBF > 5`.\
&#10146; `marg_evidence_exo.csv` file has the number of sources across each scenario for all realizations, with `5 > 2logBF > 0`.\
&#10146; `non_det_evidence_exo.csv` file has the number of sources across each scenario for all realizations, with `2logBF < 0`.
### 2e. BD_CSV_Set_* : 
&#10146; All these files were me checking how many brown dwarfs are in different mass ranges to finalize how to run brown dwarfs.\
&#10146; I chose BD_CSV_Set3 because they were more evenly distributed.\
&#10146; This doesn’t have any disadvantage like introducing bias, because this is just to run multiple sets at the same time. The final brown dwarf analysis will be done as a whole.

## 3. Translations:
&#10146; Every Translation file can be understood this way:\
`filepath = "path/filename.h5"`\
`df = pd.read_hdf(filename, key='Real2-B1')`

The key would be in the format: \
`Real{realization_number}-{scenario}`\
Realization number mapping is mentioned above. 

&#10146; The file `FINAL_RUN_search_info_output_6_Realizations.h5` has the search runs output information for all six realizations. We decided to discard `s433`, but I stored all of them just to be precautionary.\
&#10146; The file `FINAL_RUN_evidence_exo_output_6_Realizations.h5` has the evidence runs output information for exoplanets for all six realizations.


## 4. Quantiles
## 5. ???






