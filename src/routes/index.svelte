<script lang="ts">
  import { onMount } from "svelte";

  import About from "../pages/about.svelte";
  import Discord from "../pages/discord.svelte";
  import Home from "../pages/home.svelte";
  import Projects from "../pages/projects.svelte";

  let page = "home";

  function setPage(newPage: string): void {
    page = newPage;

    if (newPage === "home") {
      newPage = "/";
    } else {
      newPage = `/?tab=${newPage}`;
    }

    window.history.pushState("", "", newPage);
  }

  onMount(() => {
    const urlParams = new URLSearchParams(window.location.search);

    if (urlParams.has("tab")) {
      setPage(urlParams.get("tab"));
    }

    window.onpopstate = function () {
      let newPath = window.location.pathname.slice(1);

      if (newPath === "") {
        newPath = "home";
      }

      page = newPath;
    };
  });
</script>

<svelte:head>
  <title>Home</title>
</svelte:head>

<div>
  <nav class="flex-row centre">
    <img src="favicon.png" alt="vcokltfre icon" />
    <div class="grow" />
    <button on:click={() => setPage("home")} class={page === "home" ? "active" : ""}>Home</button>
    <button on:click={() => setPage("projects")} class={page === "projects" ? "active" : ""}
      >Projects</button
    >
    <button on:click={() => setPage("about")} class={page === "about" ? "active" : ""}>About</button
    >
    <button on:click={() => setPage("css")} class={page === "css" ? "active" : ""}>CSS</button>
  </nav>
  <div class="content">
    {#if page === "projects"}
      <Projects />
    {:else if page === "about"}
      <About />
    {:else if page === "css"}
      <Discord />
    {:else}
      <Home />
    {/if}
  </div>
</div>

<style lang="scss">
  nav {
    width: 60%;
    height: 3rem;
    padding-left: 20%;
    padding-right: 20%;

    background-color: lighten(#1a1f27, 4%);

    img {
      height: 2rem;
      width: 2rem;
    }

    button {
      height: 3rem;
      width: 4rem;
      border-radius: 0rem;
      background-color: lighten(#1a1f27, 4%);
      border: none;
      color: #87ceeb;
      margin: 0.25rem;
      transition: 0.1s linear;
    }

    button:hover {
      background-color: lighten(#1a1f27, 8%);
    }

    button:active {
      background-color: #1a1f27;
    }

    .active {
      background-color: lighten(#1a1f27, 8%);
    }
  }

  .content {
    width: 60%;
    height: 100%;
    padding-left: 20%;
    padding-right: 20%;
    margin-top: 1rem;
  }

  @media only screen and (max-width: 768px) {
    nav {
      width: 96%;
      padding-left: 2%;
      padding-right: 2%;
    }

    .content {
      width: 96%;
      padding-left: 2%;
      padding-right: 2%;
      margin-top: 0.5rem;
    }
  }
</style>
