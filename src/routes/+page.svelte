<script lang="ts">
	import { goto } from '$app/navigation';
	import { page } from '$app/stores';
	import * as m from '$lib/paraglide/messages.js';
	import { languageTag } from '$lib/paraglide/runtime.js';
	let language: 'en' | 'de' = $state(languageTag());

	$effect(() => {
		if (language === 'en') {
			goto('/');
		}
		if (language !== 'en' && languageTag() !== $page.url.pathname) {
			goto(language);
		}
	});
</script>

<select bind:value={language}>
	<option value="en">English</option>
	<option value="de">German</option>
</select>
<h1>{m.title()}</h1>
<p>{m.description()}</p>
