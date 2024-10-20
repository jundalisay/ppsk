<script lang="ts">
	import type { Post } from "@prisma/client";
	import Alert from "$lib/components/alert.svelte";
	import Delete from "./delete.svelte";

	import Fa from "svelte-fa";
	import { faPencil } from "@fortawesome/free-solid-svg-icons";

	export let posts: Post[];
</script>

{#if posts.length == 0}
	<Alert>Empty.</Alert>
{:else}
	<div class="mb-6">
		{#each posts as post}

			<a href="/{post.id}/{post.slug}">
	      <div class="grid grid-cols-4 rounded-lg bg-white shadow-lg hover:bg-yellow-50 border dark:hover:bg-gray-800 dark:bg-gray-900 dark:text-white mb-2">
					{#if post?.photo}
		        <img class="object-fill h-full rounded-l" src="/{post?.photo}" alt={post?.title} />
					{/if}

	        <div class="col-span-3 px-4 lg:p-4">
	          <div class="font-bold lg:text-4xl"></div>
	          <div class="text-sm lg:text-3xl text-gray-800 dark:text-gray-100">{post.title}</div>
	          <div class="sm:text-xs lg:text-lg text-gray-800 dark:text-gray-100">{post.content}</div>            
	        </div>
	      </div>
	    </a>

		{/each}
	</div>
{/if}
