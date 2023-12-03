<script>
  export let gameState;

  $: text = gameState === 'draw' ? 'あーいこーで' 
             : gameState === 'ready' ? 'じゃーんけーん' 
             : 'ぽんっ';
</script>

<div>{text}</div>
