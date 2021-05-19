<script context='module'>
  export async function preload() {
    let data = {};
    const response = await this.fetch(
      'https://kittygram-api.now.sh/'
    );
    data = await response.json();
    return {data};
  };
</script>

<script>
  import Header from "../components/Header.svelte";
  import Main from "../components/Main.svelte";
  import TimeLine from "../components/Timeline.svelte";
  import SideBar from "../components/Sidebar.svelte";
  export let data;
</script>

<svelte:head>
  <title>Catsgram</title>
</svelte:head>

<Main>
    <TimeLine posts = {data.posts}/>
    {#if data.user}
      <SideBar {...data.user}/>
    {/if}
</Main>