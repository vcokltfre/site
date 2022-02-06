<script lang="ts">
  export let name: string;
  export let description: string;
  export let image: string;
  export let link: string;
</script>

<div class="project flex-row centre">
  <a href={link} class="flex-row centre">
    <div class="img">
      <img src={image} alt={name} />
    </div>
    <div class="details">
      <h1>{name}</h1>
      <h2>{description}</h2>
    </div>
  </a>
</div>

<style lang="scss">
  .project {
    background-color: lighten(#1a1f27, 4%);
    padding: 0.5rem;
    border-radius: 0.5rem;
    word-wrap: break-word;
    text-align: center;
    width: calc(100% - 1rem);
    height: 5rem;
    margin-bottom: 1rem;

    .img {
      width: 8rem;
      align-items: center;

      img {
        height: 4rem;
        border-radius: 0.5rem;
      }
    }

    h1,
    h2 {
      margin: 0;
    }

    h2 {
      font-size: 1.2rem;
    }

    a {
      text-decoration: none;
      color: inherit;
    }

    a:visited {
      color: inherit;
    }

    .details {
      margin-left: 2rem;
      text-align: left;
    }
  }

  @media only screen and (max-width: 768px) {
    .project {
      margin-bottom: 0.5rem;

      h1 {
        font-size: 1.2rem;
      }

      h2 {
        font-size: 1rem;
      }
    }
  }
</style>
