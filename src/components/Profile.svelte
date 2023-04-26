<script lang="ts">
  import boringProfilePicture from "../assets/pfp.jpg";
  import funProfilePicture from "../assets/pfp0.jpg";

  let isFunMode = false;

  $: myName = isFunMode ? "Andres Flores 🤙" : "Andres Flores";
  $: profilePicture = isFunMode ? funProfilePicture : boringProfilePicture;

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

    &:hover {
      cursor: pointer;
    }
  }

  #my-name {
    margin: 0;
    font-size: 1.25em;
  }
</style>