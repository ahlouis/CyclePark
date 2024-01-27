<script context="module">
    import 'leaflet/dist/leaflet.css';
  </script>
  
  <script>
    import { onMount } from 'svelte';
  
    onMount(() => {
      // Use dynamic import to ensure this code runs only on the client side
      import('leaflet').then((L) => {
        const map = L.map('map').setView([51.505, -0.09], 13);
  
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
          attribution: '© OpenStreetMap contributors',
        }).addTo(map);
      });
    });
  </script>
  
  <style>
    #map {
      height: 400px;
    }
  </style>
  
  <div id="map"></div>
  