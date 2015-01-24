# Mapbox
MapBox (documentation en français)

# Simple carte

Afficher une carte (vous pouvez personnaliser l'emprise, le zoom et le fond de carte

        <!DOCTYPE html>
        <html>
        <head>
        <meta charset=utf-8 />
        
        <title>Single marker</title>
        
        <script src='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css' rel='stylesheet' />
        
        <style>
        body { margin:10; padding:0; }
        #map { width: 1000px; height:500px; margin:0; padding:0; background: black;}
        </style>
        
        </head>
        
        <body>
        
        <div id='map'></div>
        
        <script>
        
        L.mapbox.accessToken = 'pk.eyJ1IjoibmluYW5vdW4iLCJhIjoiSkN4dndmTSJ9.6plStO7M5AuAbDa6O1m54A';
        
        var map = L.mapbox.map('map', 'mapbox.satellite').setView([20, 20], 3);
        
        </script>
        
        </body>
        </html>

# Ajouter des fonds de carte

        <!DOCTYPE html>
        <html>
        <head>
        <meta charset=utf-8 />
        <title>A simple map</title>
        <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
        <script src='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css' rel='stylesheet' />
        
        <style>
          body { margin:10; padding:10; }
          #map {  width: 1000px; height:600px; margin:10; padding:10; background: black;}
        </style>
        </head>
        <body>
        
        
        <div id='map'></div>
        <script>
        
        L.mapbox.accessToken = 'pk.eyJ1IjoibmluYW5vdW4iLCJhIjoiSkN4dndmTSJ9.6plStO7M5AuAbDa6O1m54A';
        
        var map = L.mapbox.map('map').setView([41.68648, 82.80783], 10);
        
        // Fonds de carte 
        
        var baselayers = {
              Streets: L.mapbox.tileLayer('mapbox.streets'),
              satellite: L.mapbox.tileLayer('mapbox.satellite'),
        	  wheatpaste: L.mapbox.tileLayer('mapbox.wheatpaste'),
        	  outdoors: L.mapbox.tileLayer('mapbox.outdoors'),
        	  emerald: L.mapbox.tileLayer('mapbox.high-contrast') };  
          baselayers.Streets.addTo(map);
        
         // Selecteur de couches
         
          L.control.layers(baselayers).addTo(map);
        </script>
        
        </body>
        </html>

# Ajouter des marqueurs en GeoJSON

        <!DOCTYPE html>
        <html>
        <head>
        <meta charset=utf-8 />
        <title>Single marker</title>
        <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
        <script src='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css' rel='stylesheet' />
        <style>
        body { margin:10; padding:0; }
        #map { width: 500px; height:500px; margin:0; padding:0; background: black;}
        </style>
        </head>
        <body>
        
        <div id='map'></div>
        
        <script>
        L.mapbox.accessToken = 'pk.eyJ1IjoibmluYW5vdW4iLCJhIjoiSkN4dndmTSJ9.6plStO7M5AuAbDa6O1m54A';
        var map = L.mapbox.map('map', 'examples.map-i86nkdio')
            .setView([48.119671, -1.702769], 17);
        
        L.mapbox.featureLayer({
            type: 'FeatureCollection',
            features: [{
             type: 'Feature',
                properties: {
                    title: 'Salle A007',
                    'marker-color': '#f86767',
                    'marker-size': 'large',
                    'marker-symbol': 'star',
        			url: 'http://en.wikipedia.org/wiki/Washington,_D.C.'},
                geometry: {
                    type: 'Point',
                    coordinates: [-1.703383, 48.118407]}},
            {type: 'Feature',
                properties: {
                    title: 'BU',
                    'marker-color': '#7ec9b1',
                    'marker-size': 'large',
                    'marker-symbol': 'star',},
                geometry: {
                    type: 'Point',
                    coordinates: [-1.701353, 48.120634]}}]
        }).addTo(map);
        
        </script>
        
        </body>
        </html>


# Fonds de cartes et données issues de Mapbox

        <!DOCTYPE html>
        <html>
        <head>
          <meta charset="utf-8">
          <title>Leaflet layers control</title>
          <meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no">
          <script src="https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js"></script>
          <link href="https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css" rel="stylesheet">
          <style>
        body { margin:10; padding:10; }
        #map { width: 1200px; height:600px; margin:10; padding:10; background: black;}
          </style>
        </head>
        
        <body>
        <div id="map"></div>
        
        <script>
        L.mapbox.accessToken = 'pk.eyJ1IjoibmluYW5vdW4iLCJhIjoiSkN4dndmTSJ9.6plStO7M5AuAbDa6O1m54A';
        var map = L.map('map').setView([48.111,-1.67], 13);
        
        var baselayers = {
              Streets: L.mapbox.tileLayer('mapbox.streets'),
              satellite: L.mapbox.tileLayer('mapbox.satellite'),
        	  wheatpaste: L.mapbox.tileLayer('mapbox.wheatpaste'),
        	  outdoors: L.mapbox.tileLayer('mapbox.outdoors'),
        	  emerald: L.mapbox.tileLayer('mapbox.high-contrast')};  
          
          baselayers.Streets.addTo(map);
          
         var overlays = {
            Limites: L.mapbox.featureLayer('ninanoun.kn37dkk7'),
            Recharges: L.mapbox.featureLayer('ninanoun.kn34f7d3'),
            Bornes: L.mapbox.featureLayer('ninanoun.kn34l0ea'),
        	Metro: L.mapbox.featureLayer('ninanoun.kn35p89a')};
        
         overlays.Limites.addTo(map);
        
        L.control.layers(baselayers, overlays).addTo(map);
        </script>
        
        </body>
        </html>

# Mini carte

        <!DOCTYPE html>
        <html>
        <head>
        <meta charset=utf-8 />
        <title>A simple map</title>
        <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
        <script src='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css' rel='stylesheet' />
        <style>
        body { margin:10; padding:10; }
        #map { width: 1200px; height:600px; margin:10; padding:10; background: black;}
        </style>
        </head>
        <body>
        
        <script src='https://api.tiles.mapbox.com/mapbox.js/plugins/leaflet-minimap/v1.0.0/Control.MiniMap.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox.js/plugins/leaflet-minimap/v1.0.0/Control.MiniMap.css' rel='stylesheet'/>
        <div id='map'></div>
        <script>
        
        L.mapbox.accessToken = 'pk.eyJ1IjoibmluYW5vdW4iLCJhIjoiSkN4dndmTSJ9.6plStO7M5AuAbDa6O1m54A';
        var map = L.mapbox.map('map', 'mapbox.streets').setView([41, 32], 8);
        
        var miniMap = new L.Control.MiniMap(L.mapbox.tileLayer('mapbox.outdoors'))
                    .addTo(map);
        
        </script>
        
        </body>
        </html>

# Swipe layer 

Permet de visualiser deu couches par glissement

        <!DOCTYPE html>
        <html>
        <head>
        <meta charset=utf-8 />
        <title>Swipe between layers</title>
        <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
        <script src='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css' rel='stylesheet' />
        <style>
          body { margin:0; padding:0; }
          #map { position:absolute; top:0; bottom:0; width:100%; }
        </style>
        </head>
        <body>
        
        <style>
        .range {
          position:absolute;
          width:100%;
          }
        .leaflet-top .leaflet-control-zoom {
          top:20px;
          }
        </style>
        
        <div id='map'></div>
        <input id='range' class='range' type='range' min='0' max='1.0' step='any' />
        
        <script>
        L.mapbox.accessToken = 'pk.eyJ1IjoibmluYW5vdW4iLCJhIjoiSkN4dndmTSJ9.6plStO7M5AuAbDa6O1m54A';
        var map = L.mapbox.map('map');
        L.mapbox.tileLayer('mapbox.satellite').addTo(map);
        
        var imagery = L.tileLayer.wms('http://geobretagne.fr/geoserver/photo/wms?', { 
          format: 'image/png',
          transparent: true,
          layers: 'satellite-ancien',
          attribution: "Image de 1949" 
        }).addTo(map);
        
        var range = document.getElementById('range');
        
        function clip() {
          var nw = map.containerPointToLayerPoint([0, 0]),
              se = map.containerPointToLayerPoint(map.getSize()),
              clipX = nw.x + (se.x - nw.x) * range.value;
        
          imagery.getContainer().style.clip = 'rect(' + [nw.y, clipX, se.y, nw.x].join('px,') + 'px)';}
        
        range['oninput' in range ? 'oninput' : 'onchange'] = clip;
        map.on('move', clip);
        map.setView([48.10,-1.70], 16);
        
        clip();
        </script>
        
        </body>
        </html>

# Sync Map

Pemrt d'afficher deux types de cartes simultanément 

        <!DOCTYPE html>
        <html>
        <head>
        <meta charset=utf-8 />
        <title>Sync Maps</title>
        <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
        <script src='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js'></script>
        <link href='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css' rel='stylesheet' />
        <style>
          body { margin:10; padding:10; }
        </style>
        </head>
        <body>
        
        <div id='map1'></div>
        <div id='map2'></div>
        
        <style>
          #map1 { position:absolute; top:0; bottom:0; left:0; right:50%; }
          #map2 { position:absolute; top:0; bottom:0; left:50%; right:0; }
        </style>
        
        <script>
        L.mapbox.accessToken = 'pk.eyJ1IjoibmluYW5vdW4iLCJhIjoiSkN4dndmTSJ9.6plStO7M5AuAbDa6O1m54A';
        
        var map1 = L.mapbox.map('map1', 'mapbox.outdoors')
            .setView([39.87, -75.24], 14);
        
        	var map2 = L.mapbox.map('map2', 'mapbox.satellite')
            .setView([39.87, -75.24], 14);
        
        map1.on('moveend', follow).on('zoomend', follow);
        map2.on('moveend', follow).on('zoomend', follow);
        
        var quiet = false;
        function follow(e) {
            if (quiet) return;
            quiet = true;
            if (e.target === map1) sync(map2, e);
            if (e.target === map2) sync(map1, e);
            quiet = false;
        }
        
        function sync(map, e) {
            map.setView(e.target.getCenter(), e.target.getZoom(), {
                animate: false,
                reset: true
            });
        }
        </script>
        
        </body>
        </html>


