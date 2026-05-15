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

## Directions

<!-- 1. Map Container -->
<div id="map" style="height: 500px; width: 100%; border-radius: 12px; border: 1px solid #ccc;"></div>

<!-- 2. Stable Assets (Using 2.4.0 for the geocoder to avoid the 2025/2026 bugs) -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet-routing-machine@3.2.12/dist/leaflet-routing-machine.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet-control-geocoder@2.4.0/dist/Control.Geocoder.css" />

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet-routing-machine@3.2.12/dist/leaflet-routing-machine.js"></script>
<script src="https://unpkg.com/leaflet-control-geocoder@2.4.0/dist/Control.Geocoder.js"></script>

<script>
document.addEventListener("DOMContentLoaded", function() {
    var map = L.map('map').setView([41.8781, -87.6298], 13);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap'
    }).addTo(map);

    // 3. Routing Engine with fix for address search
    var control = L.Routing.control({
        waypoints: [
            L.latLng(41.8781, -87.6298), // Chicago
            L.latLng(41.8827, -87.6233)  // Millennium Park
        ],
        lineOptions: {
            styles: [{color: '#2A82DA', opacity: 0.8, weight: 5}]
        },
        routeWhileDragging: true,
        // This geocoder block is what makes address typing work
        geocoder: L.Control.Geocoder.nominatim()
    }).addTo(map);

    // Auto-fix layout for Jekyll
    setTimeout(() => { map.invalidateSize(); }, 500);
});
</script>

<style>
  /* 4. "Clean Mode" Styling */
  .leaflet-routing-container {
    width: 300px;
    background-color: rgba(255, 255, 255, 0.9);
    font-family: sans-serif;
    font-size: 13px;
    border: none !important;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    border-radius: 8px;
  }
  .leaflet-routing-alt {
    max-height: 250px; /* Limits the list so it doesn't cover the whole map */
  }
</style>

---
