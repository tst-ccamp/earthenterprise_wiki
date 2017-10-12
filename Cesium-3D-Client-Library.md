## Google Earth Enterprise and Cesium for 3D Maps
The [Cesium](http://www.cesium.org) WebGL Javascript client library provides implementation for Google Earth Enterprise Imagery and Terrain tile system.

### Imagery Provider
Provides tiled imagery using the Google Earth Enterprise REST API.

[GoogleEarthEnterpriseImageryProvider](https://cesiumjs.org/Cesium/Build/Documentation/GoogleEarthEnterpriseImageryProvider.html)

### Terrain Provider
Provides tiled terrain using the Google Earth Enterprise REST API.

[GoogleEarthEnterpriseTerrainProvider](https://cesiumjs.org/Cesium/Build/Documentation/GoogleEarthEnterpriseTerrainProvider.html)

### Installation instructions
[Quick start guide](https://cesiumjs.org/downloads/)

[Getting Started](https://cesiumjs.org/tutorials/cesium-up-and-running/)

### Example
   <!DOCTYPE html>
    <html lang="en">
    <head>
      <!-- Use correct character set. -->
      <meta charset="utf-8">
      <!-- Tell IE to use the latest, best version. -->
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <!-- Make the application on mobile take up the full browser screen and disable user scaling. -->
      <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no">
      <title>Google Earth Enterprise</title>
      <script src="../Build/Cesium/Cesium.js"></script>
      <style>
        @import url(../Build/Cesium/Widgets/widgets.css);
        html, body, #cesiumContainer {
          width: 100%; height: 100%; margin: 0; padding: 0; overflow: hidden;
        }
      </style>
    </head>
    <body>
      <div id="cesiumContainer"></div>
      <script>
        var geeMetadata = new Cesium.GoogleEarthEnterpriseMetadata({
        url : 'http://localhost/databasename' });
        var viewer = new Cesium.Viewer('cesiumContainer', {

        // GEE database would ideally have at least one imagery i.e. earth backdrop
        imageryProvider : new Cesium.GoogleEarthEnterpriseImageryProvider({
        metadata : geeMetadata
        }),
        // Use terrain provider if you have terrains in your database
        terrainProvider : new Cesium.GoogleEarthEnterpriseTerrainProvider({
        metadata : geeMetadata
        }),
        baseLayerPicker : false
        });
  
        // Start off looking at San Francisco.
        viewer.camera.setView({
        destination: Cesium.Rectangle.fromDegrees(-123.0, 36.0, -121.7, 39.0)});
      </script>
    </body>
  

    </html>