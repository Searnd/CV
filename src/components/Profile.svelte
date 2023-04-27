<script lang="ts">
  import boringProfilePicture from "../assets/pfp0.jpg";
  import funProfilePicture from "../assets/pfp1.jpg";

  let isFunMode = false;

  $: myName = isFunMode ? "Andres Flores 🤙" : "Andres Flores";
  $: profilePicture = isFunMode ? funProfilePicture : boringProfilePicture;

  function toggleFunMode() {
    isFunMode = !isFunMode;
  }
</script>

<div class="profile-area">
  <div class="profile-picture-container" class:back={isFunMode}>
    <img
      on:click={toggleFunMode}
      class:back={isFunMode}
      class="profile-picture"
      src="{profilePicture}" alt="profile">
  </div>
  <p id="my-name">{myName}</p>
</div>

<style lang="scss">
  .profile-area {
    width: 25%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .profile-picture-container {
    transition: transform 0.6s;
  }

  .profile-picture {
    object-fit: cover;
    border-radius: 50%;
    height: 100px;
    width: 100px;
    transition: transform 0.6s;

    &:hover {
      cursor: pointer;
    }
  }

  .back {
    transform: rotateY(180deg);
  }
  #my-name {
    margin: 0;
    font-size: 1.25em;
  }
</style>