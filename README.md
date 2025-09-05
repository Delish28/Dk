<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title>Student Portfolio</title>
  <link rel="stylesheet" href="style.css">
  <script defer src="script.js"></script>

  <!-- EmailJS SDK -->
  <script type="text/javascript" src="https://cdn.emailjs.com/dist/email.min.js"></script>
  <script>
    (function () {
      emailjs.init("YOUR_PUBLIC_KEY"); // replace with your EmailJS Public Key
    })();
  </script>

  <style>
    /* Basic styling for all pages */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f9f9f9;
      color: #333;
    }

    header {
      background: #333;
      color: #fff;
      padding: 1rem;
    }

    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .nav-links {
      list-style: none;
      display: flex;
      gap: 15px;
    }

    .nav-links li a {
      color: white;
      text-decoration: none;
    }

    section {
      padding: 40px 20px;
      max-width: 900px;
      margin: auto;
    }

    .hero {
      background: #555;
      color: white;
      text-align: center;
      padding: 100px 20px;
    }

    .btn {
      background: #ff6600;
      color: white;
      padding: 10px 20px;
      text-decoration: none;
      border-radius: 5px;
    }

    .about-content {
      display: flex;
      align-items: center;
      gap: 20px;
    }

    .about-content img {
      width: 150px;
      border-radius: 50%;
    }

    .project-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }

    .project-card {
      background: white;
      padding: 15px;
      border-radius: 8px;
      box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    }

    /* Quiz Styles */
    .question {
      margin-bottom: 20px;
      background: white;
      padding: 15px;
      border-radius: 8px;
    }

    /* Blog */
    .post {
      background: white;
      padding: 15px;
      margin-bottom: 20px;
      border-radius: 8px;
      box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    }

    .post h2 {
      margin: 0 0 10px;
    }

    .post small {
      color: gray;
      font-size: 12px;
    }

    /* Contact */
    form input,
    form textarea {
      width: 100%;
      margin-bottom: 10px;
      padding: 10px;
    }

    button {
      padding: 10px 20px;
      background: #333;
      color: white;
      border: none;
      cursor: pointer;
    }

    footer {
      background: #333;
      color: white;
      text-align: center;
      padding: 10px;
    }
  </style>
</head>

<body>
  <!-- Navbar -->
  <header>
    <nav class="navbar">
      <div class="logo">MyPortfolio</div>
      <ul class="nav-links" id="nav-links">
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#quiz">Quiz</a></li>
        <li><a href="#blog">Blog</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
      <div class="menu-toggle" id="menu-toggle">&#9776;</div>
    </nav>
  </header>

  <!-- Hero -->
  <section id="home" class="hero">
    <div class="hero-content">
      <h1>Hello, I'm <span>Mr Delish Kumar. V</span></h1>
      <p>I am the student </p>
      <a href="#projects" class="btn">View My Work</a>
    </div>
  </section>

  <!-- About -->
  <section id="about" class="about">
    <h2>About Me</h2>
    <div class="about-content">
      <img src="IMG_20250707_123638_595.webp" alt="Profile Photo">
      <p>I am a student enthusiastic about technology and design. I love building interactive,
        user-friendly web applications and exploring new tools in the tech world.
      </p>
    </div>
  </section>

  <!-- Projects -->
  <section id="projects" class="projects">
    <h2>My Projects</h2>
    <div class="project-grid">
      <div class="project-card">
        <h3>Project 1</h3>
        <p>A simple responsive website.</p>
      </div>
      <div class="project-card">
        <h3>Project 2</h3>
        <p>JavaScript-based quiz app.</p>
      </div>
      <div class="project-card">
        <h3>Project 3</h3>
        <p>Personal blog with CMS.</p>
      </div>
    </div>
  </section>

  <!-- Quiz -->
  <section id="quiz" class="quiz">
    <h2>General Knowledge Quiz</h2>
    <form id="quizForm">
      <div class="question">
        <h3>1. What is the capital of France?</h3>
        <label><input type="radio" name="q1" value="Paris"> Paris</label><br>
        <label><input type="radio" name="q1" value="Berlin"> Berlin</label><br>
        <label><input type="radio" name="q1" value="Madrid"> Madrid</label>
      </div>

      <div class="question">
        <h3>2. Who wrote 'Hamlet'?</h3>
        <label><input type="radio" name="q2" value="Shakespeare"> William Shakespeare</label><br>
        <label><input type="radio" name="q2" value="Dickens"> Charles Dickens</label><br>
        <label><input type="radio" name="q2" value="Hemingway"> Ernest Hemingway</label>
      </div>

      <div class="question">
        <h3>3. What is the largest planet in our solar system?</h3>
        <label><input type="radio" name="q3" value="Jupiter"> Jupiter</label><br>
        <label><input type="radio" name="q3" value="Mars"> Mars</label><br>
        <label><input type="radio" name="q3" value="Earth"> Earth</label>
      </div>

      <button type="button" onclick="submitQuiz()">Submit</button>
    </form>
    <p id="result"></p>
  </section>

  <!-- Blog -->
  <section id="blog" class="blog">
    <h2>My Blog</h2>
    <div class="container" id="postsContainer"></div>
  </section>

  <!-- Contact -->
  <section id="contact" class="contact">
    <h2>Contact Me</h2>
    <form id="contact-form">
      <input type="text" id="name" name="user_name" placeholder="Your Name" required>
      <input type="email" id="email" name="user_email" placeholder="Your Email" required>
      <textarea id="message" name="message" placeholder="Your Message" required></textarea>
      <button type="submit">Send</button>
    </form>
    <p id="form-status"></p>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 MR DELISH KUMAR| All rights reserved</p>
  </footer>

  <!-- Scripts -->
  <script>
    // Quiz logic
    function submitQuiz() {
      let score = 0;
      const answers = {
        q1: "Paris",
        q2: "Shakespeare",
        q3: "Jupiter"
      };

      for (let key in answers) {
        const selected = document.querySelector(`input[name="${key}"]:checked`);
        if (selected && selected.value === answers[key]) {
          score++;
        }
      }

      document.getElementById("result").innerText = "You scored " + score + "/3";
    }

    // Blog loader
    function loadPosts() {
      const postsContainer = document.getElementById("postsContainer");
      const posts = JSON.parse(localStorage.getItem("blogPosts")) || [];
      postsContainer.innerHTML = "";
      posts.reverse().forEach(post => {
        const postEl = document.createElement("div");
        postEl.classList.add("post");
        postEl.innerHTML = `
          <h2>${post.title}</h2>
          <small>${new Date(post.date).toLocaleString()}</small>
          <p>${post.content}</p>
        `;
        postsContainer.appendChild(postEl);
      });
    }
    loadPosts();
  </script>
</body>

</html>
