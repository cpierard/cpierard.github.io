---
layout: post
title:  "Bayesian Inference South Atlantic"
permalink: /projects/bayesian-inference/
---

<!DOCTYPE html>
<html>
<head>
    <title>Interactive Map</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"/>
    <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    <style>
        #mapid { height: 400px; }
    </style>
</head>
<body>
    <div id="mapid"></div>
    <script>
        var mymap = L.map('mapid').setView([51.505, -0.09], 13);
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap contributors</a>',
            maxZoom: 18,
        }).addTo(mymap);

        // Example: Add a marker and show data on hover
        var marker = L.marker([51.5, -0.09]).addTo(mymap);
        marker.bindPopup("Basic information displayed on hover.").openPopup();

        // To show data on hover instead of on click, you can use the mouseover event
        marker.on('mouseover', function(e) {
            this.openPopup();
        });
        marker.on('mouseout', function(e) {
            this.closePopup();
        });
    </script>
</body>
</html>