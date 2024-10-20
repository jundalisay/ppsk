<script lang="ts">
	import type { PageServerData } from "./$types";
	import Delete from "$lib/components/delete.svelte";

	export let data: PageServerData;
</script>

<svelte:head>
	<title>{data.post?.title}</title>
</svelte:head>

<article class="container md:w-[800px]" >

<main class="container md:w-[800px] px-8 mx-auto my-8 border rounded-lg">

	<div class="flex justify-center p-3">
		{#if data.post?.photo}
			<img src="/{data.post?.photo}" alt={data.post?.title} class="object-fill h-full rounded-xl shadow" />		
		{/if}

	</div>
  
	<div class="flex justify-center p-3">
		<div class="title text-4xl font-bold py-2">{data.post?.title}</div>
	</div>
      
      <Delete message="Delete this note?" action="/{data.post?.id}/delete" />

			<a href="/{data.post?.id}/edit" title="Edit Note" class="w-full mb-2 justify-center bg-gray-600 hover:bg-gray-800 rounded-lg text-sm px-5 py-2.5 text-white inline-flex items-center">Edit</a>

    <hr class="mt-4">

	<div class="content prose max-w-none py-3">
		{@html data.post?.contentToHtml}
	</div>

	{#if data.post?.tags}
		<div class="flex justify-center gap-3 py-4">
			{#each data.post?.tags as tag}
				<div class="badge badge-ghost hover:bg-gray-500 shadow">
					<a href="/tag/{tag.slug}">{tag.name}</a>
				</div>
			{/each}
		</div>
	{/if}
</article>
