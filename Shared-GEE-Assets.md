# A collection of preprocessed Google Earth Enterprise Assets 

The purpose of this page is to share preprocessed Google Earth Enterprise Assets (.kip / .kmp, etc.) 

These assets should assist GEE Open Source users in quickly sourcing basemap data and building globes without having to seek out commonly used source datasets and spend time processing them. 

Always respect the original source's attribution requirements in your Databases. 

If you have a preprocessed dataset you think the community would appreciate, please open an issue to have it included.

## Imagery
### Blue Marble Bathy
![](https://storage.googleapis.com/gee-data/BlueMarbleBathy/BlueMarbleBathy-preview.png)
##### Description:
A world-wide low resolution basemap image of the world. The Blue Marble: Next Generation is a series of images that show the color of the Earth’s surface for the month of July, 2004 at 500 meters/pixel. This image also contains coarse ocean Bathymetry.
##### 3D:

| Zoom Level    | File Size     | Original Source | GCS Path | GCS Permissions | GCS CRCMOD |
| ------------- | ------------- | ----------------|----------|-----------------|-------------|
| 9             | 1.78 Gigabytes| [NASA](http://www.google.com/url?q=http%3A%2F%2Fvisibleearth.nasa.gov%2Fview.php%3Fid%3D73751&sa=D&sntz=1&usg=AFQjCNHUojZG_AaCtuCq17LsFSJ1hJzXnA)| gs://gee-data/BlueMarbleBathy/| Public| No |

## Terrain
### ETOPO1
![](https://storage.googleapis.com/gee-data/ETOPO1/ETOPO1-preview.png)
##### Description:
ETOPO1 is a 1 arc-minute (Roughly 1.85 km) global relief model of Earth's surface that integrates land topography and ocean bathymetry. It was built from numerous global and regional data sets, and this is the  "Bedrock" (base of the ice sheets) version.

| Zoom Level    | File Size     | Original Source | GCS Path | GCS Permissions | GCS CRCMOD |
| ------------- | ------------- | ----------------|----------|-----------------|-------------|
| 10            | 1 Gigabyte| [NOAA](https://www.google.com/url?q=https%3A%2F%2Fwww.ngdc.noaa.gov%2Fmgg%2Fglobal%2Fglobal.html&sa=D&sntz=1&usg=AFQjCNE0x3d9GdFR5POePdQr7iiGOFcfNQ)| gs://gee-data/ETOPO1/| Public| No |

### SRTM30Plus_V8
![](https://storage.googleapis.com/gee-data/SRTM30PlusV8/srtm30plus.png)
##### Description:
his dataset is a 30-arc second (Roughly 1 Km) resolution global topography/bathymetry grid (SRTM30_PLUS) developed from a wide variety of data sources. Land and ice topography comes from the SRTM30 and ICESat topography, respectively. Ocean bathymetry is based on a new satellite-gravity model where the gravity-to-topography ratio is calibrated using 298 million edited soundings. The main contribution of this dataset is the compilation and editing of the raw soundings, which come from NOAA, individual scientists, SIO, NGA, JAMSTEC, IFREMER, GEBCO, and NAVOCEANO.
The SRTM30_PLUS dataset was developed by Scripps Institute Of Oceanography, University of California San Diego (UCSD), and served as the initila bathymetry for [Google Ocean in Google Earth and Google Maps](https://www.google.com/url?q=https%3A%2F%2Fscripps.ucsd.edu%2Fnews%2F1871&sa=D&sntz=1&usg=AFQjCNHVh4AYWMEoq6YSrBXP2nIm_X-TOQ).
Land data are based on the 1-km averages of topography derived from the USGS SRTM30 grided DEM data product created with data from the NASA Shuttle Radar Topography Mission. GTOPO30 data are used for high latitudes where SRTM data are not available. Ocean data are based on the Smith and Sandwell global 1-minute grid between latitudes +/- 81 degrees. Higher resolution grids have been added from the LDEO Ridge Multibeam Synthesis Project, the JAMSTEC Data Site for Research Cruises, and the NGDC Coastal Relief Model. Arctic bathymetry is from the International Bathymetric Chart of the Oceans (IBCAO) [Jakobsson et al., 2003]. 

| Zoom Level    | File Size     | Original Source | GCS Path | GCS Permissions | GCS CRCMOD |
| ------------- | ------------- | ----------------|----------|-----------------|-------------|
| 11            | 3.39 Gigabytes| [Scripps Institution of Oceanography, UCSD](http://www.google.com/url?q=http%3A%2F%2Ftopex.ucsd.edu%2FWWW_html%2Fsrtm30_plus.html&sa=D&sntz=1&usg=AFQjCNEWcSk9YfA5cRLXG5jngcZPDuq9YA),  via [eAtlas.org.au](http://www.google.com/url?q=http%3A%2F%2Featlas.org.au%2Fdata%2Fuuid%2F80301676-97fb-4bdf-b06c-e961e5c0cb0b&sa=D&sntz=1&usg=AFQjCNE-LWEyAQg6_fKVspF7XHD05FR3Rg)| gs://gee-data/SRTM30PlusV8/| Public| No |

