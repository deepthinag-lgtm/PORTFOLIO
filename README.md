<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio - Deepthi Nagaraj</title>

    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;800&family=Figtree:wght@400;600;800&family=Irish+Grover&family=Kolker+Brush&family=Marcellus&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>

    <style>
        :root {
            --primary-brown: #5B251A;
            --off-white: #FBF0F0; 
            --light-pink: #FFC0CB;
            --teal-glow: #77D8E1;
            --custom-dark: #252C36; 
            --input-border: #D0D5DD;
        }

        /* =========================
            BASE STYLES
        ========================= */
        body, html {
            margin: 0; padding: 0;
            overflow: hidden; 
            background-color: var(--off-white);
            font-family: 'Montserrat', sans-serif;
            min-height: 100vh;
            color: var(--custom-dark);
            transition: background 0.6s ease, color 0.6s ease;
        }

        body.dark-mode {
            background-color: #000;
            color: var(--off-white); 
        }

        body::after {
            content: "";
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-image: url("C:/Users/Deepp/Downloads/Index.html/BG IMAGE.avif");
            background-size: cover; background-position: center;
            opacity: 0.5; z-index: -1; pointer-events: none;
            transition: opacity 0.6s ease;
        }
        body.dark-mode::after { opacity: 0.25; }

        /* =========================
            NAVBAR
        ========================= */
        nav {
            position: fixed;
            top: 25px; left: 50%;
            transform: translateX(-50%);
            width: auto; min-width: 650px; height: 65px;
            background: rgba(255, 255, 255, 0.3); 
            backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 10px 0 15px; z-index: 1000;
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 100px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.06);
        }

        .nav-links { display: flex; align-items: center; gap: 30px; }
        nav a { 
            text-decoration: none; color: var(--custom-dark); 
            font-size: 13px; font-weight: 600; text-transform: uppercase; 
            cursor: pointer; transition: color 0.3s; padding-bottom: 4px;
        }
        body.dark-mode nav a { color: white; }
        .selected-nav { border-bottom: 2px solid var(--primary-brown); }
        body.dark-mode .selected-nav { border-bottom: 2px solid var(--teal-glow); }

        .logo-placeholder { width: 44px; height: 44px; background: var(--primary-brown); border-radius: 12px; overflow: hidden; display: flex; cursor: pointer; transition: transform 0.3s; }
        .logo-placeholder img { width: 100%; height: 100%; object-fit: cover; }

        .nav-cta { 
            background: var(--custom-dark); color: white !important; 
            padding: 12px 28px; border-radius: 50px; 
            font-weight: 600; margin-left: 10px; transition: background 0.3s;
        }
        body.dark-mode .nav-cta { background: var(--off-white); color: #000 !important; }

        /* =========================
            HERO SECTION
        ========================= */
        .hero {
            position: relative;
            height: 100vh;
            display: flex; justify-content: center; align-items: center;
        }

        .logo-sequence { display: flex; align-items: center; z-index: 5; }
        .letter { font-size: 200px; color: var(--primary-brown); line-height: 1; display: inline-block; transition: color 0.6s ease; }
        body.dark-mode .letter { color: white; }
        .letter-t { font-family: 'Kolker Brush', cursive; margin-right: 50px; }
        .irish { font-family: 'Irish Grover', cursive; }
        .kolker { font-family: 'Kolker Brush', cursive; }

        .frame-container {
            position: relative; width: 190px; height: 320px;
            border: 2px solid var(--custom-dark);
            border-bottom: 15px solid #1a1a1a;
            border-radius: 200px; overflow: hidden;
            transition: all 0.5s ease;
            background: transparent;
        }

        body.dark-mode .frame-container {
            border-color: var(--teal-glow);
            box-shadow: 0 0 40px rgba(119, 216, 225, 0.4);
            background: radial-gradient(circle, rgba(119, 216, 225, 0.6) 0%, rgba(0, 0, 0, 0) 70%);
        }
        
        .frame-img { 
            width: 100%; height: 100%; object-fit: cover; 
            transition: opacity 0.4s ease-in-out; 
        }

        .content-sides {
            position: absolute; width: 100%; display: flex;
            justify-content: space-between; padding: 0 6%;
            box-sizing: border-box; opacity: 0; pointer-events: none;
        }
        .side-box { max-width: 320px; cursor: pointer; }
        .side-box h2 { font-size: 30px; font-weight: 600; text-transform: uppercase; transition: all 0.5s ease; }

        #txtArch, #txtUI { color: var(--custom-dark); }
        
        body.dark-mode #txtArch { color: white; }
        body.dark-mode #txtUI {
            background: radial-gradient(circle, #77D8E1 0%, #FFFFFF 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .side-box p { font-size: 13px; line-height: 1.8; text-align: justify; transition: opacity 0.5s; }
        body.dark-mode .side-box p { opacity: 0.7; color: #fff; }

        /* =========================
            BLOG PAGE SECTION
        ========================= */
        #blogSection {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            display: none; flex-direction: column; align-items: center;
            background-color: inherit; z-index: 10; padding-top: 120px;
            overflow-y: auto;
        }

        .blog-container { width: 85%; max-width: 1100px; padding-bottom: 100px; }
        .blog-nav-filter { display: flex; gap: 25px; border-bottom: 1px solid rgba(0,0,0,0.1); padding-bottom: 15px; margin-bottom: 40px; }
        .blog-nav-filter span { font-weight: 600; color: #667085; font-size: 14px; cursor: pointer; }
        .blog-nav-filter span.active { color: var(--custom-dark); border-bottom: 2px solid var(--custom-dark); padding-bottom: 13px; }

        .blog-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 32px; }
        .blog-card { text-decoration: none; color: inherit; }
        .blog-card img { width: 100%; height: 280px; object-fit: cover; border-radius: 12px; }
        .blog-card .meta { margin: 20px 0 12px; font-weight: 600; font-size: 14px; color: var(--primary-brown); }
        .blog-card h3 { font-size: 24px; margin: 0 0 12px; font-weight: 700; color: #101828; }
        .blog-card p { font-size: 16px; color: #667085; line-height: 1.5; margin-bottom: 20px; }
        .blog-card .read-link { font-weight: 700; color: #101828; display: flex; align-items: center; gap: 8px; }

        /* =========================
            SERVICES SECTION
        ========================= */
        #servicesSection {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            display: none; flex-direction: column; justify-content: center; align-items: center;
            background-color: inherit; z-index: 10;
        }

        .services-header {
            margin-bottom: 30px; font-family: 'Figtree', sans-serif;
            text-transform: uppercase; letter-spacing: 4px; font-size: 14px;
            border-top: 1px solid rgba(0,0,0,0.1); padding-top: 20px; width: 80%; text-align: center;
        }

        .slider-wrapper { width: 90%; display: flex; flex-direction: column; align-items: center; gap: 40px; }
        .services-slider {
            display: flex; gap: 30px; overflow-x: auto; width: 100%;
            padding: 20px 0; cursor: grab; scroll-behavior: smooth;
            scrollbar-width: none; -ms-overflow-style: none;
        }
        .services-slider::-webkit-scrollbar { display: none; }
        .service-card { 
            flex: 0 0 calc(33.33% - 20px); background: white; 
            box-shadow: 0 10px 30px rgba(0,0,0,0.05); display: flex; flex-direction: column; 
            border-radius: 20px; overflow: hidden;
        }
        .service-card img { width: 100%; height: 400px; object-fit: cover; }
        .service-info { padding: 40px 20px; text-align: center; font-family: 'Figtree', sans-serif; }
        .service-info h3 { margin: 0 0 10px 0; font-weight: 600; font-size: 18px; text-transform: uppercase; letter-spacing: 2px; }
        .service-info p { font-size: 13px; color: #666; line-height: 1.6; }
        .scroll-indicator { width: 200px; height: 4px; background: rgba(0,0,0,0.1); border-radius: 10px; position: relative; overflow: hidden; }
        .scroll-progress { position: absolute; height: 100%; width: 40%; background: var(--primary-brown); border-radius: 10px; transition: transform 0.1s linear; }

        /* =========================
            ABOUT ME SECTION
        ========================= */
        #aboutSection {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            display: none; flex-direction: column; justify-content: center; align-items: center;
            background-color: inherit; z-index: 10;
        }
        .about-grid { display: flex; align-items: center; justify-content: center; gap: 60px; width: 90%; flex-grow: 1; }
        .name-label { font-size: 28px; font-weight: 600; text-transform: uppercase; transition: color 0.5s; }
        .big-text { font-size: 110px; font-weight: 600; line-height: 0.9; text-transform: uppercase; margin: 0; letter-spacing: -2px; }
        .about-image-container { position: relative; width: 400px; height: 550px; }
        .about-img { width: 100%; height: 100%; object-fit: cover; border-radius: 24px; }
        .hi-badge {
            position: absolute; bottom: 20px; left: -45px; width: 110px; height: 110px; 
            background-color: var(--primary-brown); color: white; border-radius: 50%; 
            display: flex; justify-content: center; align-items: center; 
            font-size: 36px; font-weight: 600; transform: scale(0); 
            box-shadow: 0 10px 25px rgba(0,0,0,0.2); z-index: 2;
        }

        /* =========================
            CONTACT SECTION (UPDATED)
        ========================= */
        #contactSection {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            display: none; justify-content: center; align-items: center;
            background-color: inherit; z-index: 10; padding: 0 8%;
            gap: 100px;
        }

        .contact-visual-text {
            flex: 1;
            max-width: 550px;
            font-family: 'Marcellus', serif;
            line-height: 0.85;
            text-align: left;
        }

        .contact-visual-text h1 {
            font-size: 115px;
            margin: 0;
            font-weight: 400;
            letter-spacing: -4px;
            color: var(--custom-dark);
            background-image: url('C:/Users/Deepp/Downloads/Index.html/chittara_art.png'); 
            background-size: cover;
            background-position: center;
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: rgba(37, 44, 54, 0.4);
        }

        .contact-visual-text h1 span { display: block; }
        .contact-visual-text .italic-font { font-style: italic; }

        .contact-visual-text .sub-hello {
            font-size: 28px;
            margin-top: 80px; 
            display: block;   
            text-align: right; 
            letter-spacing: -0.5px;
            border-top: 1px solid rgba(37, 44, 54, 0.3);
            padding-top: 15px;
            color: var(--custom-dark);
            -webkit-text-fill-color: initial;
            background: none;
        }

        .contact-container {
            flex: 1;
            max-width: 500px;
            width: 100%;
        }

        .input-group { margin-bottom: 35px; }
        .input-group label { 
            display: block; font-weight: 600; font-size: 13px; 
            margin-bottom: 15px; text-transform: uppercase; 
            color: var(--primary-brown); letter-spacing: 1px;
        }
        
        .chip-container { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 10px; }
        .chip {
            padding: 8px 20px; border: 1px solid var(--input-border);
            border-radius: 100px; font-size: 14px; font-weight: 500;
            cursor: pointer; transition: all 0.3s ease;
            background: white; color: var(--custom-dark);
        }
        .chip.active {
            background: var(--primary-brown); border-color: var(--primary-brown); color: white;
        }

        .input-group input, .input-group textarea {
            width: 100%; border: none; border-bottom: 1px solid var(--input-border);
            padding: 12px 0; background: transparent; font-family: inherit;
            font-size: 16px; outline: none; transition: border-color 0.3s;
        }
        .input-group input:focus, .input-group textarea:focus { border-bottom-color: var(--primary-brown); }

        .btn-submit {
            background: var(--primary-brown); color: white; border: none;
            padding: 15px 50px; border-radius: 4px; font-weight: 600;
            font-size: 16px; cursor: pointer; transition: all 0.3s;
            width: 100%;
        }
        .btn-submit:hover { opacity: 0.9; }
        .btn-submit.success { background: #28a745; }

        /* =========================
            TICKER
        ========================= */
        .ticker-container {
            width: 100%; overflow: hidden; background: rgba(0,0,0,0.03); 
            padding: 30px 0; position: absolute; bottom: 0; display: flex; white-space: nowrap;
        }
        .ticker-wrapper { 
            display: flex; flex-shrink: 0; 
            animation: ticker-loop 15s linear infinite; 
            animation-play-state: paused; 
        }
        .ticker-item { flex-shrink: 0; display: flex; align-items: center; padding: 0 50px; }
        .ticker-item img { height: 40px; width: auto; transition: transform 0.3s; }
        
        @keyframes ticker-loop { 
            0% { transform: translateX(0); } 
            100% { transform: translateX(-50%); } 
        }
    </style>
</head>

<body>

<nav id="topNav">
    <div class="logo-link" id="homeLogo">
        <div class="logo-placeholder"><img src="C:\Users\Deepp\Downloads\Index.html\Untitled-1.png"></div>
    </div>
    <div class="nav-links">
        <a id="navAbout">About</a>
        <a id="navServices">Services</a>
        <a id="navBlog">Blogs</a>
        <a class="nav-cta" id="navConnect">Connect</a>
    </div>
</nav>

<section class="hero" id="heroSection">
    <div class="logo-sequence" id="logoSeq">
        <span class="letter irish">S</span>
        <span class="letter letter-t">t</span>
        <div class="frame-container" id="pill">
            <img id="mainImg" class="frame-img" src="C:\Users\Deepp\Downloads\Index.html\cover 2.jpeg">
        </div>
        <span class="letter irish" id="letterD" style="margin-left:30px;">d</span>
        <span class="letter kolker">i</span>
        <span class="letter kolker">o</span>
    </div>

    <div class="content-sides" id="contentSides">
        <div class="side-box" id="btnArch">
            <h2 id="txtArch">Architect</h2>
            <p>As an architect dedicated to sustainability, I design eco-conscious structures that balance structural integrity with environmental respect.</p>
        </div>
        <div class="side-box" id="btnUI">
            <h2 id="txtUI">UI UX Designer</h2>
            <p>I am a problem-solver at heart, specializing in crafting seamless digital ecosystems and user-centric interfaces.</p>
        </div>
    </div>
</section>

<section id="blogSection">
    <div class="blog-container">
        <div class="blog-nav-filter">
            <span class="active">View all</span>
        </div>
        <div class="blog-grid">
            <a href="https://medium.com/@deepparinag/the-shift-to-anticipatory-ux-designing-agentic-intelligence-for-cybersecuritys-new-frontier-e09aac135b61" target="_blank" class="blog-card">
                <img src="C:\Users\Deepp\Downloads\Index.html\blog.png">
                <div class="meta">Deepthi Nagaraj • Dec 9, 2025</div>
                <h3>The Shift to Anticipatory UX</h3>
                <p>Designing agentic intelligence for cybersecurity's new frontier. Exploring the move from reactive tools to proactive user experiences.</p>
                <div class="read-link">Read post ↗</div>
            </a>
        </div>
    </div>
</section>

<section id="servicesSection">
    <div class="services-header">Design Services</div>
    <div class="slider-wrapper">
        <div class="services-slider" id="dragSlider">
            <div class="service-card"><img src="C:\Users\Deepp\Downloads\Index.html\Artboard 1.png"><div class="service-info"><h3>Architecture</h3><p>Architecture plans, 3D models, walkthrough, Renders, execution, turnkey.</p></div></div>
            <div class="service-card"><img src="C:\Users\Deepp\Downloads\Index.html\interior.jpg"><div class="service-info"><h3>Interior Design</h3><p>3D models, walkthrough, Renders, execution, turnkey.</p></div></div>
            <div class="service-card"><img src="C:\Users\Deepp\Downloads\Index.html\UI UX.png"><div class="service-info"><h3>Web Design</h3><p>Seamless digital ecosystems and interfaces.</p></div></div>
            <div class="service-card"><img src="C:\Users\Deepp\Downloads\Index.html\app.png"><div class="service-info"><h3>App Design</h3><p>User-centric mobile application experiences.</p></div></div>
            <div class="service-card"><img src="C:\Users\Deepp\Downloads\Index.html\illustATION.jpg"><div class="service-info"><h3>Illustrations</h3><p>Custom visual storytelling and digital art.</p></div></div>
        </div>
        <div class="scroll-indicator"><div class="scroll-progress" id="scrollProgress"></div></div>
    </div>
</section>

<section id="aboutSection">
    <div class="about-grid">
        <div class="about-left" style="flex:1; display:flex; flex-direction:column; align-items:flex-end; text-align:right;">
            <span class="name-label">Deepthi Nagaraj</span>
        </div>
        <div class="about-image-container">
            <img src="C:\Users\Deepp\Downloads\Index.html\about me.jpeg" class="about-img">
            <div class="hi-badge" id="hiBadge">Hi</div>
        </div>
        <div class="about-right" style="flex:1; display:flex; flex-direction:column; align-items:flex-start; text-align:left;">
            <h1 class="big-text">DESIGNER</h1>
            <p style="max-width:320px; font-size:15px; margin-top:25px;">I'm a Bangalore based designer who integrates digital and physical realm with creativity.</p>
        </div>
    </div>
    <div class="ticker-container">
        <div class="ticker-wrapper" id="masterTicker">
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Replit-Light.svg"></div>
            <div class="ticker-item"><img src="https://cdn.worldvectorlogo.com/logos/chatgpt-4.svg"></div>
            <div class="ticker-item"><img src="https://cdn.simpleicons.org/miro/050505"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Figma-Light.svg"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Photoshop.svg"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Illustrator.svg"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/VSCode-Light.svg"></div>
            <div class="ticker-item"><img src="https://cdn.simpleicons.org/autodesk/5B251A"></div>
            <div class="ticker-item"><img src="https://cdn.simpleicons.org/sketchup/5B251A"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Replit-Light.svg"></div>
            <div class="ticker-item"><img src="https://cdn.worldvectorlogo.com/logos/chatgpt-4.svg"></div>
            <div class="ticker-item"><img src="https://cdn.simpleicons.org/miro/050505"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Figma-Light.svg"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Photoshop.svg"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/Illustrator.svg"></div>
            <div class="ticker-item"><img src="https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/VSCode-Light.svg"></div>
            <div class="ticker-item"><img src="https://cdn.simpleicons.org/autodesk/5B251A"></div>
            <div class="ticker-item"><img src="https://cdn.simpleicons.org/sketchup/5B251A"></div>
        </div>
    </div>
</section>

<section id="contactSection">
    <div class="contact-visual-text">
        <h1>
            <span>Want to</span>
            <span>start</span>
            <span class="italic-font">a new.</span>
            <span>project?</span>
        </h1>
        <span class="sub-hello">Or just say hello.</span>
    </div>

    <div class="contact-container">
        <form id="proposalForm" action="https://formspree.io/f/studioirathi@gmail.com" method="POST">
            <div class="input-group">
                <label>Full Name</label>
                <input type="text" name="name" placeholder="Enter your full name" required>
            </div>

            <div class="input-group">
                <label>Scope of Service</label>
                <div class="chip-container" id="serviceChips">
                    <div class="chip" data-value="architecture">Architecture</div>
                    <div class="chip" data-value="interior">Interior</div>
                    <div class="chip" data-value="web design">Web Design</div>
                    <div class="chip" data-value="app design">App Design</div>
                    <div class="chip" data-value="illustration">Illustration</div>
                </div>
                <input type="hidden" name="service_scope" id="selectedService">
            </div>

            <div class="input-group">
                <label>Email</label>
                <input type="email" name="email" placeholder="Enter your email" required>
            </div>

            <div class="input-group">
                <label>Your Message</label>
                <textarea name="message" placeholder="Enter your message" rows="2" required></textarea>
            </div>
            
            <button type="submit" class="btn-submit" id="submitBtn">Request a Proposal</button>
        </form>
    </div>
</section>

<script>
const mainImg = document.getElementById("mainImg");
const hero = document.getElementById("heroSection");
const about = document.getElementById("aboutSection");
const services = document.getElementById("servicesSection");
const blog = document.getElementById("blogSection");
const contact = document.getElementById("contactSection");
const navLinks = document.querySelectorAll(".nav-links a");
const tickerWrap = document.getElementById("masterTicker");
const progress = document.getElementById("scrollProgress");
const slider = document.getElementById('dragSlider');

const txtArch = document.getElementById("txtArch");
const txtUI = document.getElementById("txtUI");

function playIntro() {
    let tl = gsap.timeline();
    gsap.set("#contentSides", { opacity: 0 });
    gsap.set("#pill", { width: 190, height: 320, borderRadius: 200, opacity: 1 });
    gsap.set(".letter", { opacity: 1, x: 0, rotation: 0 });
    mainImg.src = "C:\\Users\\Deepp\\Downloads\\Index.html\\cover 2.jpeg"; 
    
    txtArch.style.color = "var(--custom-dark)";
    txtUI.style.color = "var(--custom-dark)";
    txtUI.style.background = "none";
    txtUI.style.webkitTextFillColor = "initial";

    tl.from("#topNav", { y: -100, opacity: 0, duration: 1 })
      .to("#letterD", { rotation: 90, duration: 1 })
      .to(".kolker", { x: 60, duration: 1 }, "<")
      .to(".letter", { opacity: 0, duration: 1 })
      .set("#mainImg", { attr: { src: "C:\\Users\\Deepp\\Downloads\\Index.html\\Untitled-1.png" } }, "-=0.2")
      .to("#pill", { width: 450, height: 450, borderRadius: 120, duration: 1.5, ease: "power4.inOut" }, "-=0.8")
      .to("#contentSides", { opacity: 1, pointerEvents: "auto", duration: 1 });
}
playIntro();

function hideAll() {
    hero.style.display = "none"; 
    about.style.display = "none"; 
    services.style.display = "none";
    blog.style.display = "none";
    contact.style.display = "none";
    document.body.classList.remove("dark-mode");
    navLinks.forEach(l => l.classList.remove("selected-nav"));
    document.getElementById("navConnect").style.background = "var(--custom-dark)";
    tickerWrap.style.animationPlayState = "paused";
}

// Multiselect Chip Selection Logic
const chips = document.querySelectorAll('.chip');
const serviceInput = document.getElementById('selectedService');

chips.forEach(chip => {
    chip.addEventListener('click', () => {
        chip.classList.toggle('active');
        const selectedValues = Array.from(document.querySelectorAll('.chip.active'))
            .map(c => c.getAttribute('data-value'));
        serviceInput.value = selectedValues.join(', ');
    });
});

// FORM SUBMISSION LOGIC
const proposalForm = document.getElementById('proposalForm');
const submitBtn = document.getElementById('submitBtn');

proposalForm.addEventListener('submit', async function(e) {
    e.preventDefault();
    const originalText = submitBtn.innerText;
    submitBtn.innerText = "Sending...";
    submitBtn.disabled = true;

    const formData = new FormData(proposalForm);

    try {
        const response = await fetch(proposalForm.action, {
            method: 'POST',
            body: formData,
            headers: { 'Accept': 'application/json' }
        });

        if (response.ok) {
            submitBtn.innerText = "Your message has been sent";
            submitBtn.classList.add('success');
            proposalForm.reset();
            document.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));
            
            // Reset button after 5 seconds
            setTimeout(() => {
                submitBtn.innerText = "Request a Proposal";
                submitBtn.classList.remove('success');
                submitBtn.disabled = false;
            }, 5000);
        } else {
            alert("Something went wrong. Please try again.");
            submitBtn.innerText = "Request a Proposal";
            submitBtn.disabled = false;
        }
    } catch (error) {
        alert("Error connecting to server.");
        submitBtn.innerText = "Request a Proposal";
        submitBtn.disabled = false;
    }
});

document.getElementById("navConnect").addEventListener("click", function() {
    hideAll();
    this.classList.add("selected-nav");
    this.style.background = "#5B251A";
    contact.style.display = "flex";
    gsap.from("#contactSection .contact-visual-text h1 span", { opacity: 0, x: -30, stagger: 0.1, duration: 0.8, ease: "power2.out" });
    gsap.from(".contact-container", { opacity: 0, y: 30, duration: 0.8, ease: "power2.out", delay: 0.3 });
});

document.getElementById("navBlog").addEventListener("click", function() {
    hideAll();
    this.classList.add("selected-nav");
    blog.style.display = "flex";
});

document.getElementById("navAbout").addEventListener("click", function() {
    hideAll(); 
    this.classList.add("selected-nav"); 
    about.style.display = "flex";
    tickerWrap.style.animationPlayState = "running";
    gsap.fromTo("#hiBadge", { scale: 0, rotation: -40 }, { scale: 1, rotation: 0, duration: 0.8, ease: "back.out(1.7)", delay: 0.2 });
});

document.getElementById("navServices").addEventListener("click", function() {
    hideAll(); 
    this.classList.add("selected-nav"); 
    services.style.display = "flex";
});

document.getElementById("homeLogo").addEventListener("click", () => {
    hideAll(); 
    hero.style.display = "flex"; 
    playIntro();
});

document.getElementById("btnArch").addEventListener("click", () => {
    document.body.classList.remove("dark-mode");
    mainImg.src = "C:\\Users\\Deepp\\Downloads\\Index.html\\architect.png";
    txtArch.style.color = "var(--primary-brown)";
    txtUI.style.color = "var(--custom-dark)";
    txtUI.style.background = "none";
    txtUI.style.webkitTextFillColor = "initial";    
});

document.getElementById("btnUI").addEventListener("click", () => {
    document.body.classList.add("dark-mode");
    mainImg.src = "C:\\Users\\Deepp\\Downloads\\Index.html\\UI UX.png";
    txtArch.style.color = "white";
    txtUI.style.background = "radial-gradient(circle, #77D8E1 0%, #FFFFFF 100%)";
    txtUI.style.webkitBackgroundClip = "text";
    txtUI.style.webkitTextFillColor = "transparent";
});

let isDown = false, startX, scrollLeft;
slider.addEventListener('mousedown', (e) => { isDown = true; startX = e.pageX - slider.offsetLeft; scrollLeft = slider.scrollLeft; });
slider.addEventListener('mouseleave', () => isDown = false);
slider.addEventListener('mouseup', () => isDown = false);
slider.addEventListener('mousemove', (e) => { if(!isDown) return; e.preventDefault(); const x = e.pageX - slider.offsetLeft; const walk = (x - startX) * 2; slider.scrollLeft = scrollLeft - walk; });
slider.addEventListener('scroll', () => {
    const maxScroll = slider.scrollWidth - slider.clientWidth;
    const percentage = (slider.scrollLeft / maxScroll) * 120; 
    progress.style.transform = `translateX(${percentage}px)`;
});
</script>
</body>
</html>
