<!-- page.svelte -->



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
  

  /* Styling for the sign-in box */
  .signin-box {
      width: 230px;
      height: 30px;
      position: absolute;
      padding: 3px;
      bottom: 20px; /* Adjust as needed */
      left: 150px; /* Adjust as needed */
      background-color: #ffffff;
      border: 1px solid hsl(0, 0%, 80%);
      box-shadow: inset 0 3px 6px rgba(0,0,0,0.16), 0 4px 6px rgba(0,0,0,0.45);
      border-radius: 10px;
      font-family: "Monaco", "Courier New", monospace;

  }


  
  .logo {      
    width: 70px;
    height: 65px;
    position: absolute;
    bottom: 5px; /* Adjust as needed */
    left: 30px; /* Adjust as needed */
    border: 1px solid hsl(0, 0%, 80%);
    box-shadow: inset 0 3px 6px rgba(0,0,0,0.16), 0 4px 6px rgba(0,0,0,0.45);
    border-radius: 10px;
    background-image: url('./logo.gif'); /* Fixed typo in background-image */
    background-size: contain; /* Ensure the image fits within the container */
    background-repeat: no-repeat; /* Prevent the image from repeating */
    }

</style>

<!-- Map container -->
<div class="map-container">
    <!-- MapboxMap component -->
    <MapboxMap on:markerAdded={handleMarkerAdded} />
    
    <!-- Sign-in box -->
    <div class="signin-box">
        <button on:click={openOSMAuthorizationPopup}>Sign in | Not logged in </button>
    </div>
    <div class="logo"></div> 
</div>


<!-- Sidebar component -->
<Sidebar {markers} />
