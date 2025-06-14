<script lang="ts">
	import Message from './Message.svelte';

	import { getI18nContext } from '$lib/i18n';

	const i18n = getI18nContext();

	export let messages = [];
</script>

<div class="py-3 space-y-3">
	{#each messages as message, idx}
		<Message
			{message}
			{idx}
			onDelete={() => {
				messages = messages.filter((message, messageIdx) => messageIdx !== idx);
			}}
		/>
	{/each}
</div>
