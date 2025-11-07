<script lang="ts">
	import { WEBUI_BASE_URL } from '$lib/constants';

	export let className = 'size-8';
	export let src = `${WEBUI_BASE_URL}/static/favicon.png`;
	
	// Check if it's the default favicon/logo
	$: isDefaultLogo = src === `${WEBUI_BASE_URL}/static/favicon.png` || 
	                   src === `${WEBUI_BASE_URL}/favicon.png` || 
	                   src === '' ||
	                   src === `${WEBUI_BASE_URL}/doge.png`;
</script>

{#if isDefaultLogo}
	<div class="{className} rounded-full bg-gradient-to-br from-blue-600 to-blue-700 flex items-center justify-center">
		<span class="text-white font-bold" style="font-size: {className.includes('size-8') ? '0.75rem' : className.includes('size-5') ? '0.5rem' : '0.6rem'}">AG</span>
	</div>
{:else}
	<img
		crossorigin="anonymous"
		aria-hidden="true"
		src={src.startsWith(WEBUI_BASE_URL) ||
			  src.startsWith('https://www.gravatar.com/avatar/') ||
			  src.startsWith('data:') ||
			  src.startsWith('/')
			? src
			: `${WEBUI_BASE_URL}/user.png`}
		class=" {className} object-cover rounded-full"
		alt="profile"
		draggable="false"
	/>
{/if}
