<script lang="ts">
    import { Button } from "$lib/components/ui/button";
    import { Menu } from "lucide-svelte";

    let isOpen: boolean = false;

    const toggleMenu = () => {
        isOpen = !isOpen;
    };

    const scroll = (event: Event) => {
        const target = event.currentTarget as HTMLAnchorElement;
        const el = document.querySelector<HTMLElement>(
            target.getAttribute("href") || "",
        );
        if (!el) return;
        el.scrollIntoView({
            behavior: "smooth",
        });
    };
</script>

<nav
    class="fixed w-full z-20 top-0 start-0 h-auto border-b border-slate-600 backdrop-blur-sm"
>
    <div class="flex w-full p-4 justify-between items-center px-10">
        <h1
            class="text-2xl font-extrabold bg-gradient-to-r from-[#EEEEEE] via-[#76ABAE] to-[#76ABAE] inline-block text-transparent bg-clip-text "
        >
            
            <a href="#home" on:click|preventDefault={scroll}>&lt; TONY219Y /&gt;</a>
        </h1>

        <ul class="flex w-1/2 items-center justify-around max-md:hidden">
            <li
                class="text-sm bg-gradient-to-r from-[#EEEEEE] to-[#76ABAE] text-transparent bg-clip-text font-bold hover:text-lg duration-300"
            >
                <a href="#about" on:click|preventDefault={scroll}>About me</a>
            </li>
            <li
                class="text-sm bg-gradient-to-r from-[#EEEEEE] to-[#76ABAE] text-transparent bg-clip-text font-bold hover:text-lg duration-300"
            >
                <a href="#experience" on:click|preventDefault={scroll}
                    >Experience</a
                >
            </li>
            <li
                class="text-sm bg-gradient-to-r from-[#EEEEEE] to-[#76ABAE] text-transparent bg-clip-text font-bold hover:text-lg duration-300"
            >
                <a href="#projects" on:click|preventDefault={scroll}>Projects</a
                >
            </li>
        </ul>
        <Button class="sm:hidden" on:click={toggleMenu}><Menu /></Button>
    </div>
    {#if isOpen}
        <div 
            class=" fixed text-center right-0 top-14 pr-6 bg-[#222831] m-2 rounded-xl animate-fade-left border"
        >
            <li
                class="text-sm bg-gradient-to-r from-[#EEEEEE] to-[#76ABAE] text-transparent bg-clip-text font-bold p-3 animate-fade-left"
            >
                <a href="#about" on:click|preventDefault={scroll}>About me</a>
            </li>
            <li
                class="text-sm bg-gradient-to-r from-[#EEEEEE] to-[#76ABAE] text-transparent bg-clip-text font-bold p-3 animate-fade-left animate-delay-100"
            >
                <a href="#experience" on:click|preventDefault={scroll}
                    >Experience</a
                >
            </li>
            <li
                class="text-sm bg-gradient-to-r from-[#EEEEEE] to-[#76ABAE] text-transparent bg-clip-text font-bold p-3 animate-fade-left animate-delay-200"
            >
                <a href="#projects" on:click|preventDefault={scroll}>Projects</a>
            </li>
        </div>
    {/if}
</nav>
