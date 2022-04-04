<script lang="ts">
  let idmChoices = ["Inventor", "Developer", "Moderator"];

  function shuffle(array: Array<string>): Array<string> {
    let index = array.length,
      rIndex;

    while (index !== 0) {
      rIndex = Math.floor(Math.random() * index);
      index -= 1;

      [array[index], array[rIndex]] = [array[rIndex], array[index]];
    }

    return array;
  }

  const idm = shuffle(idmChoices).join(" • ");
</script>

<div class="home flex-col centre">
  <img src="favicon.png" alt="vcokltfre icon" />
  <h1>vcokltfre</h1>
  <h2 class="idm">{idm}</h2>
  <p>
    Hi! I'm a 19 year old software developer from Wales, working primarily on Discord bots using
    <a href="https://docs.disnake.dev">Disnake</a> or
    <a href="https://docs.nextcord.dev">Nextcord</a>, and APIs using
    <a href="https://fastapi.tiangolo.com">FastAPI</a>. I'm also starting to get into web
    development using <a href="https://svelte.dev">Svelte</a> (this site is made with it) and
    TypeScript. I love using
    <a href="https://workers.cloudflare.com/">Cloudflare Workers and Pages</a>
    to make serverless projects on Cloudflare's edge too, such as
    <a href="https://workbin.dev">my paste service</a>.
  </p>
</div>

<style lang="scss">
  img {
    width: 12rem;
  }

  h1 {
    font-size: 4rem;
    font-weight: 400;
    margin: 0;
    padding: 0;
  }

  p {
    width: 60%;
  }

  @media only screen and (max-width: 768px) {
    p {
      width: 100%;
    }
  }
</style>
