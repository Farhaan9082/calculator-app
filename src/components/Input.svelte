<script>
    export let ScreenInput
</script>

<section>
    <input class="input__bar" type="text" bind:value={ScreenInput} readonly="true">
</section>

<style>
    section {
        margin-bottom: 20px;
    }

    .input__bar {
        width: 100%;
        padding: 20px;
        background-color: var(--T1-screen);
        border: none;
        outline: none;
        font-size: 2rem;
        text-align: right;
        color: white;
        border-radius: 8px;
    }

    :global(body.light-mode) .input__bar {
        background-color: var(--T2-screen);
        color: var(--T2-text-dark);
    }

    :global(body.neon-mode) .input__bar {
        background-color: var(--T3-keypad);
        color: var(--T3-text-yellow);
    }
</style>