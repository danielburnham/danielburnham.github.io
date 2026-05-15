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

<!-- Map Container -->
<div id="map" style="height: 400px; width: 100%; border-radius: 8px; margin-bottom: 20px; border: 1px solid #ddd;"></div>

<!-- Load Leaflet Assets -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
  // Initialize map - centered on Chicago (41.87, -87.62)
  var map = L.map('map').setView([41.8781, -87.6298], 12);

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);

  // Add a marker
  L.marker([41.8781, -87.6298]).addTo(map)
    .bindPopup('Daniel Burnham\'s Chicago')
    .openPopup();
</script>

---
