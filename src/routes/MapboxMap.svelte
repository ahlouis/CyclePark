<!-- MapboxMap.svelte -->

<script context="module">
  import 'mapbox-gl/dist/mapbox-gl.css';
</script>

<script>
  import { onMount, onDestroy, createEventDispatcher } from 'svelte';
  import mapboxgl from 'mapbox-gl';

  const accessToken = 'pk.eyJ1IjoiaGVyYmFhbCIsImEiOiJjbHJ3Ynd6ZWIwbXB6MmlvNXJneWt3YTFxIn0.PygutsfcExif2Qo0xfikjg';

  export let markers = [];

  const dispatch = createEventDispatcher();

  let map;

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
  });

  onDestroy(() => {
      if (map) {
          map.off('click', handleMapClick);
      }
  });

  function handleMapClick(event) {
      const { lng, lat } = event.lngLat;

      const title = prompt('Enter title:');
      const description = prompt('Enter description:');
      if (title !== null && description !== null) {
          const marker = new mapboxgl.Marker()
              .setLngLat([lng, lat])
              .addTo(map)
              .setPopup(new mapboxgl.Popup().setHTML(`<h3>${title}</h3><p>${description}</p>`));

          // Emit an event to notify the parent component about the new marker
          dispatch('markerAdded', { title, description });

          // Allow editing the title and description when clicking on the marker
          marker.getElement().addEventListener('click', () => {
              const newTitle = prompt('Enter title:', title);
              const newDescription = prompt('Enter description:', description);
              if (newTitle !== null && newDescription !== null) {
                  marker.setPopup(new mapboxgl.Popup().setHTML(`<h3>${newTitle}</h3><p>${newDescription}</p>`));
              }
          });
      }
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
