<script lang="ts">
	export let onClick: () => void;
</script>

<button
	class="border-2 border-white bg-white text-black font-medium rounded-lg text-sm px-4.5 py-2.5 w-[15rem]"
	on:click={onClick}
>
	<slot />
</button>
