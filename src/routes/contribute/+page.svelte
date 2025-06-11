<iframe
	id="myIframe"
	src="http://localhost:5173?content_only=1"
	class="w-full border-0"
	title="Contribute to Open Food Facts"
	scrolling="no"
	frameborder="0"
></iframe>

<script>
  // Listen for messages from the iframe
  window.addEventListener('message', function(event) {
    // Optionally check the origin of the message for security
    // if (event.origin !== 'https://world.openfoodfacts.org') return;
    const iframe = document.getElementById('myIframe');
    if (event.data.frameHeight && iframe) {
      console.log('Received frameHeight:', event.data.frameHeight);
      iframe.style.height = event.data.frameHeight + 'px';
    }
  });
</script>
