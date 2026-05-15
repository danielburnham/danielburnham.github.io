---
layout: page
title: Other
---

## Building

I like to build things to observe and measure other things.

<video width="100%" controls>
  <source src="/images/DanielLabTimeLapse.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

---

## Art

### Python Generated Art

<table style="width:100%; border-collapse: collapse; border: none;">
  <tr style="border: none;">
    <td style="width:33%; border: none; padding: 5px;">
      <img src="/images/pattern2blacklinescirclewhitecircle_small.png" alt="Art 1" style="width:100%;">
    </td>
    <td style="width:33%; border: none; padding: 5px;">
      <img src="/images/WhiteCirclesonblack_small.png" alt="Art 2" style="width:100%;">
    </td>
    <td style="width:33%; border: none; padding: 5px;">
      <img src="/images/pattern1blackcircle_small.png" alt="Art 3" style="width:100%;">
    </td>
  </tr>
</table>

---

## Reachability Map

<div id="map" style="height: 500px; width: 100%; border-radius: 12px; border: 1px solid #ccc;"></div>

<!-- 1. Load Leaflet and Geocoder -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet-control-geocoder/dist/Control.Geocoder.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet-control-geocoder/dist/Control.Geocoder.js"></script>

<script>
document.addEventListener("DOMContentLoaded", function() {
    // --- CONFIGURATION ---
    const ORS_API_KEY = 'eyJvcmciOiI1YjNjZTM1OTc4NTExMTAwMDFjZjYyNDgiLCJpZCI6IjgzOTI0YWMxM2FmMjQ0YTM5MzU0YTZjOGYxZTQ4YTZiIiwiaCI6Im11cm11cjY0In0='; // <--- PASTE YOUR KEY HERE
    const map = L.map('map').setView([41.8781, -87.6298], 12);
    let isochroneLayer;
    let startMarker;

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap | OpenRouteService'
    }).addTo(map);

    // 2. Function to fetch the "Time Patch"
    async function updateIsochrone(latlng, minutes = 30) {
        // Remove old layer if it exists
        if (isochroneLayer) map.removeLayer(isochroneLayer);
        
        const seconds = minutes * 60;
        const url = `https://api.openrouteservice.org/v2/isochrones/driving-car`;
        
        const body = {
            locations: [[latlng.lng, latlng.lat]],
            range: [seconds],
            range_type: "time"
        };

        try {
            const response = await fetch(url, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': ORS_API_KEY
                },
                body: JSON.stringify(body)
            });
            const data = await response.json();
            
            // 3. Draw the colored patch
            isochroneLayer = L.geoJSON(data, {
                style: {
                    color: '#ff7800',
                    weight: 2,
                    opacity: 0.65,
                    fillColor: '#ff7800',
                    fillOpacity: 0.3
                }
            }).addTo(map);
            
            map.fitBounds(isochroneLayer.getBounds());
        } catch (e) {
            alert("Error fetching reachability data. Check your API key!");
        }
    }

    // 4. Add Search Bar to set start location
    const geocoder = L.Control.geocoder({ defaultMarkGeocode: false })
        .on('markgeocode', function(e) {
            const latlng = e.geocode.center;
            if (startMarker) startMarker.setLatLng(latlng);
            else startMarker = L.marker(latlng).addTo(map);
            updateIsochrone(latlng);
        })
        .addTo(map);

    // Click map to set start
    map.on('click', function(e) {
        if (startMarker) startMarker.setLatLng(e.latlng);
        else startMarker = L.marker(e.latlng).addTo(map);
        updateIsochrone(e.latlng);
    });

    setTimeout(() => { map.invalidateSize(); }, 500);
});
</script>

---
