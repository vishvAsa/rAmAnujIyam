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

    const kmz = L.kmzLayer();
    kmz.load('../yati-birth-death-locii.kmz');
    kmz.addTo(map);

    kmz.on('load', function() {
        map.fitBounds(kmz.getBounds());
    });
</script>