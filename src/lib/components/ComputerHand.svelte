<script>
  import { onDestroy } from 'svelte';
  export let isShuffling;

  export let computerHand = 'ぐー';
  const hands = ['ぐー', 'ちょき', 'ぱー'];
  let shuffleInterval;

  // シャッフル制御のリアクティブステートメント
  $: {
    if (isShuffling) {
      startShuffling();
    } else {
      stopShuffling();
    }
  }

  function startShuffling() {
    shuffleInterval = setInterval(() => {
      computerHand = hands[Math.floor(Math.random() * hands.length)];
    }, 100);
  }

  function stopShuffling() {
    clearInterval(shuffleInterval);
  }

  // コンポーネント破棄時にインターバルをクリア
  onDestroy(() => {
    clearInterval(shuffleInterval);
  });
</script>

<div>
  {computerHand}
</div>
