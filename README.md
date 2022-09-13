# cict-stepped-wedge-replication

Public data and replication of the paper: *Automated vs. Manual Case Investigation and Contact Tracing for Pandemic Surveillance: Evidence from a Stepped Wedge Cluster Randomized Trial*

## Repository Structure

1. [**`panel_data.csv`**](https://github.com/reglab/cict-stepped-wedge-replication/blob/main/panel_data.csv): Aggregate data from the study used made available for partial replication
2. [**`Figure_Replication.ipynb`**](https://github.com/reglab/cict-stepped-wedge-replication/blob/main/Figure_Replication.ipynb): A Jupyter notebook replicating Figures 2, 3, 4 (difference-in-differences time series plots)
3. [**`Figure_Replication.ipynb`**](https://github.com/reglab/cict-stepped-wedge-replication/blob/main/Regression_Replication.ipynb): Partial replication of the regression analysis presented in Table 3 using panel data instead of individual level data
4. [**`Stepped Wedge CICT Protocol.pdf`**](https://github.com/reglab/cict-stepped-wedge-replication/blob/main/Stepped%20Wedge%20CICT%20Protocol.pdf): The study protocol  

## Data Structure

The data is organized as a ZIP Code x Week panel. For each week/ZIP Code the treatment condition (manual/automated), is recorded along with the number of participants assigned to automated and manual CICT and observed outcomes for participants who recieved each treatment. 

Under perfect compliance a ZIP Code in the manual condition would only have individuals assigned to manual CICT, and a ZIP Code in the automated condition would only have individuals assigned to automated CICT; however, due to capacity constraints we observed a large number of overflow cases where individuals in the manual condition were given automated CICT. 

As a result, for each outcome we provide the result for participants in each condition (i.e., manual outcome and automated), regardless of what the randomization protocol says. This allows for replicating the ITT analysis, IV analysis and Figures 2,3,4 which visualize the overflow cases as well. The below table shows the data structure: 

| Column      	| week           	| Zip                	| crossover                                                                                                	| svi_label                                    	| condition                                                                                                                                                                       	| n_assigned_automated                               	| n_assigned_manual                              	| mean_perc_filled_assigned_automated                                                                       	| mean_perc_filled_assigned_manual                                                                       	|
|-------------	|----------------	|--------------------	|----------------------------------------------------------------------------------------------------------	|----------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|----------------------------------------------------	|------------------------------------------------	|-----------------------------------------------------------------------------------------------------------	|--------------------------------------------------------------------------------------------------------	|
| Type        	| <date>         	| <factor>           	| <int,[2,3,4,5]>                                                                                          	| <str, "[50,80) SVI" or "[80,100] SVI">       	| <str, "Manual CICT" or "Automated CICT">                                                                                                                                        	| <int>                                              	| <int>                                          	| <float, [0,1]>                                                                                            	| <float, [0,1]>                                                                                         	|
| Description 	| Reference week 	| Reference ZIP Code 	| Refers to the ZIP Code's belonging to the early (2), medium (3), late (4) or never (5) step down cluster 	| That ZIP Code's social vulnerability bucket. 	| The condition that ZIP Code is receiving on that week based on the randomization protocol. In other words, what form of CICT should participants be receiving in that ZIP Code. 	| Number of participants assigned to automated CICT. 	| Number of participants assigned to manual CICT 	| Overall completion rate of data fields for participants in the ZIP Code who  were assigned automated CICT 	| Overall completion rate of data fields for participants in the ZIP Code who  were assigned manual CICT 	|
| Example     	| 2021-12-13     	| 94040              	| 4                                                                                                        	| [50,80) SVI                                  	| Manual CICT                                                                                                                                                                     	| 1                                                  	| 10                                             	| 0.8181818181818182                                                                                        	| 0.6545454545454545                                                                                     	|
    
There are also additional columns showing the individual data field completion rate.
    
### Data Dictionary

1. **`week`**: Reference week
1. **`Zip`**: Reference ZIP Code
1. **`crossover`**: Refers to the ZIP Code's belonging to the early (2), medium (3), late (4) or never (5) step down cluster
1. **`svi_label`**:  Whether the ZIP Code is high SVI (80-100) or low SVI (50-80)
1. **`condition`**: Whether the ZIP Code is in the manual CICT condition or the automated CICT condition
1. **`n_assigned_automated`**: Number of participants in that ZIP Code assigned to automated CICT
1. **`n_assigned_manual`**: Number of participants in that ZIP Code assigned to manual CICT
1. **`mean_perc_filled_assigned_automated`**: Primary outcome, the overall completion rate for the 11 data fields for the participants who were given automated CICT
1. **`mean_perc_filled_assigned_manual`**: Primary outcome, the overall completion rate for the 11 data fields for the participants who were given manual CICT
1. **`mean_has_race_ethnicity_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided their race/ethnicity 
1. **`mean_has_race_ethnicity_assigned_manual`**: Proportion of individuals who recieved manual CICT that answered their race/ethnicity 
1. **`mean_has_employer_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided their employer 
1. **`mean_has_employer_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided their employer 
1. **`mean_has_gender_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided their gender 
1. **`mean_has_gender_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided their gender
1. **`mean_has_sexual_orientation_assigned_automated`**:  Proportion of individuals who recieved automated CICT that provided their sexual orientation 
1. **`mean_has_sexual_orientation_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided their sexual orientation 
1. **`mean_has_language_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided their preferred language 
1. **`mean_has_language_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided their preferred language 
1. **`mean_has_signs_or_symptons_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided their COVID-19 symptoms 
1. **`mean_has_signs_or_symptons_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided their COVID-19 symptoms 
1. **`mean_has_travel_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided whether they had travelled recently
1. **`mean_has_travel_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided whether they had travelled recently
1. **`mean_has_attended_gathering_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided whether they had attened a large gathering recently 
1. **`mean_has_attended_gathering_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided whether they had attened a large gathering recently 
1. **`mean_has_able_to_self_isolate_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided whether they were able to self isolate 
1. **`mean_has_able_to_self_isolate_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided whether they were able to self isolate 
1. **`mean_has_num_contacts_generated_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided whether they had any recent contacts 
1. **`mean_has_num_contacts_generated_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided whether they had any recent contacts 
1. **`mean_has_congregate_setting_assigned_automated`**: Proportion of individuals who recieved automated CICT that provided whether they had any exposure to a congregate setting 
1. **`mean_has_congregate_setting_assigned_manual`**: Proportion of individuals who recieved manual CICT that provided whether they had any exposure to a congregate setting   
    

## Contact
    
This code and data were prepared by Cameron Raymond on September 13, 2022. If you have questions, reach out to Derek Ouyang at douyang1@law.stanford.edu.