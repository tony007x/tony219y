<script lang="ts">
    import Nav from "./(component)/Nav.svelte";
    import { onMount } from "svelte";
    import { Facebook, Github } from "lucide-svelte";
    import { ChevronsDown } from 'lucide-svelte';

    let scrollY: number = 0;

    const handleScroll = () => {
        scrollY = window.scrollY;
    };

    onMount(() => {
        window.addEventListener("scroll", handleScroll);

        // Cleanup the event listener when the component is destroyed
        return () => {
            window.removeEventListener("scroll", handleScroll);
        };
    });
</script>

<!-- Main -->

<div class="fixed w-[50px] h-[200px] border top-1/3 bg-[#EEEEEE]">
    <div class="flex flex-col h-full items-center justify-around shadow-lg">
        <a href="#GITHUB"><Github /></a>
        <a href="#Facebook"><Facebook /></a>
    </div>
</div>

<div
    id="home"
    class="flex flex-col w-full h-screen gap-10 justify-center items-center duration-200 text-white"
>
    <Nav />

    <div
        class="flex text-center justify-center w-fit border px-10 py-1 rounded-full shadow-md shadow-white"
    >
        <p
            class="overflow-hidden whitespace-nowrap animate-typing border-r border-r-white text-6xl p-3 font-bold text-white max-lg:text-2xl max-lg:p-0"
        >
            T O N Y 2 1 9 Y !
        </p>
    </div>
    <h1 class="text-center animate-fade-up text-3xl">Hi, I'm Tony219Y</h1>
    <p class="animate-fade-up animate-fill-both">Welcome to my website.</p>

    <footer class="absolute bottom-20 animate-bounce animate-delay-100">
        <ChevronsDown size="40px"/>
    </footer>

</div>
<!-- About -->
<div id="about" class="flex flex-col w-full h-screen p-5 text-[#EEEEEE]">
    {#if scrollY > 100}
        <div
            id="aboutData"
            class=" flex w-full h-fit justify-around  items-center max-lg:flex-col"
        >
            <!-- DESCRIPTION -->
            <div
                class="animate-fade-right flex flex-col gap-4 h-fit max-w-[37rem] mt-16 max-sm:text-center"
            >
                <h1 class="text-lg">Hello, Welcome!</h1>
                <h1 class="text-2xl font-extrabold sm:text-3xl md:text-5xl">
                    I'm a passionate
                    <span
                        class="
                        font-extrabold bg-gradient-to-r from-[#EEEEEE] via-[#76ABAE] to-[#76ABAE] inline-block text-transparent bg-clip-text
                        ">Full Stack Developer</span
                    >
                </h1>

                <p class="sm:ml-[0.15rem] text-[1rem] hidden flex-none sm:flex">
                    I'm a programmer currently learning and improving my skills
                    in both frontend and backend development. On the frontend, I
                    work with frameworks like Svelte and React, using tools like
                    Tailwind CSS and Vite to build interfaces. On the backend, I
                    use Node.js with Express to create APIs and manage data. I'm
                    also exploring fullstack projects, using Supabase for
                    databases and deploying apps on platforms like Vercel and
                    Netlify. My goal is to become proficient in both frontend
                    and backend to create smooth, efficient applications.
                </p>
            </div>
            <!-- IMG -->
            <div
                class=" animate-fade-left flex flex-col w-fit h-fit justify-center mt-16 p-5"
            >
                <span
                    class="bg-gradient-to-r from-[#EEEEEE] via-[#76ABAE] to-[#76ABAE] h-2"
                ></span>
                <img
                    alt=""
                    srcset="/image/pic1.png"
                    class=" object-contain w-[300px] h-fit rounded-b-md shadow-[#76ABAE] shadow-lg"
                />
            </div>
        </div>
        <!-- Main Box -->
        <div class="flex p-40 justify-around gap-5 max-lg:flex-col items-center">
            <!-- FrontEnd -->
            <div
                class="flex flex-col w-[250px] h-[300px] justify-center text-center animate-fade-up animate-delay-300"
            >
                <div class="flex flex-col w-full h-full gap-4">
                    <h1 class="font-bold text-2xl">Frontend</h1>
                    <div
                        class="grid grid-cols-2 justify-center p-5 w-full h-full bg-gradient-to-b from-[#EEEEEE] to-[#76ABAE] rounded-xl border-b-4 border-r-4"
                    >
                        <div class="flex justify-center">
                            <img
                            src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg"
                            alt="html5"
                            width="60"
                            height="60"
                            />
                        </div>

                        <div class="flex justify-center">
                            <img
                                src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg"
                                alt="css3"
                                width="60"
                                height="60"
                            />
                        </div>

                        <div class="flex justify-center">
                            <img
                                src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg"
                                alt="javascript"
                                width="50"
                                height="60"
                            />
                        </div>

                        <div class="flex justify-center items-center">
                            <div
                                class="flex h-[60px] w-[60px] bg-slate-800 rounded-lg justify-center"
                            >
                                <img
                                    src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg"
                                    alt="react"
                                    width="50"
                                    height="50"
                                />
                            </div>
                        </div>

                        <div class="flex justify-center">
                            <img
                                src="https://upload.wikimedia.org/wikipedia/commons/1/1b/Svelte_Logo.svg"
                                alt="svelte"
                                width="40"
                                height="40"
                            />
                        </div>

                        <div class="flex justify-center items-center">
                            <div
                                class="flex h-[60px] w-[60px] bg-slate-800 rounded-lg justify-center"
                            >
                                <img
                                    src="https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg"
                                    alt="tailwind"
                                    width="40"
                                    height="40"
                                />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Backend -->
            <div
                class="flex flex-col w-[250px] h-[300px] justify-center text-center"
            >
                <div class="flex flex-col w-full h-full gap-4 animate-fade-up animate-delay-500">
                    <h1 class="font-bold text-2xl">Backend</h1>
                    <div
                        class="grid grid-cols-2 justify-center p-5 w-full h-full bg-gradient-to-b from-[#EEEEEE] to-[#76ABAE] rounded-xl border-b-4 border-r-4"
                    >
                        <div class="flex justify-center">
                            <img
                                src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg"
                                alt="nodejs"
                                width="60"
                                height="60"
                            />
                        </div>

                        <div class="flex justify-center">
                            <img
                                src="https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original-wordmark.svg"
                                alt="express"
                                width="60"
                                height="60"
                            />
                        </div>

                        <div class="flex justify-center">
                            <img
                                src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg"
                                alt="typescript"
                                width="60"
                                height="60"
                            />
                        </div>
                        <div class="flex justify-center items-center">
                            <div
                                class="flex h-[60px] w-[60px] bg-white rounded-lg justify-center"
                            >
                                <img
                                    src="https://www.vectorlogo.zone/logos/java/java-icon.svg"
                                    alt="tailwind"
                                    width="40"
                                    height="40"
                                />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- Database -->
            <div
                class="flex flex-col w-[250px] h-[300px] justify-center text-center animate-fade-up animate-delay-700"
            >
                <div class="flex flex-col w-full h-full gap-4 ">
                    <h1 class="font-bold text-2xl">Database</h1>
                    <div
                        class="grid grid-cols-2 justify-center p-5 w-full h-full bg-gradient-to-b from-[#EEEEEE]  to-[#76ABAE] rounded-xl border-b-4 border-r-4"
                    >
                        <div class="flex justify-center">
                            <img
                                src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg"
                                alt="postgresql"
                                width="60"
                                height="60"
                            />
                        </div>
                        
                        <div class="flex justify-center items-center">
                            <div
                                class="flex h-[60px] w-[60px] bg-white rounded-lg justify-center"
                            >
                                <img
                                    src="https://cdn.prod.website-files.com/66842e04d18971242a294872/669e87d174d190a8ba60b861_supabase-TAiY.png"
                                    alt="tailwind"
                                    width="50"
                                    height="40"
                                />
                            </div>
                        </div>
                        <div class="flex justify-center items-center">
                            <div
                                class="flex h-[60px] w-[60px] rounded-lg justify-center"
                            >
                                <img
                                    src="https://cdn-icons-png.flaticon.com/512/3161/3161158.png"
                                    alt="tailwind"
                                    width="60"
                                    height="40"
                                />
                            </div>
                        </div>

                        
                    </div>
                </div>
            </div>
        </div>
    {/if}
</div>
<!-- experience -->
<div id="experience" class="flex w-full h-screen">
    
</div>
<!-- project -->
<div id="projects" class="flex w-full h-screen"></div>

<!-- <h3 align="left">Languages and Tools:</h3>
<p align="left">

    <a href="https://www.typescriptlang.org/" target="_blank" rel="noreferrer">
        <img
            src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg"
            alt="typescript"
            width="40"
            height="40"
        />
    </a>
</p> -->
