<script>
	import { onMount } from 'svelte';

	onMount(() => {
		// Listen for messages from the iframe
		window.addEventListener('message', function (event) {
			const iframe = document.getElementById('myIframe');
			if (event.data.frameHeight && iframe) {
				console.log('Received frameHeight:', event.data.frameHeight);
				iframe.style.height = event.data.frameHeight + 'px';
			}
		});
	});

	// "http://localhost:5173?content_only=1"
	// "http://world.openfoodfacts.localhost/discover?content_only=1"
</script>

<iframe
	id="myIframe"
	src="http://localhost:5173?content_only=1"
	class="w-full border-0"
	title="Contribute to Open Food Facts"
	scrolling="no"
	frameborder="0"
></iframe>
