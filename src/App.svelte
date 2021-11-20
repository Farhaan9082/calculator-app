<script>
	import Navbar from './components/Navbar.svelte'
	import Input from './components/Input.svelte'
	import Keypad from './components/Keypad.svelte'
</script>

<svelte:head>
	<title>Frontend Mentor | Calculator app</title>
</svelte:head>
<div class="container">
	<Navbar/>
	<Input/>
	<Keypad/>
</div>

<style>
	.container {
		width: 480px;
		margin-inline: auto;
	}
</style>