<script>
	import data from './data';
	import { page } from '$app/stores';
	import { open } from '../provider/store';

	const style = {
		title: `mx-4 text-sm`,
		inactive: `text-white`,
		active: `font-medium text-green-400 hover:text-green-400`,
		link: `flex items-center justify-start my-2 p-4 w-full hover:text-white`,
		close: `lg:duration-700 lg:ease-out lg:invisible lg:opacity-0 lg:transition-all`,
		open: `lg:duration-500 lg:ease-in lg:h-auto lg:opacity-100 lg:transition-all lg:w-auto`
	};
</script>

<ul class="md:pl-5">
	<li>
		{#each data as item, i (item.title)}
			<a
				href={item.link}
				class={`${style.link} 
            ${item.link === $page.url.pathname ? style.active : style.inactive}`}
			>
				<span><svelte:component this={item.icon} /></span>
				<span class={`${style.title} ${$open ? style.open : style.close}`}>
					{item.title}
				</span>
			</a>
		{/each}
	</li>
</ul>
