<script lang="ts">
	import { enhance } from "$app/forms";

	import Fa from "svelte-fa";
	import { faTrash } from "@fortawesome/free-solid-svg-icons";

	let dialog: HTMLDialogElement;
	export let action: string;
	export let message: string;
</script>

<!-- text-error -->
<button title="Delete Note" class="w-full mb-2 justify-center bg-red-600 hover:bg-red-800 rounded-lg text-sm px-5 py-2.5 text-white inline-flex items-center" on:click={() => dialog.show()}>Delete</button>

<!-- <Fa icon=faTrash /> -->

<dialog bind:this={dialog} class="modal">
	<form {action} method="post" class="modal-box" on:submit|preventDefault={() => dialog.close()} use:enhance>
		<h3 class="font-bold text-lg">Confirm</h3>
		<p class="py-4">{@html message}</p>
		<div class="modal-action">
			<button class="btn btn-neutral btn-sm" on:click|preventDefault={() => dialog.close()}>No</button>
			<button type="submit" class="btn btn-error btn-sm">Yes</button>
		</div>
	</form>
</dialog>


