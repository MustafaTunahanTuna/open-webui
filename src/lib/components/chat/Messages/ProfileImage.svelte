<script lang="ts">
	import { WEBUI_BASE_URL } from '$lib/constants';

	export let className = 'w-full';
	export let src = `${WEBUI_BASE_URL}/static/favicon.png`;
	
	// Check if it's the default favicon/logo
	$: isDefaultLogo = src === `${WEBUI_BASE_URL}/static/favicon.png` || 
	                   src === `${WEBUI_BASE_URL}/favicon.png` || 
	                   src === '' ||
	                   src === `${WEBUI_BASE_URL}/doge.png`;
</script>

{#if isDefaultLogo}
	<div class="{className} w-[70px] flex items-center justify-center">
		<img 
			src="{WEBUI_BASE_URL}/assets/svgs/anadolu-grubu-tr-beyaz.svg" 
			alt="Anadolu Grubu" 
			class="{className} w-[70px] dark:block hidden"
			draggable="false"
		/>
		<img 
			src="{WEBUI_BASE_URL}/assets/svgs/anadolu-grubu-tr-renkli.svg" 
			alt="Anadolu Grubu" 
			class="{className} w-[70px] dark:hidden"
			draggable="false"
		/>
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
