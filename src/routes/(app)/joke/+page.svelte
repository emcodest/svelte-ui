<script lang="ts">
    import {onMount} from "svelte"
    // import random joke card
    import RandomJoke from "$lib/components/RandomJoke.svelte";
let title = "Read Jokes";
onMount(() => {

  //  alert("looks good ...")
    // cleanup
    return () => {
       // alert("destroyed ...")
    }
})

</script>

<div id="wrapper">

   <div>
     <h2>Read a Joke</h2>
     <RandomJoke />
   </div>

</div>
<style>
#wrapper  {
   margin: 0 auto;
   width: 80%;
}
</style>
