<script lang="ts">
	import TagInput from './Tags/TagInput.svelte';
	import TagList from './Tags/TagList.svelte';
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	import { getI18nContext } from '$lib/i18n';

	const i18n = getI18nContext();

	export let tags = [];
</script>

<ul class="flex flex-row flex-wrap gap-1 line-clamp-1">
	<TagList
		{tags}
		on:delete={(e) => {
			dispatch('delete', e.detail);
		}}
	/>

	<TagInput
		label={tags.length == 0 ? $i18n.t('Add Tags') : ''}
		on:add={(e) => {
			dispatch('add', e.detail);
		}}
	/>
</ul>
