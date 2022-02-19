<script lang="ts">
  import DiscordMessage from "../components/discord.svelte";
</script>

<p>This is just some CSS I wrote for fun that styles messages like Discord messages.</p>

<div class="messages">
  <DiscordMessage
    message={{
      author: {
        username: "vcokltfre",
        avatar: "/favicon.png",
        colour: "#87ceeb",
      },
      content: "discorcl.com",
    }}
  />
  <DiscordMessage
    message={{
      author: {
        username: "Phishy",
        colour: "#abc123",
        avatar: "https://avatars.githubusercontent.com/u/91234733?s=200&v=4",
        bot: true,
      },
      reference: {
        content: "discorcl.com",
        author: {
          username: "@vcokltfre",
          avatar: "/favicon.png",
          colour: "#87ceeb",
        },
      },
      content: "Oh no! A phishing link!",
      highlight: true,
    }}
  />
  <DiscordMessage
    message={{
      author: {
        username: "vcokltfre",
        avatar: "/favicon.png",
        colour: "#87ceeb",
      },
      content: "Oops",
    }}
  />
  <DiscordMessage
    message={{
      content: "I shouldn't do that.",
    }}
  />
</div>

<style lang="scss">
  p {
    text-align: center;
  }
</style>
