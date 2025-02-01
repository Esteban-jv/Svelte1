<script lang="ts">
    import PageTwo from "./pageTwo.svelte";
    let number = $state(0);
    // let stringShow = $derived(number === 0 ? 'Why not try to click the button below?' : `You've clicked ${number} times`);
    let stringShow = $derived.by(() => calculateUserInformation(number)); // Mientras no usemos nada de $derived o otras cosas de svelte, podríamos no usar $state

    const onclick = () => {
        number ++;
    }
    function calculateUserInformation (number: number) {
        if (number === 0) {
            return 'Why not try to click the button below?';
        } else if (number === 1) {
            return `You've clicked exactly one time`;
        }
        return `You've clicked ${number} times`;
    }

    // -----------------------------------------------
    let userName = $state("")
</script>
<h1 class="text-2xl">{number}</h1>
<button class="bg-green-400 p-2 text-gray-700 rounded-md hover:bg-green-600" {onclick}>Click me</button>
<div>
    <p>{ stringShow }</p>
</div>
<input type="text" name="userName" id="userName" bind:value={userName} />
<p>{ userName }</p>

<PageTwo />