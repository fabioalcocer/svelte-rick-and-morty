<script>
  import Character from './lib/Character.svelte'

  let characters = []
  let page = 1

  const loadCharacters = async () => {
    const res = await fetch(
      `https://rickandmortyapi.com/api/character?page=${page}`
    )
    const data = await res.json()
    characters = data.results
  }

  const nextPage = () => {
    page++
    loadCharacters()
  }

  const prevPage = () => {
    page--
    loadCharacters()
  }

  loadCharacters()
</script>

<h1 class="title">Rick and Morty Svelte Practice</h1>

<div class="container">
  <div class="btns">
    <button class="btn" on:click={prevPage} disabled={page === 1}>Previous</button
    >
    <button class="btn" on:click={nextPage}>Next</button>
  </div>
  <div class="grid">
    {#each characters as character}
      <Character {character} />
    {/each}
  </div>
</div>
