<script lang="ts">
    import { writeFile,FsTextFileOption } from "@tauri-apps/api/fs";
    let contents = ""
    let info = ""
    let msgVisible = false
    const message = (text:string)=>{
        msgVisible =  true 
        info = text
    }
    const handleClick = async ()=>{
        const f:FsTextFileOption = {
            path:"./test.txt",
            contents
        }
        try {
            await writeFile(f)
            info = "done"
        } catch (error) {
            info = error
        }
    }
</script>

<h1>Inicio</h1>
<input type="text" bind:value={contents}>
<button on:click={handleClick}>Save Text</button>
<p>{info}</p>
<hr>
<button on:click={()=>message("Hola mundo")}>Mostrar Mensaje</button>
{#if msgVisible}
<div  class="msg">
    {info}
    <button on:click={()=>msgVisible = false}>cerrar</button>
</div>
{/if}


<style>
    .msg{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        padding: 1rem;
        box-shadow: 0 0 6px gray;
    }
</style>