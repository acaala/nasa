<script>
    export let data
    export let links
</script>

{#if links != undefined}
<img src="{links[0].href}" alt="{data[0].nasa_id}">
{/if}
<p>{data[0].location}</p>
<p>{data[0].description}</p>

<style>

</style>