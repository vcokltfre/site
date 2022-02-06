<script lang="ts">
  import About from "../pages/about.svelte";
  import Home from "../pages/home.svelte";
  import Projects from "../pages/projects.svelte";

  let page = "home";
</script>

<svelte:head>
  <title>Home</title>
</svelte:head>

<div>
  <nav class="flex-row centre">
    <img src="favicon.png" alt="vcokltfre icon" />
    <div class="grow" />
    <button on:click={() => (page = "home")} class={page === "home" ? "active" : ""}>Home</button>
    <button on:click={() => (page = "projects")} class={page === "projects" ? "active" : ""}
      >Projects</button
    >
    <button on:click={() => (page = "about")} class={page === "about" ? "active" : ""}>About</button
    >
  </nav>
  <div class="content">
    {#if page === "home"}
      <Home />
    {:else if page === "projects"}
      <Projects />
    {:else if page === "about"}
      <About />
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
