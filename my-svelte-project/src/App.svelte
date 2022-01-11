<script>
  import schools from "./schools.json";
  let selectedSchool;
</script>

<main>
  {#if selectedSchool}
    <p>
      <!-- svelte-ignore a11y-invalid-attribute -->
      <a on:click={() => (selectedSchool = null)} href="#">
        Go back to school list
      </a>
    </p>
    <h1>School is {selectedSchool.SCHOOLNAME}</h1>
    <p>The education level is {selectedSchool.SCH_TYPE}</p>
    <p>The principal is {selectedSchool.PRINCIPAL}</p>
  {:else}
    <ul>
      <h3>NYC school list</h3>
      <p>Select a school to read some information about it</p>
      {#each schools as school}
        <li>
          <!-- svelte-ignore a11y-invalid-attribute -->
          <a on:click={() => (selectedSchool = school)} href="#">
            {school.SCHOOLNAME}
          </a>
        </li>
      {/each}
    </ul>
  {/if}

  <!-- continue from https://www.youtube.com/watch?v=fm2r6JY5h9E&t=396s -->
</main>

<style>
  main {
    text-align: left;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
