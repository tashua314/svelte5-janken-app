<script>
  export let winStreak = 0; // 外部から連勝数を受け取る
</script>

{#if winStreak > 0}
  <p>連勝数: {winStreak}</p>
{/if}

<style>
  p {
    font-size: 1.2em;
    color: #333;
    /* 必要に応じて追加のスタイリング */
  }
</style>

