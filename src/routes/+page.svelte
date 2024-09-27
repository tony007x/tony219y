<script lang="ts">
    import { onMount } from "svelte";
    import { Progress } from "$lib/components/ui/progress/index.js";

    let value = 0;
    const progressBar = async () => {
        value += 1.5;
    };
    const delay = async (ms: number) => {
        await new Promise((resolve) => setTimeout(resolve, ms));
    };

    onMount(async () => {
        while(value<100){
            progressBar();
            await delay(50)
        }
        if(value>=100){
            window.location.pathname ='home'
        }
    });
</script>

<div
    class="flex flex-col w-full h-screen justify-center items-center text-white gap-5"
>
    <div>
        <h1
            class="p-3 animate-typing overflow-hidden whitespace-nowrap border-r-4 border-r-white pr-5 text-5xl text-white font-bold"
        >
            Loading . . .
        </h1>
    </div>
    <Progress {value} max={100} class="w-[30%] border bg-[white]" />
</div>
