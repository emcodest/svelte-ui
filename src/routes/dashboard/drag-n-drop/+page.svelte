<script lang="ts">
  import { Heading } from "flowbite-svelte";
   import {flip} from "svelte/animate";
    import {dndzone} from "svelte-dnd-action";
    import {onMount} from "svelte"
    let items = $state([
        {id: 1, name: "item1"},
        {id: 2, name: "item2"},
        {id: 3, name: "item3"},
        {id: 4, name: "item4"}
    ]);
    const flipDurationMs = 300;
    function handleDndConsider(e: any) {
        items = e.detail.items;
    }
    function handleDndFinalize(e: any) {
        items = e.detail.items;
    }
    onMount(() => {
      
        items.reverse()
    })
</script>
<!-- template -->
<main class="p-5">
    <Heading>Drag and Drop</Heading>
    <section  use:dndzone="{{items, flipDurationMs}}" onconsider="{handleDndConsider}" onfinalize="{handleDndFinalize}">
    {#each items as item(item.id)}
    <div animate:flip="{{duration: flipDurationMs}}">{item.name}</div>
    {/each}
</section>
</main>



<style>
    section {
        width: 90%;
        /* padding: 0.3em; */
        border: 1px solid black;
        /* this will allow the dragged element to scroll the list although starting in version 0.9.41 the lib would detect any scrollable parent*/
        overflow: scroll;
        height: 200px;
    }
    div {
        width: 50%;
        padding: 0.2em;
        border: 1px solid blue;
        margin: 0.15em 0;
    }
</style>
