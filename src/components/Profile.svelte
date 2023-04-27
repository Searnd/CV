<script lang="ts">
  import boringProfilePicture from "../assets/pfp.jpg";
  import funProfilePicture from "../assets/pfp0.jpg";

  let isFunMode = false;

  $: myName = isFunMode ? "Andres Flores 🤙" : "Andres Flores";

  function toggleFunMode() {
    isFunMode = !isFunMode;
  }
</script>

<div class="profile-area">
  <div on:click={toggleFunMode} class="flip-outer" class:fun={isFunMode}>
    <div class="flip-inner">
      {#if !isFunMode}
      <div class="flip-front">
        <img id="profile-picture" src="{boringProfilePicture}" alt="profile">
      </div>
      {:else}
      <div class="flip-back">
        <img id="profile-picture" src="{funProfilePicture}" alt="profile">
      </div>
      {/if}
    </div>
  </div>
  <p id="my-name">{myName}</p>
</div>

<style lang="scss">
  .profile-area {
    width: 25%;
  }
  .flip-outer {
    perspective: 1000px;
    &:hover {
      cursor: pointer;
    }
    &.fun {
      .flip-inner {
        transform: rotateY(180deg);
      }  
    }

    .flip-inner {
      transition: transform 0.6s;
      transform-style: preserve-3d;

      .flip-front, .flip-back {
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
      }

      .flip-back {
        transform: rotateY(180deg);
      }
    }
  }

  #profile-picture {
    object-fit: cover;
    border-radius: 50%;
    height: 100px;
    width: 100px;
  }

  #my-name {
    margin: 0;
    font-size: 1.25em;
  }
</style>