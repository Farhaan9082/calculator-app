<script>
	import Navbar from './components/Navbar.svelte'
	import Input from './components/Input.svelte'
	import Keypad from './components/Keypad.svelte'
	import Footer from './components/Footer.svelte'

	let ScreenInput = '0'
	$: LastOperator = ScreenInput.substr(-1)
	$: NumbersArray = ScreenInput.split(/\+|-|\*|\//)

	const AddValue = (e) => {
		if(NumbersArray[NumbersArray.length-1] === '0') {
			if(Number.isInteger(e.detail)) {
				ScreenInput = ScreenInput.slice(0, -1)
				ScreenInput = ScreenInput.concat(e.detail)
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
		try {
			let Result = eval(ScreenInput)
			if (Number.isFinite(Result)) {
				ScreenInput = Result.toString()
			}
			else {
				alert(Result.toString())
			}
		}
		catch {
			alert("Error")
		}
	}
</script>

<svelte:head>
	<title>Frontend Mentor | Calculator app</title>
</svelte:head>
<div class="container">
	<Navbar/>
	<Input {ScreenInput} />
	<Keypad on:insert-value={AddValue} on:insert-point={AddPoint} on:reset-value={ResetValue} on:delete-value={DeleteValue} on:output-value={OutputValue}/>
	<Footer/>
</div>

<style>
	.container {
		width: 480px;
		margin-inline: auto;
	}

	:global(body) {
		background-color: var(--Very-dark-desaturated-blue);
		transition: background-color 0.2s;
	}

	:global(body.light-mode) {
		background-color: var(--T2-main);
	}

	:global(body.neon-mode) {
		background-color: var(--T3-main);
	}
</style>