<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher()

    const HandleValue = (value) => {
        dispatch('insert-value', value)
    }

    const HandlePoint = (value) => {
        dispatch('insert-point', value)
    }

    const HandleReset = () => {
        dispatch('reset-value')
    }

    const HandleDelete = () => {
        dispatch('delete-value')
    }

    const HandleOutput = () => {
        dispatch('output-value')
    }
</script>

<section class="grid">
    <button on:click={() => HandleValue(7)}>7</button>
    <button on:click={() => HandleValue(8)}>8</button>
    <button on:click={() => HandleValue(9)}>9</button>
    <button class="blue" on:click={() => HandleDelete()}>DEL</button>
    <button on:click={() => HandleValue(4)}>4</button>
    <button on:click={() => HandleValue(5)}>5</button>
    <button on:click={() => HandleValue(6)}>6</button>
    <button on:click={() => HandleValue('+')}>+</button>
    <button on:click={() => HandleValue(1)}>1</button>
    <button on:click={() => HandleValue(2)}>2</button>
    <button on:click={() => HandleValue(3)}>3</button>
    <button on:click={() => HandleValue('-')}>-</button>
    <button on:click={() => HandlePoint('.')}>.</button>
    <button on:click={() => HandleValue(0)}>0</button>
    <button on:click={() => HandleValue('/')}>/</button>
    <button on:click={() => HandleValue('*')}>&times;</button>
    <button class="large blue" on:click={() => HandleReset()}>RESET</button>
    <button class="large red" on:click={() => HandleOutput()}>=</button>
</section>

<style>
    .grid {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        padding: 25px;
        grid-gap: 20px;
        background-color: var(--T1-keypad);
        border-radius: 8px;
    }

    button {
        background-color: var(--T1-gray);
        color: var(--T1-text-dark);
        font-size: 1.5rem;
        padding-top: 12px;
        padding-bottom: 9px;
        border-radius: 9px;
        cursor: pointer;
        border: none;
        border-bottom: 4px solid var(--T1-gray-shadow);
    }

    .large {
        grid-column-start: span 2;
    }

    .blue {
        font-size: 1.1rem;
        color: white;
        background-color: var(--T1-blue);
        border-bottom: 4px solid var(--T1-blue-shadow);
    }

    .red {
        font-size: 1.2rem;
        color: white;
        background-color: var(--T1-red);
        border-bottom: 4px solid var(--T1-red-shadow);
    }

    @media only screen and (max-width: 425px) {
        .grid {
            grid-gap: 15px;
            padding: 20px;
        }
    }

    @media only screen and (max-width: 345px) {
        button {
            font-size: 1.1rem;
        }

        .blue {
            font-size: 1rem;
        }
    }
</style>