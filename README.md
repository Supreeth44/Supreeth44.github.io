<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Supreeth Rumalad | Portfolio</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0a0a0a;
            color: #e2e8f0;
        }
        .section-glow {
            position: relative;
            z-index: 1;
        }
        .section-glow::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 50%;
            height: 50%;
            background: radial-gradient(circle, rgba(29, 78, 216, 0.15) 0%, rgba(29, 78, 216, 0) 70%);
            z-index: -1;
            pointer-events: none;
        }
        .nav-link {
            position: relative;
            transition: color 0.3s ease;
        }
        .nav-link::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -4px;
            left: 50%;
            transform: translateX(-50%);
            background-color: #3b82f6;
            transition: width 0.3s ease;
        }
        .nav-link:hover::after, .nav-link.active::after {
            width: 100%;
        }
        .project-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header & Navigation -->
    <header id="header" class="fixed top-0 left-0 right-0 z-40 bg-black/30 backdrop-blur-sm transition-all duration-300">
        <div class="container mx-auto px-6 py-4 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-white">SR.</a>
            <nav class="hidden md:flex items-center space-x-8">
                <a href="#about" class="nav-link text-gray-300 hover:text-white">About</a>
                <a href="#experience" class="nav-link text-gray-300 hover:text-white">Experience</a>
                <a href="#projects" class="nav-link text-gray-300 hover:text-white">Projects</a>
                <a href="#skills" class="nav-link text-gray-300 hover:text-white">Skills</a>
                <a href="#education" class="nav-link text-gray-300 hover:text-white">Education</a>
                <a href="#contact" class="nav-link text-gray-300 hover:text-white">Contact</a>
            </nav>
            <button id="mobile-menu-button" class="md:hidden p-2 rounded-md text-gray-300 hover:text-white hover:bg-gray-800 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white">
                <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
                </svg>
            </button>
        </div>
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden px-6 pt-2 pb-4 space-y-2 bg-gray-900/80 backdrop-blur-sm">
            <a href="#about" class="block nav-link text-gray-300 hover:text-white py-2">About</a>
            <a href="#experience" class="block nav-link text-gray-300 hover:text-white py-2">Experience</a>
            <a href="#projects" class="block nav-link text-gray-300 hover:text-white py-2">Projects</a>
            <a href="#skills" class="block nav-link text-gray-300 hover:text-white py-2">Skills</a>
            <a href="#education" class="block nav-link text-gray-300 hover:text-white py-2">Education</a>
            <a href="#contact" class="block nav-link text-gray-300 hover:text-white py-2">Contact</a>
        </div>
    </header>

    <main class="container mx-auto px-6 pt-24 md:pt-32">

        <!-- Hero Section -->
        <section id="home" class="min-h-[80vh] flex flex-col justify-center items-start section-glow">
            <p class="text-lg text-blue-400 mb-2">Hi, my name is</p>
            <h1 class="text-5xl md:text-7xl font-bold text-white">Supreeth Rumalad.</h1>
            <h2 class="text-4xl md:text-6xl font-bold text-gray-400 mt-2">I build things for the web.</h2>
            <p class="mt-6 max-w-3xl text-gray-400">
                I'm an aspiring Software Engineer and a final-year Computer Science student with a passion for technology's transformative potential, especially in Python, AI, and ML.
            </p>
            <div class="mt-8 flex items-center space-x-4">
                <a href="#" id="get-in-touch-btn" class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-6 rounded-lg transition-transform duration-300 hover:scale-105">Get In Touch</a>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="py-20 md:py-32 section-glow">
            <h3 class="text-3xl font-bold text-white mb-8 flex items-center"><span class="text-blue-400 mr-3">01.</span> About Me</h3>
            <div class="grid grid-cols-1 md:grid-cols-5 gap-10">
                <div class="md:col-span-3 text-gray-400 space-y-4 text-lg">
                    <p>
                        I'm a final-year B.E. student in Computer Science and Engineering (CSE) at Sapthagiri College of Engineering. As a passionate AI enthusiast, I'm driven by technology's transformative potential and constantly exploring how fields like AI and ML can solve real-world problems.
                    </p>
                    <p>
                        Beyond the classroom, I've had the opportunity to organize several college events, which has honed my communication and leadership skills. I thrive in team settings and have enjoyed collaborating with peers to achieve common goals.
                    </p>
                </div>
                <div class="md:col-span-2 flex justify-center items-center">
                     <div class="w-64 h-64 rounded-lg bg-gray-800 relative overflow-hidden group">
                        <img src="http://googleusercontent.com/file_content/1" alt="Supreeth Rumalad" class="w-full h-full object-cover rounded-lg transition-transform duration-500 group-hover:scale-110">
                        <div class="absolute inset-0 bg-blue-600/20"></div>
                     </div>
                </div>
            </div>
        </section>

        <!-- Experience Section -->
        <section id="experience" class="py-20 md:py-32 section-glow">
            <h3 class="text-3xl font-bold text-white mb-12 flex items-center"><span class="text-blue-400 mr-3">02.</span> Experience & Activities</h3>
            <div class="max-w-3xl mx-auto">
                <div class="relative border-l-2 border-gray-700 pl-8 space-y-12">
                    <div class="relative">
                        <div class="absolute -left-[42px] top-1 h-4 w-4 rounded-full bg-blue-500 ring-8 ring-gray-900"></div>
                        <h4 class="text-xl font-semibold text-white">Core Team Member</h4>
                        <p class="text-blue-400 font-medium">GDSC (Google Developer Student Clubs)</p>
                        <p class="mt-2 text-gray-400">Actively involved in fostering a culture of innovation and learning by organizing workshops, tech talks, and coding events for the student community.</p>
                    </div>
                    <div class="relative">
                        <div class="absolute -left-[42px] top-1 h-4 w-4 rounded-full bg-blue-500 ring-8 ring-gray-900"></div>
                        <h4 class="text-xl font-semibold text-white">Event Organizer</h4>
                        <p class="text-blue-400 font-medium">College Events</p>
                        <p class="mt-2 text-gray-400">Organized several college events, honing communication, leadership, and project management skills while collaborating with teams to achieve successful outcomes.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section id="projects" class="py-20 md:py-32 section-glow">
            <h3 class="text-3xl font-bold text-white mb-12 flex items-center"><span class="text-blue-400 mr-3">03.</span> Some Things I've Built</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="project-card bg-gray-900/50 p-6 rounded-lg border border-gray-800 flex flex-col">
                    <h4 class="text-xl font-semibold text-white mb-2">Real-Time AQI Analysis & Guidance</h4>
                    <p class="text-gray-400 mb-4 flex-grow">A system to provide real-time Air Quality Index (AQI) analysis using weather APIs, featuring a warning system for hazardous conditions.</p>
                    <ul class="flex flex-wrap text-sm text-blue-400 font-mono">
                        <li class="mr-3 mb-1">Python</li>
                        <li class="mr-3 mb-1">Flask</li>
                        <li class="mr-3 mb-1">Leaflet.js</li>
                    </ul>
                </div>
                <div class="project-card bg-gray-900/50 p-6 rounded-lg border border-gray-800 flex flex-col">
                    <h4 class="text-xl font-semibold text-white mb-2">AI-Powered Educational Assistant</h4>
                    <p class="text-gray-400 mb-4 flex-grow">A platform offering study and code assistance, with a module to automatically generate question papers from documents using NLP.</p>
                    <ul class="flex flex-wrap text-sm text-blue-400 font-mono">
                        <li class="mr-3 mb-1">Python</li>
                        <li class="mr-3 mb-1">Streamlit</li>
                        <li class="mr-3 mb-1">LangChain</li>
                    </ul>
                </div>
                <div class="project-card bg-gray-900/50 p-6 rounded-lg border border-gray-800 flex flex-col">
                    <h4 class="text-xl font-semibold text-white mb-2">Multilingual AI Translation System</h4>
                    <p class="text-gray-400 mb-4 flex-grow">A real-time communication platform that supports instant messaging across different languages, powered by an AI translation service.</p>
                    <ul class="flex flex-wrap text-sm text-blue-400 font-mono">
                        <li class="mr-3 mb-1">Node.js</li>
                        <li class="mr-3 mb-1">Socket.IO</li>
                        <li class="mr-3 mb-1">React</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Skills & Certifications Section -->
        <section id="skills" class="py-20 md:py-32 section-glow">
            <h3 class="text-3xl font-bold text-white mb-12 flex items-center"><span class="text-blue-400 mr-3">04.</span> Skills & Certifications</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                <div>
                    <h4 class="text-2xl font-semibold text-white mb-6">Top Skills</h4>
                    <ul class="space-y-3">
                        <li class="flex items-center text-gray-300"><span class="text-blue-400 mr-3">▹</span>Amazon Web Services (AWS)</li>
                        <li class="flex items-center text-gray-300"><span class="text-blue-400 mr-3">▹</span>Python & Java</li>
                        <li class="flex items-center text-gray-300"><span class="text-blue-400 mr-3">▹</span>AI & Machine Learning</li>
                        <li class="flex items-center text-gray-300"><span class="text-blue-400 mr-3">▹</span>Leadership & Communication</li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-2xl font-semibold text-white mb-6">Certifications</h4>
                    <ul class="space-y-3">
                        <li class="flex items-center text-gray-300"><span class="text-blue-400 mr-3">▹</span>AWS Academy Graduate</li>
                        <li class="flex items-center text-gray-300"><span class="text-blue-400 mr-3">▹</span>Networking Fundamentals on Google Cloud</li>
                        <li class="flex items-center text-gray-300"><span class="text-blue-400 mr-3">▹</span>Deloitte - Data Analytics Simulation</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Education Section -->
        <section id="education" class="py-20 md:py-32 section-glow">
            <h3 class="text-3xl font-bold text-white mb-12 flex items-center"><span class="text-blue-400 mr-3">05.</span> Education</h3>
            <div class="space-y-8 max-w-3xl">
                <div class="bg-gray-900/50 p-6 rounded-lg border border-gray-800 hover:border-blue-500/50 transition-colors duration-300">
                    <p class="text-gray-400">2022 - 2026</p>
                    <h4 class="text-xl font-semibold text-white mt-1">Bachelor of Engineering - Computer Science</h4>
                    <p class="text-gray-300">Sapthagiri College of Engineering (VTU)</p>
                </div>
                <div class="bg-gray-900/50 p-6 rounded-lg border border-gray-800 hover:border-blue-500/50 transition-colors duration-300">
                    <p class="text-gray-400">2020 - 2022</p>
                    <h4 class="text-xl font-semibold text-white mt-1">PUC - Computer Science</h4>
                    <p class="text-gray-300">Vidya Mandir IND PU college</p>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-20 md:py-32 text-center section-glow">
            <h3 class="text-2xl font-semibold text-blue-400 mb-2">06. What's Next?</h3>
            <h4 class="text-4xl md:text-5xl font-bold text-white mb-4">Get In Touch</h4>
            <p class="max-w-xl mx-auto text-gray-400 mb-8">
                I'm currently seeking opportunities to apply my skills and passion for technology. Whether you have a question or just want to say hi, my inbox is always open.
            </p>
            <a href="#" id="say-hello-btn" class="inline-block bg-blue-600 hover:bg-blue-700 text-white font-semibold py-4 px-8 rounded-lg transition-transform duration-300 hover:scale-105">Say Hello</a>
        </section>

    </main>

    <!-- Footer -->
    <footer class="text-center py-8">
        <p class="text-gray-500">Designed & Built by Supreeth Rumalad</p>
         <div class="mt-4 flex items-center justify-center space-x-6">
            <a href="https://www.linkedin.com/in/supreeth-rumalad-3b65a235a/" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition duration-300"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24"><path fill-rule="evenodd" d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" clip-rule="evenodd"/></svg></a>
            <a href="https://www.instagram.com/supreeth_r/" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition duration-300"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.162 6.162 6.162 6.162-2.759 6.162-6.162-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4s1.791-4 4-4 4 1.79 4 4-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44 1.441-.645 1.441-1.44c0-.795-.645-1.44-1.441-1.44z"/></svg></a>
             <a href="mailto:supreethr8055@gmail.com" class="text-gray-400 hover:text-white transition duration-300"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24"><path d="M22 6c0-1.1-.9-2-2-2H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6zm-2 0l-8 5-8-5h16zm0 12H4V8l8 5 8-5v10z"/></svg></a>
        </div>
    </footer>

    <!-- Contact Modal -->
    <div id="contact-modal" class="hidden fixed inset-0 bg-black/60 backdrop-blur-sm flex items-center justify-center z-50 opacity-0 transition-opacity duration-300 ease-in-out">
        <div id="modal-content" class="bg-gray-900 rounded-lg shadow-xl p-8 max-w-sm w-full relative scale-95 transition-all duration-300 ease-in-out">
            <button id="close-modal-btn" class="absolute top-3 right-3 text-gray-500 hover:text-white text-3xl font-bold leading-none">&times;</button>
            <h3 class="text-2xl font-bold text-white mb-6 text-center">Connect with Me</h3>
            <div class="flex flex-col space-y-4">
                <a href="https://www.linkedin.com/in/supreeth-rumalad-3b65a235a/" target="_blank" rel="noopener noreferrer" class="flex items-center p-3 bg-gray-800 rounded-lg hover:bg-gray-700 transition-colors duration-300"><svg class="w-6 h-6 mr-4 text-blue-400" fill="currentColor" viewBox="0 0 24 24"><path fill-rule="evenodd" d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" clip-rule="evenodd"/></svg><span class="text-white font-medium">LinkedIn</span></a>
                <a href="https://www.instagram.com/supreeth_r/" target="_blank" rel="noopener noreferrer" class="flex items-center p-3 bg-gray-800 rounded-lg hover:bg-gray-700 transition-colors duration-300"><svg class="w-6 h-6 mr-4 text-pink-400" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.162 6.162 6.162 6.162-2.759 6.162-6.162-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4s1.791-4 4-4 4 1.79 4 4-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44 1.441-.645 1.441-1.44c0-.795-.645-1.44-1.441-1.44z"/></svg><span class="text-white font-medium">Instagram</span></a>
                <a href="mailto:supreethr8055@gmail.com" class="flex items-center p-3 bg-gray-800 rounded-lg hover:bg-gray-700 transition-colors duration-300"><svg class="w-6 h-6 mr-4 text-gray-400" fill="currentColor" viewBox="0 0 24 24"><path d="M22 6c0-1.1-.9-2-2-2H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6zm-2 0l-8 5-8-5h16zm0 12H4V8l8 5 8-5v10z"/></svg><span class="text-white font-medium">Email</span></a>
            </div>
        </div>
    </div>

    <script>
        // --- Mobile Menu Toggle ---
        const mobileMenuButton = document.getElementById('mobile-menu-button');
        const mobileMenu = document.getElementById('mobile-menu');
        mobileMenuButton.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });
        const mobileNavLinks = document.querySelectorAll('#mobile-menu a');
        mobileNavLinks.forEach(link => {
            link.addEventListener('click', () => {
                mobileMenu.classList.add('hidden');
            });
        });

        // --- Active Nav Link Scroll Spy ---
        const sections = document.querySelectorAll('section');
        const navLinks = document.querySelectorAll('header nav a');
        window.onscroll = () => {
            let current = 'home';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                if (pageYOffset >= sectionTop - 80) {
                    current = section.getAttribute('id');
                }
            });

            navLinks.forEach(link => {
                link.classList.remove('active', 'text-white');
                if (link.href.includes(current)) {
                    link.classList.add('active', 'text-white');
                }
            });
        };

        // --- Contact Modal Handling ---
        const getInTouchBtn = document.getElementById('get-in-touch-btn');
        const sayHelloBtn = document.getElementById('say-hello-btn');
        const contactModal = document.getElementById('contact-modal');
        const modalContent = document.getElementById('modal-content');
        const closeModalBtn = document.getElementById('close-modal-btn');

        const openModal = (e) => {
            e.preventDefault();
            contactModal.classList.remove('hidden');
            setTimeout(() => {
                contactModal.classList.remove('opacity-0');
                modalContent.classList.remove('scale-95');
            }, 10);
        };

        const closeModal = () => {
            contactModal.classList.add('opacity-0');
            modalContent.classList.add('scale-95');
            setTimeout(() => contactModal.classList.add('hidden'), 300);
        };

        getInTouchBtn.addEventListener('click', openModal);
        sayHelloBtn.addEventListener('click', openModal);
        closeModalBtn.addEventListener('click', closeModal);
        contactModal.addEventListener('click', (e) => {
            if (e.target === contactModal) {
                closeModal();
            }
        });
    </script>
</body>
</html>
