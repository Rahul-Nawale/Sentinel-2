Sentinel-2 Imagery Data Processing and STAC Metadata Generation

Overview
This documentation outlines the process of downloading, processing, and organizing Sentinel-2 imagery data into a SpatioTemporal Asset Catalog (STAC) format. The process involves combining bands, converting to Cloud Optimized GeoTIFFs (COGs), creating metadata, and uploading data to Google Cloud Storage.

Project Details
Sentinel-2 Data Source: Sentinel-2 Data Hub

Processing Steps

1. Combining Bands Using GDAL
Three bands (B02, B03, B04) are combined into an RGB composite using GDAL commands.

2. Converting to Cloud Optimized GeoTIFFs (COGs)
JP2 files are converted to COGs to optimize them for web access and analysis.
Pixel data is replaced with a nodata value of 0 in the COG files.

4. Creating Overview and Thumbnail Images
Lower resolution overview and thumbnail images are generated from the COGs.
Overview and thumbnail images are saved in WEBP format.

6. Extracting Metadata
Metadata is extracted from the COG files using gdalinfo.
Metadata is saved in JSON files, one for each COG.

8. Creating STAC JSON Files
Item JSON files are created for each COG, adhering to the STAC specification.
A collection JSON file and a catalog JSON file are created to organize the data.

10. Uploading to Google Cloud Storage
Data files, including COGs, JSON files, and images, are uploaded to Google Cloud Storage.
Data is organized in the following structure:

gs://your-bucket-name/stac-data/
├── item-1/
│   ├── item.json
│   ├── assets/
│   │   ├── asset-1.jpg
│   │   ├── asset-2.tif
│   └── ...
├── item-2/
│   ├── item.json
│   ├── assets/
│   │   ├── asset-1.jpg
│   │   ├── asset-2.tif
│   └── ...
└── ..

Running the Code
Detailed code examples and scripts for each step are provided in the repository.
Prerequisites

GDAL library installed for geospatial data processing.
Python environment with required libraries (e.g., PIL, rasterio) for image processing.

Conclusion
This documentation outlines the step-by-step process of processing Sentinel-2 imagery data and organizing it into a STAC format. By following these steps, you can efficiently manage and share your geospatial data for various applications.
