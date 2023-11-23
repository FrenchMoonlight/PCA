# Principal Component Analysis (PCA) to identify three distinct gun cultures

## About
This repository contains code to reproduce the findings from the following paper: Boine, C., Siegel, M., Ross, C. et al. What is gun culture? Cultural variations and trends across the United States. Humanit Soc Sci Commun 7, 21 (2020). https://doi.org/10.1057/s41599-020-0520-6

While the authors originally conducted their Principal Component Analysis using the Stata software, this python program uses the same method and parameters, and reaches the same results. In addition, this program creates a plot showing the loadings of the three main components found, which is not present in the original paper.  

## Understanding the PCA
The PCA focuses on various aspects of gun culture across different states in the U.S. The analysis aims to identify and visualize key components and trends over time.

PCA is a data reduction method that transforms variables into new axes called principal components, which are linear combinations of the original variables with weights and account for most of the variance in the data. 

The created components are uncorrelated and can be used in subsequent analyses. The authors view these components as proxies of distinct gun cultures : a recreational culture, a self-defense culture, and a culture centered around Second Amendment activism. 

## Understanding the plot

In the 3D scatter plot, each point represents one of the eleven original variables from the PCA, and its position in the 3D space is determined by its loading on the three principal components.

The location of each point in the 3D space shows how much each variable contributes to each principal component. If certain variables cluster together in the plot, it suggests they share a similar pattern in terms of their contribution to the principal components. Outliers might indicate variables that have a unique structure in the data.

## Data Sources
The data used in the PCA comes from a combination of public sources and proprietary datasets. 

Public data includes:
  - the number of [hunting licenses](https://us-east-1.quicksight.aws.amazon.com/sn/accounts/329180516311/dashboards/48b2aa9c-43a9-4ea6-887e-5465bd70140b?directory_alias=tracs-quicksight) from the U.S. Fish and Wildlide Services
  - the [number of background checks](https://www.fbi.gov/how-we-can-help-you/more-fbi-services-and-information/nics) for the purchase of handguns and long guns from the Federal Bureau of Investigation
  - the presence of a stand-your-ground law in each U.S. state (the data was compiled by Michael Siegel and is available in the [State Firearms Laws database](https://mail.statefirearmlaws.org/))
  - the presence of an assault weapon ban in each U.S. state (the data was compiled by Michael Siegel and is available in the [State Firearms Laws database](https://mail.statefirearmlaws.org/))
  - the [number of federally licensed gun dealers](https://www.atf.gov/firearms/listing-federal-firearms-licensees) from the Bureau of Alcohol, Tobacco, Firearms, and Explosives

The proprietary data covers:
  - the number of NRA members in each state and for each year;
  - the share of NRA members who subscribe to the different NRA magazines (The American Hunter, America’s 1st Freedom, American Rifleman)
  - the number of Americans who subscribe to the magazine Guns and Ammo
  This data was acquired from the Alliance for Audited Media and cannot be shared publicly due to usage restrictions.

## Usage
To use the code in this repository, you will need Python and several libraries including Pandas, NumPy, and Plotly. Follow the comments in the code for detailed instructions on running the PCA.

## Limitations
Please note that the dataset used for this analysis contains proprietary variables that are not included in this repository. The code is provided for educational and illustrative purposes, and may require adaptation for use with other datasets.

## Contributing
Contributions to this project are welcome. Please feel free to fork the repository and submit pull requests. For major changes or questions, please open an issue first to discuss what you would like to change.

## License
This project is licensed under the MIT License - see the LICENSE file for details. While the MIT License does not require attribution, I kindly request that if you use or adapt this code for work on gun culture, please give appropriate credit to the original author as a courtesy. This helps to promote transparency and acknowledgment in the open-source community.

## Author
The sole author of this program is Claire Boine. If you have any inquiries or wish to provide attribution, you can reach me at contact@claireboine.com.
