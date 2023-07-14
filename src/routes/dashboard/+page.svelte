<script lang="ts">
	import Sidebar from '$components/custom/sidebar/Sidebar.svelte';
	import Dashboard from '$components/custom/dashboard/Dashboard.svelte';
	import Inventory from '$components/custom/inventory/Inventory.svelte';

	let activeSection: string = 'dashboard';

	const setActiveSection = (section: string): void => {
		activeSection = section;
	};
</script>

<main class="flex min-h-screen">
	<Sidebar {activeSection} {setActiveSection} />

	<section class="flex-grow p-2 fixed sm:static z-0 md:px-10 lg:px-52 py-6">
		{#if activeSection === 'dashboard'}
			<Dashboard />
		{:else if activeSection === 'inventory'}
			<Inventory />
		{/if}
	</section>
</main>
