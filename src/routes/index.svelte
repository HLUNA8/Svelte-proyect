<script>
  import { onMount } from "svelte";
  import Header from "../components/Header.svelte";
  import Main from "../components/Main.svelte";
  import TimeLine from "../components/Timeline.svelte";
  import SideBar from "../components/Sidebar.svelte";

  let data = {};
  const API = "https://kittygram-api.now.sh/"

  onMount(async () =>{
    const response = await fetch(API);
    data = await response.json();
  })
</script>



<Main>
    <TimeLine posts = {data.posts}/>
    {#if data.user}
      <SideBar {...data.user}/>
    {/if}
</Main>