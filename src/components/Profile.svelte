<script lang="ts">
  import profilePicture from "../assets/pfp.jpg";
  let isFunMode = false;

  $: myName = isFunMode ? "Andres Flores 🤙" : "Andres Flores";

  function toggleFunMode() {
    isFunMode = !isFunMode;
  }
</script>

<div>
  <img on:click={toggleFunMode} id="profile-picture" src="{profilePicture}" alt="profile">
  <p id="my-name">{myName}</p>
</div>

<style lang="scss">
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