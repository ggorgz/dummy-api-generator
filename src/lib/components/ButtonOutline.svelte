<script lang="ts">
  export let href: string | undefined = undefined;
  export let onClick: (() => void) | undefined  = undefined;
  export let size: "sm" | "normal" = "normal"
	export let primary = false;
	export let disabled = false;
	export let type: 'submit' | 'button' | 'reset' | null | undefined = undefined;

  let className =
    'inline-block cursor-pointer transition font-medium ';

  if(primary){
    className += " border-2 border-primary-500 hover:bg-primary-500 hover:text-white "
  }else{
    className += " border-2 hover:bg-gray-500/20 border-black dark:border-gray-400 "
  }

  if(size=="sm") {
    className += " px-2 py-1 text-sm rounded-lg"
  }else{
    className += " px-4 py-2 rounded-global"
  }

	if (disabled) {
		className += ' bg-primary-300 ';
	}
</script>

{#if href != undefined}
	<a {href} class={className}><slot /></a>
{:else}
	<button {disabled} on:click={onClick} {type} class={className}><slot /></button>
{/if}
