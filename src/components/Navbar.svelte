<script>
	import Themetoggle from './Themetoggle.svelte'
</script>

<nav>
    <h1>calc</h1>
    <Themetoggle/>
</nav>

<style>
    nav {
        margin-bottom: 20px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

	h1 {
        color: white;
        font-size: 1.6rem;
        align-self: flex-end;
    }

    :global(body.light-mode) h1 {
        color: var(--T2-text-dark);
    }

    :global(body.neon-mode) h1 {
        color: var(--T3-text-yellow);
    }
</style>