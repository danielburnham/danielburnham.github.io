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

## Location

<!-- 1. The Container (Must come BEFORE the script) -->
<div id="map" style="height: 400px; width: 100%; border-radius: 8px; margin-bottom: 20px; border: 1px solid #ddd;"></div>

<!-- 2. Leaflet Assets -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<!-- 3. The Logic -->
<script>
  document.addEventListener("DOMContentLoaded", function() {
    // Initialize map
    var map = L.map('map').setView([41.8781, -87.6298], 12);

    // Add Tiles
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

    // Add Marker
    L.marker([41.8781, -87.6298]).addTo(map)
      .bindPopup("<b>Daniel Burnham's Chicago</b><br>Make no little plans.")
      .openPopup();
      
    // Fix for gray tiles/display glitches on some Jekyll themes
    setTimeout(function(){ map.invalidateSize()}, 400);
  });
</script>

---
