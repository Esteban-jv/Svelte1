<script lang="ts">
    let peopleWaiting = $state(['Esteban', 'Juan']);
    $inspect(peopleWaiting);
</script>

<h1 class="text-2xl">Page Two</h1>
{#snippet userInput(personId: string)}
    <li>Id for person waiting: {personId}</li>
{/snippet}

<ul>
    {#each peopleWaiting as person}
        {@render userInput(person)}
    {/each}
</ul>

<button
    onclick="{() => peopleWaiting.push(new Date().toLocaleTimeString())}"
>I'm waiting too</button>