# PrecipitationUS
Plotting the Precipitation Using Online Sourced Spatial Data

The code is composed of several steps that perform different operations on data related to precipitation in the United States.

The first part of the code loads several packages that are required for the code to run. These packages include tidyverse, sf, raster, maps, and ggplot2.

The next part of the code reads a precipitation data file as a raster object using the raster function from the raster package. The data is from the PRISM climate group and is based on 30-year normals (1981-2010) for annual precipitation.

The code then loads a shapefile that contains the polygons of the US states using the st_read function from the sf package. The crop function from the raster package is then used to crop the raster object to the extent of the US states, and the resulting object is converted to an sf object using the as and st_as_sf functions from the sf package.

The st_join function from the sf package is used to perform a spatial join of the precipitation sf object with the US states sf object based on the intersection of polygons. Rows with missing state names are then removed using the filter function from the dplyr package.

The code then calculates the mean annual precipitation for each state by extracting the precipitation values for each state from the cropped raster object using the extract function from the raster package. The extracted precipitation values are then divided by 25.4 to convert  millimeters to inches. The resulting data frame is converted to an sf object and joined with the US states sf object using the st_join function from the sf package.

The code writes the resulting sf object to an Excel file using the write_xlsx function from the writexl package.

In the second part of the code, the US states sf object is read back in using the st_read function from the sf package. Alaska and Hawaii are removed from the data, and the state names are converted to title case using the filter and mutate functions from the dplyr package. The precipitation data is then read in from the Excel file using the read_excel function from the readxl package. The precipitation data is then joined to the US states sf object using the left_join function from the dplyr package.

Finally, the code plots the US map with each state colored according to the amount of precipitation using the ggplot2 package. The geom_sf function is used to plot the state polygons, and the scale_fill_gradient function is used to set the color gradient. The labs function is used to set the title, subtitle, and legend labels for the plot.
