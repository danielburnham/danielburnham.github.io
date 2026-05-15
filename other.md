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

## Directions Map

<!-- 1. Map Container -->
<div id="map" style="height: 500px; width: 100%; border-radius: 8px; margin-bottom: 20px; border: 1px solid #ddd;"></div>

<!-- 2. Load Leaflet & Routing Assets -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet-routing-machine@latest/dist/leaflet-routing-machine.css" />

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet-routing-machine@latest/dist/leaflet-routing-machine.js"></script>
<!-- Geocoder is needed so you can type addresses instead of just clicking -->
<script src="https://unpkg.com/leaflet-control-geocoder/dist/Control.Geocoder.js"></script>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // Initialize map
    var map = L.map('map').setView([41.8781, -87.6298], 12);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    // 3. Add Routing Control
    var control = L.Routing.control({
      waypoints: [
        L.latLng(41.8781, -87.6298), // Default Start: Chicago
        L.latLng(41.8827, -87.6233)  // Default End: Millennium Park
      ],
      routeWhileDragging: true,
      geocoder: L.Control.Geocoder.nominatim(), // Allows typing addresses
      router: L.Routing.osrmv1({
        serviceUrl: 'https://router.project-osrm.org/route/v1'
      })
    }).addTo(map);

    // Fix for display glitches in Jekyll themes
    setTimeout(function(){ map.invalidateSize()}, 500);
  });
</script>

<style>
  /* Optional: Adjust the size/look of the directions panel */
  .leaflet-routing-container {
    background-color: white;
    padding: 10px;
    border-radius: 5px;
    box-shadow: 0 1px 5px rgba(0,0,0,0.4);
    max-height: 400px;
    overflow-y: auto;
  }
</style>

---
