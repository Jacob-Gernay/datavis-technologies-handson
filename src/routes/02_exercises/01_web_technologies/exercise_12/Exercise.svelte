<script>
	let clicked = false;
</script>

<div>
	<button class="btn btn-primary" on:click={() => (clicked = true)}>
		click here
	</button>
	<!--  -->
</div>

<div>
	{#if clicked==true}
	You have clicked the button!
	{:else}
	You have to click the button!
	{/if}
</div>