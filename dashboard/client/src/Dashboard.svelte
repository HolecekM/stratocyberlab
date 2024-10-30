<script>
  import ChallengeDetail from './ChallengeDetail.svelte';
  import ClassDetail from './ClassDetail.svelte';
  import Introduction from './Introduction.svelte';
  import SideNavBar from './SideNavBar.svelte';

  export let chosenChallenge;
  export let chosenClass;
</script>

<style>
</style>

<div class="d-flex">
  <div class="flex-grow-0">
    <SideNavBar class="mb2" bind:chosenChallenge bind:chosenClass />
  </div>
  <div class="flex-grow-1 ps-5">
    {#if chosenChallenge !== undefined}
      <ChallengeDetail bind:challenge={chosenChallenge} />
    {:else if chosenClass !== undefined}
      <ClassDetail bind:curClass={chosenClass} />
    {:else}
      <Introduction />
    {/if}
  </div>
</div>
