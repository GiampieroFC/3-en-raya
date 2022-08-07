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

<main>
  <div class="container">
    
    {#if winner}
      <p class="ganador">El ganador es {winner}</p>
    {:else if a && b && c && d && e && f && g && h && i}
      <p class="tablas">Tablas, no hay ganador 😐</p>
    {:else}
      <p class="turno">Es el turno de {mark}</p>
    {/if}
      

<div class="game">
  <div>
    <Box {mark} on:newMark={changes} on:valor={(event) => {a = event.explicitOriginalTarget.textContent}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {b = event.explicitOriginalTarget.textContent}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {c = event.explicitOriginalTarget.textContent}}/>
  </div>
  <div>
    <Box {mark} on:newMark={changes} on:valor={(event) => {d = event.explicitOriginalTarget.textContent}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {e = event.explicitOriginalTarget.textContent}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {f = event.explicitOriginalTarget.textContent}}/>
  </div>
  <div>
    <Box {mark} on:newMark={changes} on:valor={(event) => {g = event.explicitOriginalTarget.textContent}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {h = event.explicitOriginalTarget.textContent}}/>
    <Box {mark} on:newMark={changes} on:valor={(event) => {i = event.explicitOriginalTarget.textContent}}/>
  </div> 
  </div>
  <div class="boton">
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

.ganador {
  color: green;
  font-size: 2.5rem;
}
.tablas {
  color: darkslategray;
  font-size: 2.5rem;
}
.turno {
  color: black;
  font-size: 2.5rem;
}

.boton {
  display: flex;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
}

.container {
  /* border: 1px solid black; */
  box-sizing: border-box;

}

.game {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
