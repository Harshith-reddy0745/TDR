<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TDR Junior College | IIT·MIT Legacy</title>
    <!-- Font Awesome 6 (free) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Google Fonts: Inter + Playfair Display -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* RESET & BASE */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: #fafafa;
            color: #1e1e2f;
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Color palette – MIT red accent / deep navy */
        :root {
            --primary: #0a1929;      /* deep navy (like IIT/MIT formal) */
            --accent: #b22234;        /* MIT red / classic */
            --accent-light: #d44c4c;
            --gray-light: #f0f2f5;
            --gray: #a0a0b0;
            --white: #ffffff;
            --shadow: 0 20px 40px -10px rgba(0,0,0,0.15);
            --transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
        }

        /* TYPOGRAPHY */
        h1, h2, h3, h4 {
            font-family: 'Playfair Display', serif;
            font-weight: 600;
            letter-spacing: -0.02em;
        }

        .section-title {
            font-size: 2.8rem;
            margin-bottom: 1.5rem;
            position: relative;
            color: var(--primary);
        }
        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: var(--accent);
            margin-top: 0.5rem;
            border-radius: 2px;
        }
        .text-center .section-title::after {
            margin-left: auto;
            margin-right: auto;
        }

        /* container */
        .container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        /* Buttons */
        .btn {
            display: inline-block;
            background: var(--accent);
            color: white;
            font-weight: 600;
            padding: 0.8rem 2.5rem;
            border-radius: 40px;
            text-decoration: none;
            transition: var(--transition);
            border: none;
            cursor: pointer;
            box-shadow: 0 4px 12px rgba(180, 50, 50, 0.3);
            letter-spacing: 0.3px;
        }
        .btn:hover {
            background: #8b1a1a;
            transform: translateY(-3px);
            box-shadow: 0 12px 24px rgba(140, 30, 30, 0.3);
        }
        .btn-outline {
            background: transparent;
            border: 2px solid var(--accent);
            color: var(--accent);
            box-shadow: none;
        }
        .btn-outline:hover {
            background: var(--accent);
            color: white;
        }

        /* Navbar */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            padding: 1.2rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255,255,255,0.85);
            backdrop-filter: blur(12px);
            z-index: 1000;
            transition: var(--transition);
            box-shadow: 0 4px 20px rgba(0,0,0,0.05);
        }
        .navbar.scrolled {
            padding: 0.8rem 5%;
            background: rgba(255,255,255,0.95);
            box-shadow: 0 4px 30px rgba(0,0,0,0.1);
        }
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary);
            font-family: 'Playfair Display', serif;
        }
        .logo span {
            color: var(--accent);
            font-weight: 300;
            font-size: 1rem;
            margin-left: 0.3rem;
        }
        .nav-links {
            display: flex;
            gap: 2.5rem;
            align-items: center;
        }
        .nav-links a {
            text-decoration: none;
            color: var(--primary);
            font-weight: 500;
            font-size: 1rem;
            transition: var(--transition);
            position: relative;
        }
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -6px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: 0.3s;
        }
        .nav-links a:hover::after {
            width: 100%;
        }
        .hamburger {
            display: none;
            font-size: 2rem;
            color: var(--primary);
            cursor: pointer;
        }

        /* Hero Section with 3D canvas background */
        .hero {
            position: relative;
            height: 100vh;
            min-height: 700px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            overflow: hidden;
            background-color: var(--primary); /* fallback */
        }
        #hero-3d {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            opacity: 0.35;
            pointer-events: none;
        }
        .hero-content {
            position: relative;
            z-index: 10;
            max-width: 1000px;
            padding: 2rem;
            animation: fadeUp 1.2s ease-out;
        }
        .hero-content h1 {
            font-size: 5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            text-shadow: 0 10px 30px rgba(0,0,0,0.5);
            line-height: 1.1;
        }
        .hero-content h1 span {
            color: var(--accent);
            border-bottom: 4px solid var(--accent);
            display: inline-block;
            padding-bottom: 0.2rem;
        }
        .hero-content p {
            font-size: 1.6rem;
            font-weight: 300;
            margin-bottom: 2.5rem;
            opacity: 0.95;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }
        @keyframes fadeUp {
            0% { opacity:0; transform:translateY(30px); }
            100% { opacity:1; transform:translateY(0); }
        }

        /* Sections */
        section {
            padding: 6rem 0;
            position: relative;
            background: white;
        }
        section:nth-child(even) {
            background: var(--gray-light);
        }

        /* About */
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }
        .about-text p {
            font-size: 1.2rem;
            color: #333;
            margin-bottom: 1.5rem;
            line-height: 1.8;
        }
        .about-stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
        }
        .stat-item {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            box-shadow: var(--shadow);
            text-align: center;
            transition: var(--transition);
        }
        .stat-item:hover {
            transform: scale(1.05);
            box-shadow: 0 30px 50px -10px rgba(0,0,0,0.2);
        }
        .stat-item h3 {
            font-size: 2.5rem;
            color: var(--accent);
            margin-bottom: 0.5rem;
        }

        /* Courses */
        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }
        .course-card {
            background: white;
            padding: 2.5rem 1.5rem;
            border-radius: 24px;
            box-shadow: var(--shadow);
            text-align: center;
            transition: var(--transition);
            border: 1px solid rgba(0,0,0,0.02);
        }
        .course-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 40px 60px -10px rgba(178, 34, 52, 0.2);
            border-color: var(--accent);
        }
        .course-card i {
            font-size: 3.5rem;
            color: var(--accent);
            margin-bottom: 1rem;
        }
        .course-card h3 {
            font-size: 1.8rem;
            margin-bottom: 0.8rem;
        }

        /* Faculty */
        .faculty-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 2.5rem;
        }
        .faculty-card {
            background: white;
            border-radius: 30px;
            padding: 2rem 1.5rem;
            text-align: center;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }
        .faculty-card:hover {
            transform: scale(1.02);
            box-shadow: 0 30px 50px -10px var(--accent-light);
        }
        .faculty-card img {
            width: 140px;
            height: 140px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid var(--accent);
            margin-bottom: 1.2rem;
            background: #eee;
        }
        .faculty-card h4 {
            font-size: 1.6rem;
            color: var(--primary);
        }
        .faculty-card p {
            color: var(--accent);
            font-weight: 500;
        }

        /* Gallery */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
        }
        .gallery-item {
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            height: 240px;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }
        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s;
        }
        .gallery-item:hover img {
            transform: scale(1.1);
        }
        .gallery-item .overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(transparent, rgba(10,25,50,0.9));
            color: white;
            padding: 1rem;
            font-size: 1.2rem;
            font-weight: 500;
        }

        /* Form */
        .form-card {
            background: white;
            border-radius: 40px;
            padding: 3rem;
            box-shadow: var(--shadow);
            max-width: 800px;
            margin: 0 auto;
        }
        .form-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }
        .form-group {
            margin-bottom: 1.5rem;
        }
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--primary);
        }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 1rem 1.2rem;
            border: 1px solid #ddd;
            border-radius: 30px;
            font-size: 1rem;
            transition: var(--transition);
            background: #f9f9f9;
        }
        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 4px rgba(178,34,52,0.1);
            background: white;
        }
        .btn-block {
            width: 100%;
            padding: 1rem;
            font-size: 1.2rem;
        }

        /* Map */
        .map-container {
            height: 400px;
            border-radius: 30px;
            overflow: hidden;
            box-shadow: var(--shadow);
        }

        /* Contact */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            background: white;
            padding: 3rem;
            border-radius: 40px;
            box-shadow: var(--shadow);
        }
        .contact-item {
            text-align: center;
        }
        .contact-item i {
            font-size: 2.5rem;
            color: var(--accent);
            margin-bottom: 1rem;
        }
        .contact-item h4 {
            font-size: 1.4rem;
            margin-bottom: 0.5rem;
        }
        .contact-item a {
            color: var(--primary);
            text-decoration: none;
        }

        footer {
            background: var(--primary);
            color: white;
            text-align: center;
            padding: 2rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                flex-direction: column;
                background: white;
                position: absolute;
                top: 70px;
                right: 5%;
                width: 200px;
                padding: 1.5rem;
                border-radius: 20px;
                box-shadow: var(--shadow);
            }
            .nav-links.active {
                display: flex;
            }
            .hamburger {
                display: block;
            }
            .hero-content h1 {
                font-size: 3.5rem;
            }
            .about-grid {
                grid-template-columns: 1fr;
            }
            .form-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Navbar -->
    <nav class="navbar" id="navbar">
        <div class="logo">TDR<span>Junior College</span></div>
        <div class="hamburger" id="hamburger"><i class="fas fa-bars"></i></div>
        <div class="nav-links" id="navLinks">
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#courses">Courses</a>
            <a href="#faculty">Faculty</a>
            <a href="#gallery">Gallery</a>
            <a href="#admission">Admission</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <!-- Hero with 3D canvas -->
    <section id="home" class="hero">
        <div id="hero-3d"></div>
        <div class="hero-content">
            <h1>TDR <span>Junior College</span></h1>
            <p>Uppal · Telangana · Excellence since 2024</p>
            <a href="#admission" class="btn">Apply now <i class="fas fa-arrow-right"></i></a>
        </div>
    </section>

    <!-- About -->
    <section id="about">
        <div class="container">
            <h2 class="section-title">About the College</h2>
            <div class="about-grid">
                <div class="about-text">
                    <p>Founded in 2024 with the vision to deliver world-class junior college education, <strong>TDR Junior College</strong> has quickly established itself as a rising star in Uppal. Affiliated with the Telangana Board of Intermediate Education, we blend rigorous academics with holistic development.</p>
                    <p>Our campus features smart classrooms, fully equipped labs, and a digital library. We take pride in our dedicated faculty, many of whom are alumni of premier institutions, and our first batch achieved a remarkable <strong>100% pass percentage</strong>.</p>
                    <a href="#contact" class="btn btn-outline">Visit us</a>
                </div>
                <div class="about-stats">
                    <div class="stat-item">
                        <h3>100%</h3>
                        <p>Pass percentage</p>
                    </div>
                    <div class="stat-item">
                        <h3>2+</h3>
                        <p>Years of legacy</p>
                    </div>
                    <div class="stat-item">
                        <h3>25+</h3>
                        <p>Expert faculty</p>
                    </div>
                    <div class="stat-item">
                        <h3>2024</h3>
                        <p>Excellence since</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Courses -->
    <section id="courses">
        <div class="container">
            <h2 class="section-title">Courses offered</h2>
            <div class="cards-grid">
                <div class="course-card">
                    <i class="fas fa-flask"></i>
                    <h3>MPC</h3>
                    <p>Mathematics, Physics, Chemistry – for engineering & pure sciences.</p>
                </div>
                <div class="course-card">
                    <i class="fas fa-dna"></i>
                    <h3>BiPC</h3>
                    <p>Biology, Physics, Chemistry – for medicine & life sciences.</p>
                </div>
                <div class="course-card">
                    <i class="fas fa-chart-line"></i>
                    <h3>MEC</h3>
                    <p>Mathematics, Economics, Commerce – for economics & finance.</p>
                </div>
                <div class="course-card">
                    <i class="fas fa-gavel"></i>
                    <h3>CEC</h3>
                    <p>Civics, Economics, Commerce – for law & civil services.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Faculty -->
    <section id="faculty">
        <div class="container">
            <h2 class="section-title">Our Faculty</h2>
            <div class="faculty-grid">
                <div class="faculty-card">
                    <img src="https://images.unsplash.com/photo-1568602471122-7832951cc4c5?w=200&h=200&fit=crop&auto=format" alt="Dr. S. Reddy">
                    <h4>Dr. S. Reddy</h4>
                    <p>Mathematics</p>
                    <small>Ph.D (IIT Hyderabad)</small>
                </div>
                <div class="faculty-card">
                    <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=200&h=200&fit=crop&auto=format" alt="Mrs. V. Laxmi">
                    <h4>Mrs. V. Laxmi</h4>
                    <p>Botany</p>
                    <small>M.Sc, M.Ed (BHU)</small>
                </div>
                <div class="faculty-card">
                    <img src="https://images.unsplash.com/photo-1560250097-0b93528c311a?w=200&h=200&fit=crop&auto=format" alt="Mr. K. Rajesh">
                    <h4>Mr. K. Rajesh</h4>
                    <p>Economics</p>
                    <small>MBA (Osmania)</small>
                </div>
                <div class="faculty-card">
                    <img src="https://images.unsplash.com/photo-1580489944761-15a19d654956?w=200&h=200&fit=crop&auto=format" alt="Prof. M. Anitha">
                    <h4>Prof. M. Anitha</h4>
                    <p>Civics</p>
                    <small>M.Phil (Delhi Univ)</small>
                </div>
            </div>
            <p style="text-align: center; margin-top: 2rem; font-size: 1.2rem; color: var(--primary);">... and 20+ more experienced educators</p>
        </div>
    </section>

    <!-- Gallery -->
    <section id="gallery">
        <div class="container">
            <h2 class="section-title">Campus Gallery</h2>
            <div class="gallery-grid">
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1541339907198-e08756dedf3f?w=400&h=300&fit=crop" alt="Campus"><div class="overlay">Main building</div></div>
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1523050854058-8df90110c9f1?w=400&h=300&fit=crop" alt="Library"><div class="overlay">Library</div></div>
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1588072432836-e10032774350?w=400&h=300&fit=crop" alt="Lab"><div class="overlay">Physics lab</div></div>
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1524178232363-1fb2b075b655?w=400&h=300&fit=crop" alt="Sports"><div class="overlay">Sports ground</div></div>
            </div>
        </div>
    </section>

    <!-- Admission Form -->
    <section id="admission">
        <div class="container">
            <h2 class="section-title">Online Admission</h2>
            <div class="form-card">
                <form id="admissionForm">
                    <div class="form-grid">
                        <div class="form-group">
                            <label>Full name *</label>
                            <input type="text" id="name" required placeholder="John Doe">
                        </div>
                        <div class="form-group">
                            <label>Mobile *</label>
                            <input type="tel" id="phone" required placeholder="+91 98765 43210">
                        </div>
                        <div class="form-group">
                            <label>Email</label>
                            <input type="email" id="email" placeholder="john@example.com">
                        </div>
                        <div class="form-group">
                            <label>Course *</label>
                            <select id="course" required>
                                <option value="">-- select --</option>
                                <option value="MPC">MPC</option>
                                <option value="BiPC">BiPC</option>
                                <option value="MEC">MEC</option>
                                <option value="CEC">CEC</option>
                            </select>
                        </div>
                    </div>
                    <div class="form-group">
                        <label>Message (optional)</label>
                        <textarea id="message" rows="3" placeholder="Any queries..."></textarea>
                    </div>
                    <button type="submit" class="btn btn-block">Submit application</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Google Map -->
    <section id="location">
        <div class="container">
            <h2 class="section-title">Our Location</h2>
            <div class="map-container">
                <iframe src="https://maps.google.com/maps?q=Uppal+Medchal-Malkajgiri+Telangana+TDR+Junior+College&output=embed" allowfullscreen="" loading="lazy"></iframe>
            </div>
        </div>
    </section>

    <!-- Contact -->
    <section id="contact">
        <div class="container">
            <h2 class="section-title">Contact us</h2>
            <div class="contact-grid">
                <div class="contact-item">
                    <i class="fas fa-phone-alt"></i>
                    <h4>Phone</h4>
                    <a href="tel:+917013943315">+91 70139 43315</a>
                </div>
                <div class="contact-item">
                    <i class="fas fa-clock"></i>
                    <h4>Timings</h4>
                    <p>9:00 AM – 5:00 PM</p>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <h4>Address</h4>
                    <p>H No: 2-3-215/3&4/NR and 2-3-215/2&5/NR, Survey No:124 Part, Main Road, Uppal, Medchal-Malkajgiri District, Telangana</p>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <p>© 2025 TDR Junior College. All rights reserved. Designed with <i class="fas fa-heart" style="color:#b22234;"></i> for academic excellence.</p>
    </footer>

    <!-- Three.js for subtle 3D background in hero -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // === Three.js Subtle Professional 3D ===
        const canvasContainer = document.getElementById('hero-3d');
        if (canvasContainer) {
            const scene = new THREE.Scene();
            scene.background = new THREE.Color(0x0a1929); // match primary navy

            const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
            camera.position.set(0, 2, 18);

            const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: false });
            renderer.setSize(window.innerWidth, window.innerHeight);
            renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
            canvasContainer.appendChild(renderer.domElement);

            // Lights
            const ambientLight = new THREE.AmbientLight(0x404060);
            scene.add(ambientLight);
            const dirLight = new THREE.DirectionalLight(0xffffff, 1);
            dirLight.position.set(1, 2, 3);
            scene.add(dirLight);
            const pointLight = new THREE.PointLight(0xb22234, 1, 20);
            pointLight.position.set(2, 3, 4);
            scene.add(pointLight);

            // Central geometric shape: Icosahedron wireframe
            const geometry = new THREE.IcosahedronGeometry(2.5, 0);
            const material = new THREE.MeshStandardMaterial({
                color: 0xb22234,
                wireframe: true,
                emissive: 0x330000,
                transparent: true,
                opacity: 0.35
            });
            const core = new THREE.Mesh(geometry, material);
            scene.add(core);

            // Floating tiny particles around
            const particlesGeo = new THREE.BufferGeometry();
            const count = 400;
            const positions = new Float32Array(count * 3);
            for (let i = 0; i < count * 3; i += 3) {
                const r = 5 + Math.random() * 3;
                const theta = Math.random() * Math.PI * 2;
                const phi = Math.acos(2 * Math.random() - 1);
                positions[i] = Math.sin(phi) * Math.cos(theta) * r;
                positions[i+1] = Math.sin(phi) * Math.sin(theta) * r;
                positions[i+2] = Math.cos(phi) * r;
            }
            particlesGeo.setAttribute('position', new THREE.BufferAttribute(positions, 3));
            const particlesMat = new THREE.PointsMaterial({ color: 0xa0a0b0, size: 0.05, transparent: true });
            const particles = new THREE.Points(particlesGeo, particlesMat);
            scene.add(particles);

            // Rotating rings
            const ringGeo = new THREE.TorusGeometry(3.8, 0.08, 16, 100);
            const ringMat = new THREE.MeshStandardMaterial({ color: 0xb22234, emissive: 0x220000 });
            const ring = new THREE.Mesh(ringGeo, ringMat);
            ring.rotation.x = Math.PI / 2;
            ring.rotation.z = 0.3;
            scene.add(ring);

            const ring2 = new THREE.Mesh(new THREE.TorusGeometry(4.2, 0.06, 16, 100), new THREE.MeshStandardMaterial({ color: 0x4a6fa5, emissive: 0x112233 }));
            ring2.rotation.x = 1.2;
            ring2.rotation.y = 0.5;
            scene.add(ring2);

            // Animation
            function animate() {
                requestAnimationFrame(animate);

                core.rotation.y += 0.002;
                core.rotation.x += 0.001;
                ring.rotation.z += 0.001;
                ring.rotation.y += 0.002;
                ring2.rotation.x += 0.001;
                ring2.rotation.y += 0.003;
                particles.rotation.y += 0.0005;

                renderer.render(scene, camera);
            }
            animate();

            // resize handler
            window.addEventListener('resize', () => {
                camera.aspect = window.innerWidth / window.innerHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(window.innerWidth, window.innerHeight);
            });
        }

        // === Navbar scroll effect ===
        window.addEventListener('scroll', () => {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // === Hamburger menu ===
        const hamburger = document.getElementById('hamburger');
        const navLinks = document.getElementById('navLinks');
        hamburger.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                    navLinks.classList.remove('active');
                }
            });
        });

        // Form submission
        document.getElementById('admissionForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('name').value.trim();
            const phone = document.getElementById('phone').value.trim();
            const course = document.getElementById('course').value;
            if (!name || !phone || !course) {
                alert('Please fill all required fields.');
                return;
            }
            alert(`Thank you, ${name}. Your application for ${course} has been received. Our admissions team will contact you shortly.`);
            this.reset();
        });
    </script>
</body>
</html>
