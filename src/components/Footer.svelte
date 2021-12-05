<script>
    
</script>

<footer>
    Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
    Coded by <a href="https://github.com/Farhaan9082">Farhaan</a>.
</footer>

<style>
    footer {
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 20px;
        font-size: 0.8rem;
    }

    :global(body.light-mode) footer {
        color: var(--T2-text-dark);
    }

    :global(body.neon-mode) footer {
        color: var(--T3-text-yellow);
    }

    a {
        color: var(--T1-red);
        margin-left: 5px;
    }

    :global(body.light-mode) a {
        color: var(--T2-orange);
    }

    :global(body.neon-mode) a {
        color: var(--T3-cyan);
    }

    @media only screen and (max-width: 425px) {
        footer {
            font-size: 0.7rem;
        }
    }

    @media only screen and (max-width: 380px) {
        footer {
            font-size: 0.55rem;
        }
    }
</style>