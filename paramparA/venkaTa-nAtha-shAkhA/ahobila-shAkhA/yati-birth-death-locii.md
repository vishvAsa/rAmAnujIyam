+++
title = "Yati birth death locii"
+++

<div id="map" style="height: 500px; width: 100%;"></div>

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet-kmz/dist/leaflet-kmz.js"></script>

<script>
    const map = L.map('map').setView([0, 0], 2);

    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    const kmz = L.kmzLayer();
    kmz.load('yati-birth-death-locii.kmz');
    kmz.addTo(map);

    kmz.on('load', function() {
        map.fitBounds(kmz.getBounds());
    });
</script>