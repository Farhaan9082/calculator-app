<script>
	import Navbar from './components/Navbar.svelte'
	import Input from './components/Input.svelte'
	import Keypad from './components/Keypad.svelte'

	let ScreenInput = '0'

	const AddValue = (e) => {
		if(ScreenInput === '0') {
			if(Number.isInteger(e.detail)) {
				ScreenInput = e.detail.toString()
			}
		}
		else {
			ScreenInput = ScreenInput.concat(e.detail)
		}
	}

	const ResetValue = (e) => {
		ScreenInput = '0'
	}
</script>

<svelte:head>
	<title>Frontend Mentor | Calculator app</title>
</svelte:head>
<div class="container">
	<Navbar/>
	<Input {ScreenInput} />
	<Keypad on:insert-value={AddValue} on:reset-value={ResetValue}/>
</div>

<style>
	.container {
		width: 480px;
		margin-inline: auto;
	}
</style>