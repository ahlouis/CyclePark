<!-- page.svelte -->

<h1>Roam</h1>
<p>A personalized map for friends.</p>

<script>
  import MapboxMap from './MapboxMap.svelte';
  import Sidebar from './Sidebar.svelte';

  let markers = [];

  function handleMarkerAdded(event) {
      markers = [...markers, event.detail];
  }

  // Function to open OpenStreetMap authorization popup
  function openOSMAuthorizationPopup() {
        // Define the authorization URL provided by OpenStreetMap
        const osmAuthorizationURL = 'https://www.openstreetmap.org/oauth/authorize?oauth_token=YOUR_OAUTH_TOKEN&oauth_callback=YOUR_CALLBACK_URL';

        // Open a new window or modal with the authorization URL
        window.open(osmAuthorizationURL, 'OSM_Authorization', 'width=600,height=400');
    }
</script>

<style>
  /* Styling for the map container */
  .map-container {
      position: relative;
      width: 100%;
      height: 65vh; /* Adjust height as needed */
  }

  /* Styling for the sign-in box */
  .signin-box {
      position: absolute;
      bottom: 500px; /* Adjust as needed */
      right: 10px; /* Adjust as needed */
      background-color: #ffffff;
      padding: 10px;
      border: 1px solid #cccccc;
      border-radius: 5px;
  }

  
</style>

<!-- Map container -->
<div class="map-container">
    <!-- MapboxMap component -->
    <MapboxMap on:markerAdded={handleMarkerAdded} />
    
    <!-- Sign-in box -->
    <div class="signin-box">
        <button on:click={openOSMAuthorizationPopup}>Sign in</button>
    </div>
</div>

<!-- Sidebar component -->
<Sidebar {markers} />
