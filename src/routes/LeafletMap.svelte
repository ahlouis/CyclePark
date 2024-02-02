<script context="module">
  import 'leaflet/dist/leaflet.css';
</script>

<script>
  import { onMount } from 'svelte';

  let places = [
    { id: 1, name: 'Ale House', coordinates: [36.2179, -81.6861] },
    { id: 2, name: 'Place 2', coordinates: [36.2299, -81.7015] },
    // Add more places as needed
  ];

  const showMarker = (coordinates) => {
    // Logic to highlight or navigate to the marker on the map
  };

  onMount(() => {
    // Use dynamic import to ensure this code runs only on the client side
    import('leaflet').then((L) => {
      const map = L.map('map').setView([36.2199, -81.6915], 16);

      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap contributors',
      }).addTo(map);

      // Add markers to the map based on the places array
      places.forEach((place) => {
        L.marker(place.coordinates).addTo(map).bindPopup(place.name);
      });
    });
  });
</script>

<style>
  #map {
    position: fixed;
    height: 900px;
    width: calc(90% - 400px); /* Adjust width to leave space for the sidebar */
    position: fixed;
    top: 0; /* Adjust the top position as needed */
    right: 0;
  }

  #sidebar {
    position: fixed;
    top: 20;
    left: 0;
    width: 540px;
    height: 100%;
    background-color: #f1f1f1;
    overflow-y: auto;
    padding: 20px;
    z-index: 1000;
  }

  .place {
    margin-bottom: 10px;
    cursor: pointer;
  }

  h2 {
    font-family: "Lucida Console", "Courier New", monospace;
    width: 200px;
    font-size: 20px;

  }
</style>

<div id="sidebar">
  <h2>Nearby Places</h2>
  {#each places as place (place.id)}
    <div class="place" on:click={() => showMarker(place.coordinates)}>
      {place.name}
    </div>
  {/each}
</div>

<div id="map"></div>
