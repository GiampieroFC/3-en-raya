<script>
  import Box from './lib/Box.svelte'
  import ButtonReset from "./lib/ButtonReset.svelte";

  let a, b, c, d, e, f, g, h, i;

  let mark = '❌'

  let winner;

  const changes = () => {
      if (mark === '❌') {
        return mark = '⭕'
      }
      if (mark === '⭕') {
        return mark = '❌'
      }
  }
  
  
  $: {
    if (a && b && c && a === b && b === c) {winner = b}
    if (d && e && f && d === e && e === f) {winner = e}
    if (g && h && i && g === h && h === i) {winner = h}
    if (a && d && g && a === d && d === g) {winner = d}
    if (b && e && h && b === e && e === h) {winner = e}
    if (c && f && i && c === f && f === i) {winner = f}
    if (a && e && i && a === e && e === i) {winner = e}
    if (c && e && g && c === e && e === g) {winner = e}  
    if (winner) {mark = ''}
  }


</script>

<main class="position-relative">
  <div class="position-absolute top-50 start-50 translate-middle">
    
    {#if winner}

   <div class="alert alert-success" role="alert"><h2>El ganador es {winner}</h2>
  
</div>




    {:else if a && b && c && d && e && f && g && h && i}
      <div class="alert alert-dark" role="alert"> <h2>Tablas, no hay ganador 😐</h2>
  
</div>
    {:else}
      <div class="alert alert-light" role="alert"> <h2>Es el turno de {mark}</h2>
        
</div>

    {/if}
      

<div class="game">
  <div>
    <Box {mark} on:newMark={changes} on:valor={(event) => {a = event.detail.target.innerHTML}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {b = event.detail.target.innerHTML}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {c = event.detail.target.innerHTML}}/>
  </div>
  <div>
    <Box {mark} on:newMark={changes} on:valor={(event) => {d = event.detail.target.innerHTML}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {e = event.detail.target.innerHTML}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {f = event.detail.target.innerHTML}}/>
  </div>
  <div>
    <Box {mark} on:newMark={changes} on:valor={(event) => {g = event.detail.target.innerHTML}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {h = event.detail.target.innerHTML}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {i = event.detail.target.innerHTML}}/>
  </div> 
  </div>
  <div class="d-flex justify-content-evenly">
    <ButtonReset />
  </div>
</div>
</main>

<style>
  
main {
  padding: auto;
  width: 96vw;
  height: 96vh;
  display: flexbox;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
}

.game {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
