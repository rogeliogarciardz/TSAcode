# TSAcode
TSA code for analyzing the "El Cielo" biosphere reserve

tsa_per_pixel.mlx: Contains the matlab code of TSA analysis
arr_ndvi_3d.mat: Contains the MODIS/NDVI data and another information
BiosferaElCielo.kml: Contains the kml used to delimite the study area. 
 
In matlab code, you can change the umbral theta and the year of analysis

%% umbral theta of sensibility 
%% recomended: 0.3, 1.53, 2.40, 3.00, 3.55 acording dNBR
theta = 2.40;

%% year of analysis. Interval (2000-2025)
year = 2022;

==== TSA MAP PER DAY ====
tsa_map_per_day.mlx: Contains the matla code for mapping TSA values
arr_tsa_3d.mat Contains TSA values from TSA analysis using ϴ=[0.30, 1.53, 2.40, 3.00, 3.55]  

In matlab code, you can change the day you see the map
id_day =  516; refere May 25, 2022

you can see more id_day in arr_date vector. 
