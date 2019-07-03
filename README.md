# Map-file-for-WMS-layers
The map file required to publish WMS layers  on QGIS
While publishing these files need to be kept in a separate folder in the apps folder of the ms4w server.

Steps for publishing WMS layers of geotiff images-
1.)run the wms4 server by running in the administrtive command prompt- 
apache-install.bat
2.) Stack the required bands first using the following command in the OSGeo4W shell
(cd to the folder where you want to keep all the stacks)

**
gdal_merge -separate -o outputfilename.tif -co PHOTOMETRIC=MINISBLACK pathtoband2.tif pathtoband3.tif pathtoband4.tif
**

3.)add these stacked images to QGIS and make them false colour composite-RED band=Band 3, Green band=Band 2,Blue band=Band 1(gray)
3.)go to add wms layer
4.)in the 'NEW' section provide Name(eg.test) and the following URL:

**
http://127.0.0.1/cgi-bin/mapserv.exe?map=C:/ms4w/apps/k/test.map&REQUEST=GetCapabilities&SERVICE=WMS&VERSION=1.3.0

**
where C:/ms4w/apps/k/test.map is the address to the map file.

5.)Connect
6.)check for the published layer on the same link as mentioned above on Chrome.
