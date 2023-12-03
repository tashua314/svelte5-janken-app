<script>
  import ComputerHand from '$lib/components/ComputerHand.svelte';
  import UserHand from '$lib/components/UserHand.svelte';
  import ResultText from '$lib/components/ResultText.svelte';
  import AnimationArea from '$lib/components/AnimationArea.svelte';
  import WinStreak from '$lib/components/WinStreak.svelte';

  let userHand;
  let computerHand = 'ぐー';
  let gameState = 'ready'; // 'ready', 'draw', 'playing'
  let result;
  let isShuffling = true; // コンピュータの手のシャッフル制御
  let winStreak = 0; // 連勝数

  function handleUserSelect(event) {
    userHand = event.detail;
    gameState = 'playing';
    isShuffling = false; // シャッフル停止
    determineWinner();
  }

  function determineWinner() {
    if (userHand === computerHand) {
      result = 'draw';
      gameState = 'draw';
      isShuffling = true;
    } else {
      result = (userHand === 'ぐー' && computerHand === 'ちょき') ||
               (userHand === 'ちょき' && computerHand === 'ぱー') ||
               (userHand === 'ぱー' && computerHand === 'ぐー') 
               ? 'win' : 'lose';
      gameState = 'done';
      if (result === 'win') {
        winStreak++;
      } else if (result === 'lose') {
        winStreak = 0;
      }
    }
  }

  function resetGame() {
    gameState = 'ready';
    isShuffling = true;
    result = null;
  }
</script>

<h1>じゃんけんアプリ</h1>

<WinStreak {winStreak} />
<ComputerHand bind:computerHand {isShuffling} />
<UserHand on:select={handleUserSelect} />
<ResultText {gameState} />
<AnimationArea {result} />

{#if gameState === 'done'}
  <button on:click={resetGame}>再戦</button>
{/if}
