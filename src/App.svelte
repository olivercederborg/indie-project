<script>
	import { items } from './items'
	let searchValue
	let searchResults = []

	const checkName = (name, str) => {
		var pattern = str
			.split('')
			.map((x) => {
				return `(?=.*${x})`
			})
			.join('')
		var regex = new RegExp(`${pattern}`, 'g')
		return name.match(regex)
	}

	$: {
		if (searchValue) {
			let searchString = searchValue.toLowerCase().substring(0, 4)

			searchResults = items.filter((item) => {
				let substring = item.name.substring(0, 4).toLowerCase()
				return (
					item.name.toLowerCase().includes(searchString) ||
					checkName(substring, searchString)
				)
			})
		} else {
			searchResults = []
		}
		console.log(searchResults)
	}
</script>

<main>
	<section class="container min-h-screen grid place-items-center">
		<div class="relative">
			<form>
				<input
					type="text"
					bind:value={searchValue}
					class="border py-3 px-4 rounded-lg"
				/>
				<button class="py-3 px-5 bg-black text-white rounded-lg"
					>Search</button
				>
			</form>

			{#if searchResults.length}
				<ul
					class="space-y-4 absolute top-20 bg-white shadow-lg w-full p-4 rounded-lg"
				>
					{#each searchResults as item}
						<li class="flex items-center">
							<img
								src={item.img}
								alt={item.name}
								class="h-[50px] w-[50px] object-cover mr-4 rounded-lg"
							/>
							{item.name}: {item.price}
						</li>
					{/each}
				</ul>
			{/if}
		</div>
	</section>
</main>
