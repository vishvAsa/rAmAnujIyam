+++
title = "Yati birth death locii"
js_extras = ["leaflet"]
+++

<div id="map" style="height: 500px; width: 100%;"></div>

<script>
const map = L.map('map').setView([0, 0], 2);

L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
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