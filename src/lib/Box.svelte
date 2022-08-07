<script>
  
  export let mark;

  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();

  const clickMark = (event) => {
  
  event.target.innerHTML = mark
  dispatch("newMark")
  dispatch("valor", event)

  }

</script>

<div {mark} on:click|once={clickMark}>

</div>

<svelte:options accessors/>

<style>
  div {
    font-size: 3.5rem;
    width: 5rem;
    height: 5rem;
    border: 1px solid whitesmoke;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
