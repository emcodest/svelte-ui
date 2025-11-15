<script lang="ts">
    let btn_name = "Click Me"
   export let myname : string = "Emcde"
    function CallMe() {
        alert("my name is: "+myname)
    }
</script>
<button on:click={CallMe}>THIS IS A BUTTON - {btn_name}</button>