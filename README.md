website/
│── index.html        (Home)
│── about.html        (About)
│── contact.html      (Contact)
│── style.css         (Styling & responsive layout)
│── script.js         (Form validation + slider interactivity)
│── images/           (place images like slide1.jpg, slide2.jpg, etc.)


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Home | My Website</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <nav class="navbar">
      <a href="index.html" class="logo">MySite</a>
      <ul class="nav-links">
        <li><a href="index.html" class="active">Home</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="contact.html">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section class="hero">
      <h1>Welcome to My Website</h1>
      <p>Built with HTML5, CSS3, and JavaScript</p>
    </section>

    <section class="slider-section">
      <h2>Image Slider</h2>
      <div class="slider">
        <img src="images/slide1.jpg" alt="Slide 1" class="slide active" />
        <img src="images/slide2.jpg" alt="Slide 2" class="slide" />
        <img src="images/slide3.jpg" alt="Slide 3" class="slide" />
      </div>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 MySite. All rights reserved.</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>About | My Website</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <nav class="navbar">
      <a href="index.html" class="logo">MySite</a>
      <ul class="nav-links">
        <li><a href="index.html">Home</a></li>
        <li><a href="about.html" class="active">About</a></li>
        <li><a href="contact.html">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section class="content">
      <h1>About Us</h1>
      <p>This is a demo responsive website created using semantic HTML5, styled with CSS3, and powered by JavaScript interactivity.</p>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 MySite. All rights reserved.</p>
  </footer>
</body>
</html>


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Contact | My Website</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <nav class="navbar">
      <a href="index.html" class="logo">MySite</a>
      <ul class="nav-links">
        <li><a href="index.html">Home</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="contact.html" class="active">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section class="content">
      <h1>Contact Us</h1>
      <form id="contactForm">
        <label for="name">Name</label>
        <input type="text" id="name" placeholder="Enter your name" />

        <label for="email">Email</label>
        <input type="text" id="email" placeholder="Enter your email" />

        <label for="message">Message</label>
        <textarea id="message" placeholder="Write your message"></textarea>

        <button type="submit">Send</button>
        <p id="formMessage"></p>
      </form>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 MySite. All rights reserved.</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>


/* Reset */
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: Arial, sans-serif; background: #f8f9fa; color: #333; }

/* Navbar */
.navbar { display: flex; justify-content: space-between; align-items: center; padding: 1rem; background: #333; }
.logo { color: white; font-weight: bold; font-size: 1.2rem; }
.nav-links { list-style: none; display: flex; gap: 1rem; }
.nav-links a { color: white; padding: 0.5rem; }
.nav-links a.active, .nav-links a:hover { background: #555; border-radius: 4px; }

/* Hero */
.hero { text-align: center; padding: 3rem 1rem; background: #007bff; color: white; }

/* Slider */
.slider { max-width: 600px; margin: 2rem auto; position: relative; }
.slide { display: none; width: 100%; border-radius: 8px; }
.slide.active { display: block; }

/* Content & Forms */
.content { padding: 2rem; max-width: 800px; margin: auto; }
form { display: flex; flex-direction: column; gap: 1rem; }
input, textarea { padding: 0.75rem; border: 1px solid #ccc; border-radius: 6px; }
button { padding: 0.75rem; background: #007bff; color: white; border: none; border-radius: 6px; cursor: pointer; }
button:hover { background: #0056b3; }
#formMessage { font-weight: bold; }

/* Footer */
footer { text-align: center; padding: 1rem; background: #333; color: white; margin-top: 20px; }

/* Responsive */
@media (max-width: 768px) {
  .nav-links { flex-direction: column; gap: 0.5rem; }
  .hero h1 { font-size: 1.8rem; }
}


// ==========================
// Image Slider (Home Page)
// ==========================
let currentSlide = 0;
const slides = document.querySelectorAll(".slide");

function showSlide(index) {
  slides.forEach((slide, i) => {
    slide.classList.toggle("active", i === index);
  });
}

function nextSlide() {
  currentSlide = (currentSlide + 1) % slides.length;
  showSlide(currentSlide);
}

// Auto-slide every 3s
if (slides.length > 0) {
  setInterval(nextSlide, 3000);
  showSlide(currentSlide);
}

// ==========================
// Contact Form Validation
// ==========================
const form = document.getElementById("contactForm");
if (form) {
  form.addEventListener("submit", function (e) {
    e.preventDefault();
    const name = document.getElementById("name").value.trim();
    const email = document.getElementById("email").value.trim();
    const message = document.getElementById("message").value.trim();
    const msgEl = document.getElementById("formMessage");

    if (name.length < 2) {
      msgEl.textContent = "Sosha Softness.";
      msgEl.style.color = "red";
    } else if (!/^[^@]+@[^@]+\.[^@]+$/.test(email)) {
      msgEl.textContent = "SoshaSoftnesd@gmail.com.";
      msgEl.style.color = "red";
    } else if (message.length < 10) {
      msgEl.textContent = "The best paper from Kasi.";
      msgEl.style.color = "red";
    } else {
      msgEl.textContent = "✅ Thank you, " + name + "! Your message has been sent.";
      msgEl.style.color = "green";
      form.reset();
    }
  });
}


