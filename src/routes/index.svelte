<script lang="ts">
// @ts-ignore

import {HsvPicker} from 'svelte-color-picker';

function colorCallback(rgba:any) {
    console.log(rgba.detail)
}
</script>
<HsvPicker on:colorChange={colorCallback} startColor={"#FBFBFB"}/>
<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
