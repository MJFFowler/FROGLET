# FROGLET

Fields extRactor frOm GoogLe EarTh pins 

A semi-automated pipeline for the conversion of Google Earth KML pin files formatted to record archaeological features into an Excel database. The pipeline has been built to support the Aerial Archaeology Research Group's Ukraine Working Group as it maps archaeological features from freely available satellite imagery and other sources.

The pipeline comprises two Excel worksheets and a .txt intermediate file to process the GE pins and includes a relatively high degree of error checking to diagnose any anomalies in the recording of data. It starts with the KMZ file of a square containing the placemarks of features recorded primarily as pins, but also polygons and lines. The KMZ is loaded into GE and all the pins in the square are saved in a separate KML file .Likewise, if present the polygons and lines are saved as KML files for later use. 

The KML pin file is then parsed into Excel and the relevant columns containing the pin name, description, pin type and latitude and longitude coordinates are copied and pasted into the first FROGLET worksheet. Within this worksheet, lots of Excel ‘magic’ is done to format the text into an intermediate file for processing in the second FROGLET worksheet. Specifically, the worksheet:

•	Converts any commas in the description fields into underscores so they do not interfere with the later output of CSV files from the database.

•	Removes any extraneous carriage returns and extracts the latitude and longitude coordinate information into separate text fields.

•	Includes a relatively high degree of error checking to diagnose any anomalies in the recording of the data.

•	Produces a formatted intermediate output for the second FROGLET worksheet

The formatted output from the first worksheet is then copied and saved as a text file, and imported into a new blank Excel spreadsheet as a #-delimeted input to give columns corresponding to the various fields. These are then copied and pasted into the second FROGLET worksheet which:

•	Removes the field names from each record to leave the recorded data.

•	Converts the latitude and longitude coordinate information from text into numerical values.

•	Adds additional fields such as the square number, the date when the KMZ was processed, and the name of the KMZ file that was processed.

•	Uses a lookup table to convert the various synonyms for features recorded by the pins into an agreed feature type (e.g., features recorded as ‘mound’, ‘Mound’, ‘mounds’ are all given the feature name of ‘mound’).

•	Identifies archaeological and non-archaeological sites based on the feature type lookup table .

•	Includes further error checking of field names.

•	Produces a formatted output for export to a database table.

Finally, the output from the second worksheet is copied and pasted into an Excel database table which is linked to an Access database as an external data source. The Excel database can be queried to produce outputs as Comma Separated Values (CSV) files for display and analysis in QGIS and ArcGIS Earth / Online, and produce various text reports such as a detailed gazetteer of mapped features, lists of feature types, features per square etc
