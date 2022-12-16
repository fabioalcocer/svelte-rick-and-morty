<script>
  let characters = []

  const loadCharacters = async () => {
    const res = await fetch(
      'https://rickandmortyapi.com/api/character'
    )
    const data = await res.json()
    characters = data.results
  }

  loadCharacters()
</script>

<h1>Rick and Morty Svelte Practice</h1>

<div>
  {#each characters as character}
    <div>
      <img src={character.image} alt={character.name} />
      <h2>{character.name}</h2>
      <p>{character.species}</p>
    </div>
  {/each}
</div>
