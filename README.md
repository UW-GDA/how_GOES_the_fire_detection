# how_GOES_the_fire_detection
Project Title: 
- How GOES The Fire Detection? Assessing GOES satellite fire detection accuracy.

Name(s) of individual or team members:
- Jori Carter

Short 1-2 sentence summary:
- This project will use government provided historic fire data, including start dates and total acres burned. This data will then be compared to GOES satellite data from those times to assess whether or not GOES satellites can be used to accurately detect fires.

Some introductory background information
- This project will use existing code from Steven Pestana to process and orthorectify the GOES data. The data used will be from the Washington Department of Natural Resources.

Problem statement, question(s) and/or objective(s)
- How accurate is GOES when detecting fires?
    - Does it accurately detect start dates?
    - How does the extent of the fire compare to government data
    - Are there other signs of fire that can be used from GOES for early detection?
    - How does GOES see the lifespan of a fire?
    
Datasets you will use (with links, if available)
- https://geo.wa.gov/
- Washington Large Fires -> Washington Large Fires 1973-2020 download 
- WSDOT Highway Corridors



Tools/packages you’ll use (with links):
- goes-ortho (Steven Pestana) https://github.com/spestana/goes-ortho
- goes-py https://github.com/palexandremello/goes-py
- numpy
- geopandas
- xarray
- rasterio
- matplotlib
- fiona
- folium
- rioxarray

Methodology/approach:
- First, the government data needs to be sorted and projected correctly. This will be done just using geopandas and numpy. The time range for fires is going to be 2018 to 2020. These years need to be isolated
- A few metrics will be used to pick 4 fires. Remoteness, which will be relative to the centroid of each fire and WSDOT highway corridors, will be one metric. Size will also be considered. 2 large and 2 small fires will be analyzed.
- The bulk of this project is going to occur using GOES data, there are several fire products available to use already provided by NOAA, however I am just going to use thermal infrared bands for basic detection.
- Using Steven's Orthorectifying and general downloading code, GOES-17 data for a few selected fires will be downloaded.
- This data needs to be projected in a way that allows for it to be overlayed with the government provided data. The government data is a vector dataset, the GOES data is a raster dataset, so there should be some immediate differences in the boundary areas.
- First, the start date will be assessed. were there signs of the fire before the recorded start date? Unfortunately, the vector data does not give a day by day boundary, so the maximum extent of the fires will be compared.
- Since the fire data was questionable, a single fire will be analyzed throughout its lifespan as well. From this, the area of the fire per day is determined. 

Expected outcomes
- I am going to assume that government vector data is going to be more accurate than GOES. The point of this is to assess whether or not GOES can be a useful tool in finding fires. Many fires in remote regions may not be recognized or found quick enough to prevent massive spread. Using a satellite like GOES, which is generally for weather and is geostationary, can be a great backup for fire detection as it will always be available.

Any other relevant information, images/tables, references, etc.
- There is one notebook for this project, organized in 6 parts. The GOESpy and goes_ortho libraries are included in this repository, however the actual code used may vary slightly due to environment differences etc. Note that all data should be included for this notebook to run. All Data has been used has been uploaded to the github repository. For any questions, email jpwc@uw.edu.
