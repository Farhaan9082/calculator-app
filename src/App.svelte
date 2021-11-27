<script>
	import Navbar from './components/Navbar.svelte'
	import Input from './components/Input.svelte'
	import Keypad from './components/Keypad.svelte'

	let ScreenInput = '0'
	$: LastOperator = ScreenInput.substr(-1)

	const AddValue = (e) => {
		if(ScreenInput === '0') {
			if(Number.isInteger(e.detail)) {
				ScreenInput = e.detail.toString()
			}
			else {
				ScreenInput = ScreenInput.concat(e.detail)
			}
		}
		else if((LastOperator === '+' || LastOperator === '-'  || LastOperator === '*'  || LastOperator === '/') && (e.detail === '+' || e.detail === '-'  || e.detail === '*'  || e.detail === '/')) {
			ScreenInput = ScreenInput.slice(0, -1)
			ScreenInput = ScreenInput.concat(e.detail)
		}
		else {
			ScreenInput = ScreenInput.concat(e.detail)
		}
	}

	const AddPoint = (e) => {
		let NumbersArray = ScreenInput.split(/\+|-|\*|\//)
		let NoOfDot = (NumbersArray[NumbersArray.length-1].match(/\./g) || []).length
		if (NoOfDot === 0) {
			if(LastOperator === '+' || LastOperator === '-'  || LastOperator === '*'  || LastOperator === '/') {
				ScreenInput = ScreenInput.concat('0.')
			}
			else {
				ScreenInput = ScreenInput.concat(e.detail)
			}
		}
	}

	const ResetValue = (e) => {
		ScreenInput = '0'
	}

	const DeleteValue = (e) => {
		if(ScreenInput.length === 1) {
			ScreenInput = '0'
		}
		else {
			ScreenInput = ScreenInput.slice(0, -1)
		}
	}

	const OutputValue = (e) => {
		console.log(eval(ScreenInput))
	}
</script>

<svelte:head>
	<title>Frontend Mentor | Calculator app</title>
</svelte:head>
<div class="container">
	<Navbar/>
	<Input {ScreenInput} />
	<Keypad on:insert-value={AddValue} on:insert-point={AddPoint} on:reset-value={ResetValue} on:delete-value={DeleteValue} on:output-value={OutputValue}/>
</div>

<style>
	.container {
		width: 480px;
		margin-inline: auto;
	}
</style>