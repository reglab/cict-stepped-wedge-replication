# cict-stepped-wedge-replication

Public data and replication for the paper: "Automated vs. Manual Case Investigation and Contact Tracing for Pandemic Surveillance: Evidence from a Stepped Wedge Cluster Randomized Trial"

## Repository Structure

1. **`panel_data.csv`**: Aggregate data from the study used made available for partial replication
2. **`Figure_Replication.ipynb`**: A Jupyter notebook replicating Figures 2, 3, 4 (difference-in-differences time series plots)
3. **`Figure_Replication.ipynb`**: Partial replication of the regression analysis presented in Table 3 using panel data instead of individual level data

## Data Structure

| Column      	| week           	| Zip                	| crossover                                                                                                	| svi_label                                    	| condition                                                                                                                                                                       	| n_assigned_automated                               	| n_assigned_manual                              	| mean_perc_filled_assigned_automated                                                                       	| mean_perc_filled_assigned_automated                                                                   	|
|-------------	|----------------	|--------------------	|----------------------------------------------------------------------------------------------------------	|----------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|----------------------------------------------------	|------------------------------------------------	|-----------------------------------------------------------------------------------------------------------	|-------------------------------------------------------------------------------------------------------	|
| Type        	| <date>         	| <factor>           	| <int,[2,3,4,5]>                                                                                          	| <str, "[50,80) SVI" or "[80,100] SVI">       	| <str, "Manual CICT" or "Automated CICT">                                                                                                                                        	| <int>                                              	| <int>                                          	| <float, [0,1]>                                                                                            	| <float, [0,1]>                                                                                        	|
| Description 	| Reference week 	| Reference ZIP Code 	| Refers to the ZIP Code's belonging to the early (2), medium (3), late (4) or never (5) step down cluster 	| That ZIP Code's social vulnerability bucket. 	| The condition that ZIP Code is receiving on that week based on the randomization protocol. In other words, what form of CICT should participants be receiving in that ZIP Code. 	| Number of participants assigned to automated CICT. 	| Number of participants assigned to manual CICT 	| Overall completion rate of data fields for participants in the ZIP Code who  were assigned automated CICT 	| Overall completion rateof data fields for participants in the ZIP Code who  were assigned manual CICT 	|
| Example     	| 2021-12-13     	| 94040              	| 4                                                                                                        	| [50,80) SVI                                  	| Manual CICT                                                                                                                                                                     	| 1                                                  	| 10                                             	| 0.8181818181818182                                                                                        	| 0.6545454545454545                                                                                    	|