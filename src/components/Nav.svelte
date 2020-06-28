<script>
  // --------------------------------------------------------------
  // Import packages and components
  // --------------------------------------------------------------

  	import { createEventDispatcher } from "svelte";

  // --------------------------------------------------------------
  // Declared Variables
  // --------------------------------------------------------------

  	const dispatch = createEventDispatcher();

  // --------------------------------------------------------------
  // Functions Definations
  // --------------------------------------------------------------

		const updatModel = () => {
			dispatch("updatModel");
		};
</script>

<nav>
  <button on:click={updatModel}>Add Contact</button>
</nav>

<style>
  nav {
    width: 100%;
    height: 70px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #fff;
  }

  button {
    border: none;
    padding: 10px 20px;
    border-radius: 3px;
    background: linear-gradient(to right, #6547e3, skyblue);
    color: #fff;
    outline: none;
    cursor: pointer;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  }
</style>
