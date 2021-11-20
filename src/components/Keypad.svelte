<script>
    
</script>

<section class="grid">
    <button>7</button>
    <button>8</button>
    <button>9</button>
    <button class="blue">DEL</button>
    <button>4</button>
    <button>5</button>
    <button>6</button>
    <button>+</button>
    <button>1</button>
    <button>2</button>
    <button>3</button>
    <button>-</button>
    <button>.</button>
    <button>0</button>
    <button>/</button>
    <button>x</button>
    <button class="large blue">RESET</button>
    <button class="large red">=</button>
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
</style>