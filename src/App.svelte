<script lang="ts">
import { Router,Link,Route} from "svelte-navigator";
import About from "./About.svelte";
import Inicio from "./Inicio.svelte";

</script>

<Router>
	<nav>
		<Link style={"color: white;text-decoration: none; "} to="/">Inicio</Link>
		<Link style={"color: white;text-decoration: none; "} to="about">About</Link>
	</nav>
	<main>
		<Route component={Inicio}/>
		<Route path="about" component={About}/>
	</main>
</Router>

<style>
</style>