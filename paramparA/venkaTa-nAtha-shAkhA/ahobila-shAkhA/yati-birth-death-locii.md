+++
title = "Yati birth death locii"
js_extras = ["leaflet"]
+++

<div id="map" style="height: 500px; width: 100%;"></div>

<script>
const map = L.map('map').setView([0, 0], 2);

// Use Esri World Street Map for dense, clear city and geographic labels at all zoom levels
L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
    maxZoom: 17,
    attribution: 'sundara-mAlola'
}).addTo(map);

const kmz = L.kmzLayer().addTo(map);

kmz.on('load', function(e) {
    // Add the parsed features to the map
    e.layer.addTo(map);

    // Fit bounds safely
    const bounds = e.layer.getBounds();
    if (bounds && bounds.isValid()) {
        map.fitBounds(bounds);
    }
});


// Load your KMZ file
kmz.load('../yati-birth-death-locii.kml');
</script>