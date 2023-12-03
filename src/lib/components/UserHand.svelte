<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function selectHand(hand) {
    dispatch('select', hand);
  }
</script>

<button on:click={() => selectHand('ぐー')}>ぐー</button>
<button on:click={() => selectHand('ちょき')}>ちょき</button>
<button on:click={() => selectHand('ぱー')}>ぱー</button>
