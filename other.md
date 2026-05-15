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

<!-- 1. Map Container -->
<div id="map" style="height: 450px; width: 100%; border-radius: 8px; margin-bottom: 20px; border: 1px solid #ddd;"></div>

<!-- 2. Load Leaflet & Geocoder Assets -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet-control-geocoder/dist/Control.Geocoder.css" />

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet-control-geocoder/dist/Control.Geocoder.js"></script>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    // Initialize map
    var map = L.map('map').setView([41.8781, -87.6298], 12);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; OpenStreetMap contributors'
    }).addTo(map);

    // Create a global marker variable so we can move it later
    var marker = L.marker([41.8781, -87.6298]).addTo(map)
      .bindPopup('Daniel Burnham\'s Chicago')
      .openPopup();

    // 3. Add the Search Control (Geocoder)
    var geocoder = L.Control.geocoder({
      defaultMarkGeocode: false, // Prevents creating a second marker automatically
      placeholder: "Type an address...",
      errorMessage: "Address not found."
    })
    .on('markgeocode', function(e) {
      var latlng = e.geocode.center;
      
      // Move the existing marker to the new location
      marker.setLatLng(latlng);
      marker.bindPopup(e.geocode.name).openPopup();
      
      // Center the map on the new location
      map.setView(latlng, 15); 
    })
    .addTo(map);
    
    // Fix for display glitches in Jekyll themes
    setTimeout(function(){ map.invalidateSize()}, 500);
  });
</script>

---
