<script lang="ts">
  type MessageAuthor = {
    username: string;
    avatar?: string;
    colour?: string;
    bot?: boolean;
  };

  type MessageReference = {
    content: string;
    author: MessageAuthor;
  };

  type Message = {
    author?: MessageAuthor;
    content?: string;
    reference?: MessageReference;
    highlight?: boolean;
  };

  export let message: Message;
</script>

<div class="discord-message" style={message.highlight ? "background-color: #00ff0011" : ""}>
  {#if message.reference}
    <div class="dmsg-reference">
      <div class="dmsg-ref-line" />
      <div class="dmsg-ref-author">
        <img
          class="avatar"
          src={message.reference.author.avatar || "https://cdn.discordapp.com/embed/avatars/0.png"}
          alt={message.reference.author.username}
        />
        <span class="username" style="color: {message.reference.author.colour || '#fff'}"
          >{message.reference.author.username}</span
        >
        {#if message.reference.author.bot}
          <span class="dmsg-bot">BOT</span>
        {/if}
      </div>
      <div class="dmsg-ref-content">
        {message.reference.content}
      </div>
    </div>
  {/if}
  <div class="dmsg-main">
    <div class="dmsg-side">
      <div class="dmsg-avatar">
        {#if message.author}
          <img
            class="avatar"
            src={message.author.avatar || "https://cdn.discordapp.com/embed/avatars/0.png"}
            alt={message.author.username}
          />
        {:else}
          <div class="dmsg-noauth" />
        {/if}
      </div>
    </div>
    <div class="dmsg-body">
      {#if message.author}
        <div class="dmsg-header">
          <span class="username" style="color: {message.author.colour || '#fff'}"
            >{message.author.username}</span
          >
          {#if message.author.bot}
            <span class="dmsg-bot">BOT</span>
          {/if}
        </div>
      {/if}
      <div class="dmsg-content dmsg-noauth-{!message.author}">
        {message.content}
      </div>
    </div>
  </div>
</div>

<style lang="scss">
  .discord-message {
    display: flex;
    flex-direction: column;
    width: 100%;
    color: #c1c1c1;
    margin-top: 0.25rem;
    padding-top: 0.2rem;
    padding-left: 0.2rem;

    .dmsg-bot {
      background-color: #5865f2;
      color: #fff;
      font-size: 0.65em;
      padding-right: 0.1rem;
      padding-left: 0.1rem;
      border-radius: 0.2rem;
      font-weight: bold;
    }

    .dmsg-noauth {
      margin-left: 3rem;
    }

    .dmsg-noauth-true {
      position: relative;
      top: -0.6rem;
    }

    .dmsg-reference {
      display: flex;
      flex-direction: row;
      align-items: center;
      margin-bottom: 0.1rem;

      .dmsg-ref-line {
        border: none;
        border-top: 1px solid grey;
        border-left: 1px solid grey;
        border-top-left-radius: 0.25rem;
        width: 1.25rem;
        height: 0.5rem;
        margin-left: 1.25rem;
        margin-right: 0.5rem;
      }

      .dmsg-ref-author {
        display: flex;
        flex-direction: row;
        align-items: center;
        position: relative;
        top: -0.2rem;

        .avatar {
          border-radius: 50%;
          width: 1rem;
          height: 1rem;
        }

        .username {
          margin-left: 0.3rem;
          margin-right: 0.2rem;
          font-size: 0.8em;
        }
      }

      .dmsg-ref-content {
        position: relative;
        top: -0.1rem;
        margin-left: 0.3rem;
        font-size: 0.8em;
        color: #a1a1a1;
      }
    }

    .dmsg-main {
      display: flex;
      flex-direction: row;
      align-items: top;
      width: 100%;

      .avatar {
        height: 2.5rem;
        width: 2.5rem;
        border-radius: 50%;
        margin-right: 0.5rem;
      }

      .dmsg-header {
        .username {
          font-size: 1em;
        }
      }

      .dmsg-content {
        font-size: 0.95em;
      }
    }
  }
</style>
