<script>
  export let hook;
  export let i;
  export let hookEntityDefinitions;
</script>

<div class="hook">
  {#if i || i === 0}<span class="hook-number">{i + 1}.</span>{/if}

  <div class="overview">
    <span class="hook-name">
      {#if hook.link && hook.link.length > 0}<a href={hook.link}>{hook.hook}</a>{:else}{hook.hook}{/if}
    </span>
    : {hook.context}
  </div>
  <div class="use">
    {@html hook.use}
  </div>

  <div class="list">
    <strong>Props</strong> : {#each hook.props as prop}
      <div class="code" data-balloon-length="medium" data-balloon-pos="up" aria-label={hookEntityDefinitions[prop]}>
        {prop}
      </div>
    {/each}
  </div>
  <div class="list">
    <strong>Mutable</strong> : {#each hook.mutable as mutable}
      <div class="code" data-balloon-length="medium" data-balloon-pos="up" aria-label={hookEntityDefinitions[mutable]}>
        {mutable}
      </div>
    {/each}
  </div>

  {#if hook.advanced}
    <div><small>This hook is an 'advanced' hook meaning it geared towards advanced users or plugins.</small></div>
  {/if}

  <small>{hook.expiremental ? 'Expiremental' : 'Stable'} &middot; Location: {hook.location}</small>
</div>
