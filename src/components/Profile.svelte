<script lang="ts">
  import boringProfilePicture from "../assets/pfp0.jpg";
  import funProfilePicture from "../assets/pfp1.jpg";

  import FaLinkedin from "svelte-icons/fa/FaLinkedin.svelte";
  import FaGithub from "svelte-icons/fa/FaGithub.svelte";
  import FaEnvelope from "svelte-icons/fa/FaEnvelope.svelte";
  import FaPhone from "svelte-icons/fa/FaPhone.svelte";

  const email = "andres.flores@outlook.fr";
  const phone = "(514) 632-3485";

  let isFunMode = false;

  $: myName = isFunMode ? "Andres Flores 🤙" : "Andres Flores";
  $: profilePicture = isFunMode ? funProfilePicture : boringProfilePicture;

  function toggleFunMode() {
    isFunMode = !isFunMode;
  }
</script>

<div class="profile-area">
  <div class="profile-picture-container" class:flipped={isFunMode}>
    <img
      on:click={toggleFunMode}
      class:flipped={isFunMode}
      class="profile-picture"
      src="{profilePicture}" alt="profile">
  </div>
  <p id="my-name">{myName}</p>
  <div class="profile-line links">
    <a target="_blank" href="https://www.linkedin.com/in/andres-flores-3a679bb5">
      <i class="li-icon"><FaLinkedin/></i>
    </a>
    <a target="_blank" href="https://github.com/Searnd">
      <i class="gh-icon"><FaGithub/></i>
    </a>
  </div>
  <div class="profile-line email">
    <i><FaEnvelope/></i>
    <a href={`mailto:${email}`}>
      {email}
    </a>
  </div>
  <div class="profile-line phone">
    <i><FaPhone/></i>
    {phone}
  </div>
</div>

<style lang="scss">
  i {
    display: block;
    height: 1em;
  }
  .li-icon {
    color: #0a66c2;
  }

  .gh-icon {
    color: black;
  }
  .profile-line {
    display: flex;
    gap: 0.5em;
  }
  .email {
    i {
      align-self: flex-end;
    }
  }

  .phone {
    i {
      align-self: center;
    }
  }
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
    height: 200px;
    width: 200px;
    transition: transform 0.6s;

    &:hover {
      cursor: pointer;
    }
  }

  .flipped {
    transform: rotateY(180deg);
  }
  #my-name {
    margin: 0;
    font-size: 1.25em;
  }
</style>