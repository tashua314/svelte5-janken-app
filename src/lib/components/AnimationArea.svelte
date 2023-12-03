<script>
  import { fade } from 'svelte/transition';

  export let result;

  $: animationText = result === 'win' ? '勝ち！' 
                     : result === 'lose' ? '負け…' 
                     : '';
</script>

{#if animationText}
  <div in:fade={{ duration: 500 }}>
    {animationText}
  </div>
{/if}

