
<script context="module">
    import 'mapbox-gl/dist/mapbox-gl.css';
  </script>
  
  <script>
    import { onMount, onDestroy } from 'svelte';
    import mapboxgl from 'mapbox-gl';
  
    const accessToken = 'pk.eyJ1IjoiaGVyYmFhbCIsImEiOiJjbHJ3Ynd6ZWIwbXB6MmlvNXJneWt3YTFxIn0.PygutsfcExif2Qo0xfikjg';
  
    let map;
    let markers = [];
  
    onMount(() => {
      mapboxgl.accessToken = accessToken;
  
      
      map = new mapboxgl.Map({
        container: 'map',
        style: 'mapbox://styles/herbaal/cls3jw96401yf01p1ah1lcri1',
        center: [-81.6915, 36.2199],
        zoom: 15
      });
  
      map.addControl(new mapboxgl.NavigationControl());
  
      map.on('click', handleMapClick);
  
      // Add any existing markers from previous sessions (you might fetch these from a database)
      markers.forEach(marker => marker.addTo(map));
    });
  
    onDestroy(() => {
      // Cleanup when the component is destroyed
      if (map) {
        map.off('click', handleMapClick);
        markers.forEach(marker => marker.remove());
      }
    });
  
    function handleMapClick(event) {
      const { lng, lat } = event.lngLat;
  
      // Create a marker
      const marker = new mapboxgl.Marker()
        .setLngLat([lng, lat])
        .addTo(map);
  
      // Add the marker to the markers array
      markers.push(marker);
    }
  </script>
  
  <style>
    #map {
      height: 720px;
      width: calc(950px);
      position: fixed;
      top: 2;
      right: 0;
    }
    
  </style>
  
  <div id="map"></div>
  