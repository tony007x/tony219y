<script lang="ts">
    import CarouselNext from "./../../lib/components/ui/carousel/carousel-next.svelte";
    import Nav from "./(component)/Nav.svelte";
    import { onMount } from "svelte";
    import { Facebook, Github } from "lucide-svelte";
    import { ChevronsDown } from "lucide-svelte";
    import { ChevronsRight } from "lucide-svelte";
    import * as Card from "$lib/components/ui/card";
    import { Button } from "$lib/components/ui/button";
    import * as Carousel from "$lib/components/ui/carousel/index.js";
    import { Description } from "$lib/components/ui/alert";
    import CarouselPrevious from "$lib/components/ui/carousel/carousel-previous.svelte";
    import { Label } from "$lib/components/ui/label";
    import { Input } from "$lib/components/ui/input";
    import Textarea from "$lib/components/ui/textarea/textarea.svelte";
    import { toast } from "svelte-sonner";
    import wretch from 'wretch'

    let scrollY: number = 0;

    const handleScroll = () => {
        scrollY = window.scrollY;
    };

    let fullName: string;
    let email: string;
    let subject: string;
    let body: string;

    const sendEmail = async (event : any) =>{
        event.preventDefault();
        if(!fullName || !email || !subject || !body){
            return toast.error("Please complete the form!")
        }
        await wretch('http://localhost:3000/email/send')
        .post({
            fullName: fullName,
            email: email,
            subject: subject,
            body: body
        })
        .json()
        scrollY= window.scrollY;
    }

    onMount(() => {
        window.addEventListener("scroll", handleScroll);

        // Cleanup the event listener when the component is destroyed
        return () => {
            window.removeEventListener("scroll", handleScroll);
        };
    });
</script>

<!-- Main -->

<div
    class="fixed w-[50px] h-[200px] border top-1/3 bg-[#EEEEEE] z-[2] max-sm:hidden"
>
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
    <h1
        class="text-center w-[700px] animate-fade-up text-2xl p-3 max-lg:w-auto max-lg:text-xl"
    >
        My name is Akeanant Poomdeesittinon, and my nickname is Gun. I am
        currently studying <span class="text-[#E35205] underline"
            >Computer Science at KMITL</span
        > ,pursuing a Bachelor's degree.
    </h1>
    <p class="animate-fade-up animate-fill-both">Welcome to my website.</p>

    <footer class="absolute bottom-20 animate-bounce animate-delay-100">
        <ChevronsDown size="40px" />
    </footer>
</div>
<!-- About -->
<div id="about" class="flex flex-col w-full text-[#EEEEEE]">
    {#if scrollY > 100}
        <div
            id="aboutData"
            class=" flex w-full h-fit justify-around items-center max-lg:flex-col"
        >
            <!-- DESCRIPTION -->
            <div
                class="animate-fade-right flex flex-col gap-4 h-fit max-w-[37rem] mt-16 max-lg:text-center"
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
                class=" animate-fade-left w-[400px] h-fit justify-center mt-16 p-5 max-sm:w-full"
            >
                <span
                    class="flex bg-gradient-to-r from-[#EEEEEE] via-[#76ABAE] to-[#76ABAE] h-2"
                ></span>
                <img
                    alt=""
                    srcset="/image/pic1.png"
                    class=" object-contain w-[400px] h-fit rounded-b-md shadow-[#76ABAE] shadow-lg max-sm:w-full"
                />
                <p
                    class="hidden mt-5 sm:ml-[0.15rem] text-[1rem] flex-none max-sm:flex flex-col"
                >
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
        </div>
        <!-- Main Box -->
        <div></div>
        <div class="flex flex-col gap-5 max-lg:flex-col items-center">
            <h1 class=" self-center font-bold text-4xl p-4">Skills</h1>
            <div
                class="flex w-full justify-around max-lg:flex-col items-center"
            >
                <!-- FrontEnd -->
                <div
                    class="flex flex-col w-[250px] h-[500px] justify-center text-center animate-fade-up animate-delay-300 max-sm:h-[300px]"
                >
                    <div class="flex flex-col w-full h-full gap-4">
                        <h1 class="font-bold text-2xl">Frontend</h1>
                        <div
                            class="grid grid-cols-2 justify-center p-5 w-full h-full bg-gradient-to-b from-[#76ABAE] rounded-xl"
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
                                        width="50"
                                        height="40"
                                    />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Backend -->
                <div
                    class="flex flex-col w-[250px] h-[500px] justify-center text-center max-sm:h-[300px]"
                >
                    <div
                        class="flex flex-col w-full h-full gap-4 animate-fade-up animate-delay-500"
                    >
                        <h1 class="font-bold text-2xl">Backend</h1>
                        <div
                            class="grid grid-cols-2 justify-center p-5 w-full h-full bg-gradient-to-b from-[#76ABAE] rounded-xl"
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
                    class="flex flex-col w-[250px] h-[500px] justify-center text-center animate-fade-up animate-delay-700 max-sm:h-[300px]"
                >
                    <div class="flex flex-col w-full h-full gap-4">
                        <h1 class="font-bold text-2xl">Database</h1>
                        <div
                            class="grid grid-cols-2 justify-center p-5 w-full h-full bg-gradient-to-b from-[#76ABAE] rounded-xl"
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
        </div>
        <footer
            class="flex justify-center bottom-20 animate-bounce animate-delay-100"
        >
            <ChevronsDown size="40px" />
        </footer>
    {/if}
</div>

<!-- experience -->
<div id="experience" class="flex w-full border h-screen">
    <div class="flex border w-full m-20 max-md:m-5"></div>
</div>
<!-- project -->
<div
    id="projects"
    class="flex flex-col w-full h-screen justify-center items-center"
>
    <h1 class=" self-center font-bold text-4xl p-4 text-white">Projects</h1>
    <div class="w-full m-20 max-md:m-5">
        <div
            class="grid grid-cols-1 md:grid-cols-3 gap-10 p-5 justify-items-center max-lg:hidden"
        >
            <Card.Root
                class="flex flex-col w-80 p-4  bg-gradient-to-b from-[#EEEEEE] to-[#76ABAE] justify-between"
            >
                <Card.Header>
                    <Card.Title>Collection Cow</Card.Title>
                    <Card.Description
                        >Mini Projects for Testing Logic in MVC</Card.Description
                    >
                </Card.Header>
                <Card.Content>
                    <img src="" alt="" srcset="./image/image1.png" />
                </Card.Content>
                <Card.Footer>
                    <Button
                        class="flex w-full"
                        href="https://github.com/tony007x/mvc-test"
                        >See Project</Button
                    >
                </Card.Footer>
            </Card.Root>

            <Card.Root
                class="w-80 p-4 flex flex-col justify-between bg-gradient-to-b from-[#EEEEEE] to-[#76ABAE]"
            >
                <Card.Header>
                    <Card.Title>Restful API (CRUD)</Card.Title>
                    <Card.Description
                        >Using Express.js to manage user data: get, post,
                        update, and delete.
                    </Card.Description>
                </Card.Header>
                <Card.Content>
                    <img src="" alt="" srcset="./image/image2.png" />
                </Card.Content>
                <Card.Footer>
                    <Button
                        class="flex w-full"
                        href="https://github.com/tony007x/comsci_senimar"
                        >See Project</Button
                    >
                </Card.Footer>
            </Card.Root>

            <Card.Root
                class="w-80 border p-4 flex flex-col justify-between bg-gradient-to-b from-[#EEEEEE] to-[#76ABAE]"
            >
                <Card.Header>
                    <Card.Title>CS-Event (KMITL)</Card.Title>
                    <Card.Description
                        >CSEvent is a comprehensive short course registration
                        system designed to streamline the process of course
                        creation, student enrollment, and administration. As the
                        primary developer</Card.Description
                    >
                </Card.Header>
                <Card.Content>
                    <img src="" alt="" srcset="./image/csEvent.png" />
                    <br />
                    <Card.Description>
                        Associated with <strong
                            >King Mongkut's Institute of Technology Ladkrabang</strong
                        >
                    </Card.Description>
                </Card.Content>
                <Card.Footer>
                    <Button
                        class="flex w-full"
                        href="https://csevent.vercel.app/">See Project</Button
                    >
                </Card.Footer>
            </Card.Root>
        </div>
        <!-- Responesive -->
        <Carousel.Root
            class="lg:hidden flex  justify-center w-full  shadow-black  backdrop-blur-lg"
        >
            <div class="absolute">
                <!-- <ChevronsRight size="40px" color="white" /> -->
                <Carousel.Previous class=" " />
                <Carousel.Next class="  " />
            </div>
            <Carousel.Content>
                <Carousel.Item class="flex justify-center">
                    <Card.Root
                        class="flex flex-col bg-gradient-to-b m-10 from-[#EEEEEE] to-[#76ABAE] justify-between shadow-lg shadow-black"
                    >
                        <Card.Header>
                            <Card.Title>Collection Cow</Card.Title>
                            <Card.Description
                                >Mini Projects for Testing Logic in MVC</Card.Description
                            >
                        </Card.Header>
                        <Card.Content>
                            <img src="" alt="" srcset="./image/image1.png" />
                        </Card.Content>
                        <Card.Footer>
                            <Button
                                class="flex w-full"
                                href="https://github.com/tony007x/mvc-test"
                                >See Project</Button
                            >
                        </Card.Footer>
                    </Card.Root>
                </Carousel.Item>

                <Carousel.Item class="flex">
                    <Card.Root
                        class="flex flex-col bg-gradient-to-b m-10 from-[#EEEEEE] to-[#76ABAE] justify-between  shadow-lg shadow-black"
                    >
                        <Card.Header>
                            <Card.Title>Restful API (CRUD)</Card.Title>
                            <Card.Description
                                >Using Express.js to manage user data: get,
                                post, update, and delete.</Card.Description
                            >
                        </Card.Header>
                        <Card.Content>
                            <img src="" alt="" srcset="./image/image2.png" />
                        </Card.Content>
                        <Card.Footer>
                            <Button
                                class="flex w-full"
                                href="https://github.com/tony007x/mvc-test"
                                >See Project</Button
                            >
                        </Card.Footer>
                    </Card.Root>
                </Carousel.Item>

                <Carousel.Item class="flex">
                    <Card.Root
                        class="flex flex-col bg-gradient-to-b m-10 from-[#EEEEEE] to-[#76ABAE] justify-between shadow-lg shadow-black"
                    >
                        <Card.Header>
                            <Card.Title>CS-Event (KMITL)</Card.Title>
                            <Card.Description
                                >CSEvent is a comprehensive short course
                                registration system designed to streamline the
                                process of course creation, student enrollment,
                                and administration. As the primary developer.C</Card.Description
                            >
                        </Card.Header>
                        <Card.Content>
                            <img src="" alt="" srcset="./image/csEvent.png" />
                            <br />
                            <Card.Description>
                                Associated with <strong
                                    >King Mongkut's Institute of Technology
                                    Ladkrabang</strong
                                >
                            </Card.Description>
                        </Card.Content>

                        <Card.Footer>
                            <Button
                                class="flex w-full"
                                href="https://github.com/tony007x/mvc-test"
                                >See Project</Button
                            >
                        </Card.Footer>
                    </Card.Root>
                </Carousel.Item>
            </Carousel.Content>
        </Carousel.Root>
    </div>
</div>

<!-- contact -->
<div
    id="contact"
    class="flex w-full border h-screen justify-center items-center"
>
    <div
        class="flex flex-col w-1/2 bg-[#EEEEEE] rounded-lg justify-center items-center p-5 gap-5 max-lg:w-full m-5"
    >
        <form class=" flex flex-col gap-5">
            <h1 class="text-center font-bold text-2xl mb-4">
                Send me a message 💌
            </h1>
            <div class="flex gap-5">
                <div>
                    <Label
                        for="Fullname"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Fullname</Label
                    >
                    <Input type="text" id="email" bind:value={fullName} required />
                </div>
                <div>
                    <Label
                        for="email"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Email</Label
                    >
                    <Input type="email" id="body" bind:value={email} required />
                </div>
            </div>
            <div>
                <Label
                    for="subject"
                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                    >Subject</Label
                >
                <Input type="subject" id="body" bind:value={subject} required />
                <Label
                    for="body"
                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                    >Body</Label
                >
                <Textarea
                    id="body"
                    bind:value={body}
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    required
                />
            </div>

            <button
                class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                on:click={sendEmail}
                >Submit</button
            >
        </form>
    </div>
</div>
