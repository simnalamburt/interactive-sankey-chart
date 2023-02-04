<script>
	const expenses = {
		"Gross profit": {
			"Operating profit": {
				"Net profit": 4.7,
				"Tax": 1.5,
				"Interest": 0.3,
			},
			"Operating expenses": {
				"R&D": 9.8,
				"Sales & marketing": 4.6,
				"General & admin": 3.1,
			},
		},
		"Cost of revenue": 8.3,
	};

	function sumExpenses(expenses) {
		let sum = 0
		for (const [_, value] of Object.entries(expenses)) {
			switch (typeof value) {
				case 'number':
					sum += value;
					break;
				case 'object':
					sum += sumExpenses(value);
					break;
				default:
					throw new Error('Unexpected type');
			}
		}
		return sum;
	}
</script>

<svg id=canvas>
	<rect width=30 height={sumExpenses(expenses) * 30} fill="red" />
</svg>

<style>
	svg#canvas {
		display: block;
		width: 100vw;
		height: 100vh;
	}
</style>
