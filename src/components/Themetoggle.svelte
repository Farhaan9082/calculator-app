<script>
    $: CurrentTheme = ""
    const ToggleMain = () => {
        if(CurrentTheme === "light-mode") {
            window.document.body.classList.remove('light-mode')
        }
        else if(CurrentTheme === "neon-mode") {
            window.document.body.classList.remove('neon-mode')
        }

        CurrentTheme = ""
    }

	const ToggleLight = () => {
        if(CurrentTheme === "") {
            window.document.body.classList.add('light-mode')
        }
        else if(CurrentTheme === "neon-mode") {
            window.document.body.classList.replace('neon-mode', 'light-mode')
        }

        CurrentTheme = 'light-mode'
    }

    const ToggleNeon = () => {
        if(CurrentTheme === "") {
            window.document.body.classList.add('neon-mode')
        }
        else if(CurrentTheme === "light-mode") {
            window.document.body.classList.replace('light-mode', 'neon-mode')
        }

        CurrentTheme = 'neon-mode'
    }
</script>

<section>
    <div class="theme-grid">
        <div></div>
        <div class="theme-numbers">
            <h4>1</h4>
            <h4>2</h4>
            <h4>3</h4>
        </div>
        <h3>THEME</h3>
        <div class="theme-toggle">
            <div class="theme-group">
                <input type="radio" name="radio" class="toggle" id="toggle-1" checked on:click={() => ToggleMain()}>
                <label for="toggle-1" class="button"></label>
            </div>
            
            <div class="theme-group">
                <input type="radio" name="radio" class="toggle" id="toggle-2" on:click={() => ToggleLight()}>
                <label for="toggle-2" class="button"></label>
            </div>
            
            <div class="theme-group">
                <input type="radio" name="radio" class="toggle" id="toggle-3" on:click={() => ToggleNeon()}>
                <label for="toggle-3" class="button"></label>
            </div>
        </div>
    </div>
</section>

<style>
    h3 {
        font-size: 0.7rem;
        align-self: center;
        color: white;
    }

    :global(body.light-mode) h3 {
        color: var(--T2-text-dark);
    }

    :global(body.neon-mode) h3 {
        color: var(--T3-text-yellow);
    }

    h4 {
        font-size: 0.65rem;
        color: white;
    }

    :global(body.light-mode) h4 {
        color: var(--T2-text-dark);
    }

    :global(body.neon-mode) h4 {
        color: var(--T3-text-yellow);
    }

    .toggle {
        opacity: 0;
        position: absolute;
        cursor: pointer;
    }

    .theme-group {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .theme-grid {
        width: 130px;
        height: 45px;
        display: grid;
        grid-template-columns: 1fr 1fr;
    }

    .theme-numbers {
        display: flex;
        justify-content: space-between;
        padding-inline: 9px;
        align-self:flex-end;
        padding-bottom: 3px;
    }

    .theme-toggle {
        background-color: var(--T1-screen);
        border-radius: 500px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-inline: 12px;
    }

    :global(body.light-mode) .theme-toggle {
        background-color: var(--T2-keypad);
    }

    :global(body.neon-mode) .theme-toggle {
        background-color: var(--T3-keypad);
    }

    .toggle:checked + .button{
        position: absolute;
        background-color: var(--T1-red);
        width: 14px;
        height: 14px;
        border-radius: 50%;
    }

    :global(body.light-mode) .toggle:checked + .button {
        background-color: var(--T2-orange);
    }

    :global(body.neon-mode) .toggle:checked + .button {
        background-color: var(--T3-cyan);
    }
</style>