# EnDOH-RAG-v-s-NonRAG

## Finding relevant topics/categories for RAG vs. Non-RAG prompts to generate concepts
In order to find relevants topics, we first look at the existing Environmental Determinants of Health Ontology (EnDOH) at BioPortal and filter out concepts which has >2 siblings and a grandparent. From these concepts we find relevant categories which can be included for further research.

As the second step, we look at Environmental Science Journals with High Scimago Ranking and find the upcoming research topics in the past two years.

These two steps together give us the following viable categories.

| **Category** | **Concept (Leaf Node)** | **Parent** | **Grandparent** |
|:--|:--|:--|:--|
| **Climate Change and Disease Spread** | Vector_borne_disease_transmission, Heat_related_illnesses | Climate_related_health_risks | Environmental_Determinants_of_Health |
| **Occupational and Industrial Exposures** | Agriculture_pesticide_Exposure, Construction_dust_hazrad, Industrial_noise_pollution, Lead_pipes_workplace, Paint_chemical_inhalation | Exposure_to_pollutants_workplace | At_the_Individual_level |
| **Housing Conditions and Health** | Indoor_air_pollution, Poor_ventilation_effects, Overcrowding | Exposure_to_pollutants_home | At_the_Individual_level |
| **Vulnerable Populations** | Elderly_population, Homeless_individuals, Migrant_workers | Population_subgroups | Social_Determinants_of_Health |
| **Neighbor and Community Environment** | Access_to_clean_Water, Access_to_nutritious_food, Public_green_spaces, Street_lighting_quality, Community_noise_pollution | Local_community_infrastructre | At_the_microenvironmental_level |
| **Biological Exposures** | Viral_pathogens, Bacterial_contaminants, Fungal_spores | Biological_agents | Environmental_Exposures |
| **Chemical Exposures** | Asbestos_Exposure_home, Carbon_monoxide_Exposure, Cleaning_chemical_risk, Indoor_mold_growth, Lead_pipes_at_home, Poor_ventilation_effects | Exposure_to_pollutants_home | At_the_Individual_level |
| **Disasters and Emergency Preparedness** | Flood_related_injuries, Earthquake_response_capacity, Disaster_recovery_infrastructure | Disaster_preparedness | Environmental_Events |
| **Built Environment and Infrastructure Quality** | Lead_pipes_workplace, Construction_dust_hazrad, Industrial_noise_pollution | Exposure_to_pollutants_workplace | At_the_Individual_level |
| **Indoor Air Quality and Household Hazards** | Carbon_monoxide_Exposure, Indoor_mold_growth, Cleaning_chemical_risk | Exposure_to_pollutants_home | At_the_Individual_level |
| **Water, Sanitation, and Waste Management** | Clean_sanitation_facility, Community_sewage_management, Waste_managment_facility, Waste_recycling_facilities | Local_community_infrastructre | At_the_microenvironmental_level |
| **Urban Design and Livability** | Public_green_spaces, Street_lighting_quality, Community_noise_pollution | Local_community_infrastructre | At_the_microenvironmental_level |
| **Climate Adaptation and Infrastructure Resilience** | Flood_control_mechanisms, Erosion_in_irrigation_channels | Local_community_infrastructre | At_the_microenvironmental_level |
