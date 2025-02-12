---
layout: post
title:  
search_exclude: true
hide: true
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Popup Login Alert</title>
    <style>
        /* Overlay background */
        .popup-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 999;
            display: none; /* Initially hidden */
        }
        /* Popup container */
        .popup-container {
            background: white;
            padding: 20px;
            width: 320px;
            text-align: center;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
            position: relative;
        }
        /* Close (X) button */
        .close-btn {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 20px;
            font-weight: bold;
            color: black;
            cursor: pointer;
        }
        .close-btn:hover {
            color: red;
        }
        /* Popup heading and text */
        .popup-container h2 {
            margin-bottom: 10px;
            font-size: 18px;
            color: black; /* Text color set to black */
        }
        /* Login button */
        .popup-button {
            background: #008080;
            color: white;
            border: none;
            padding: 10px 15px;
            font-size: 14px;
            cursor: pointer;
            border-radius: 5px;
            text-decoration: none;
            display: inline-block;
            margin-top: 10px;
        }
        .popup-button:hover {
            background: #005f5f;
        }
    </style>
</head>
<body>
    <!-- Popup Alert -->
    <div class="popup-overlay" id="popup">
        <div class="popup-container">
            <span class="close-btn" onclick="closePopup()">✖</span>
            <h2>Please Login/Sign-up to access all website features</h2>
            <a href="login.html" class="popup-button">Go to Login Page</a>
        </div>
    </div>
    <script>
        document.addEventListener("DOMContentLoaded", function() {
            // Check authentication status from localStorage
            const isAuthenticated = localStorage.getItem('authenticated') === 'true';
            if (!isAuthenticated) {
                // Show the popup if user is NOT logged in
                document.getElementById("popup").style.display = "flex";
            }
            // Function to close the popup
            function closePopup() {
                document.getElementById("popup").style.display = "none";
            }
            // Close popup when clicking the (X) button
            document.querySelector(".close-btn").addEventListener("click", closePopup);
            // Hide popup when clicking outside the box
            document.getElementById("popup").addEventListener("click", function(event) {
                if (event.target === this) {
                    closePopup();
                }
            });
        });
    </script>
</body>

</html>



<style>
    
.sidebar {
    width: 260px; /* Wider for better visibility */
    height: 75vh; /* Taller but not full height */
    background: linear-gradient(135deg,rgb(134, 8, 8),rgb(48, 10, 10)); /* Dark red gradient */
    padding: 15px;
    position: fixed;
    left: 10px;
    top: 12vh; /* Adjusted for better vertical centering */
    color: white;
    font-family: 'Poppins', sans-serif; /* Modern font */
    border-radius: 12px; /* Softer edges */
    box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.3); /* Subtle shadow */
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 3px dotted white;
}

/* Sidebar title */
.sidebar h3 {
    font-size: 20px;
    margin-bottom: 15px;
    font-weight: 600;
    letter-spacing: 1px;
    text-align: center;
}
.sidebar h3::after {
    content: "";
    display: block;
    width: 100%;
    height: 2px;
    background: rgba(255, 255, 255, 0.5); /* Light separator line */
    margin: 10px auto;
    border-radius: 2px;
}

/* Sidebar links */
.sidebar a {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    color: white !important;
    text-decoration: none;
    padding: 12px 18px;
    margin: 8px 0;
    border-radius: 8px;
    font-size: 16px;
    font-weight: 500;
    transition: all 0.3s ease-in-out;
    width: 100%;
}

/* Hover effect with glowing border */
.sidebar a:hover {
    background: rgba(255, 255, 255, 0.2);
    box-shadow: 0 0 10px rgba(255, 255, 255, 0.4);
    transform: scale(1.05); /* Slight pop effect */
}

/* Sidebar icons */
.sidebar a::before {
    content: ""; /* Default arrow icon */
    margin-right: 10px;
    transition: transform 0.3s ease;
}

/* Rotate icon on hover */
.sidebar a:hover::before {
    transform: translateX(5px);
}

</style>

<div class="sidebar">
  <h3>❄️ MENU ❄️</h3>
  <a href="{{site.baseurl}}">🏠 Home Page</a>
  <a href="{{ site.baseurl }}/holiday/searchbar/"> 🔍Search Bar</a>
  <a href="{{ site.baseurl }}/holiday/chatbot/">🤖 ChatBot</a>
  <a href="{{ site.baseurl }}/holiday/event_calendar/">📅 Event Calendar</a>
  <a href="{{ site.baseurl }}/holiday/notif/">🔔 Notification</a>
  <a href="{{ site.baseurl }}/holiday/survey/">📰 Survey</a>
  <a href="{{ site.baseurl }}/post/">📧 Post</a>
  <a href="{{ site.baseurl }}/holiday/about/">📖 About Our Team</a>
</div>


<div class="holiday-page">
    <header class="holiday-header">
        <h1>🎁 Happy Holidays Gift List 🎄</h1>
    </header>
    <div class="categories-grid">
        <div class="category-box" id="home-decor">
            <h2>Home Decor</h2>
            <button onclick="location.href='{{ site.baseurl }}/holiday/home-decor/'">Explore Home Decor</button>
        </div>
        <div class="category-box" id="food">
            <h2>Food</h2>
            <button onclick="location.href='{{ site.baseurl }}/holiday/food/'">Explore Food</button>
        </div>
        <div class="category-box" id="clothes">
            <h2>Clothes</h2>
            <button onclick="location.href='{{ site.baseurl }}/holiday/clothes/'">Explore Clothes</button>
        </div>
        <div class="category-box" id="scented">
            <h2>Scented Gifts</h2>
            <button onclick="location.href='{{ site.baseurl }}/holiday/scented/'">Explore Scented Gifts</button>
        </div>
        <div class="category-box" id="electronics">
            <h2>Electronics</h2>
            <button onclick="location.href='{{ site.baseurl }}/holiday/electronics/'">Explore Electronics</button>
        </div>
        <div class="category-box" id="toys">
            <h2>Toys</h2>
            <button onclick="location.href='{{ site.baseurl }}/holiday/toys/'">Explore Toys</button>
        </div>
    </div>
</div>

<style>
/* Reset margin and padding for the whole page */
html, body {
    margin: 0;
    padding: 0;
    width: 100%;
}

/* Apply the background image to the container */
.holiday-page {
    background-image: url('{{ site.baseurl }}/images/greenbackground.png');
    background-size: cover; /* Keeps the image covering the container */
    background-position: center;
    background-attachment: fixed; /* Keeps background fixed on scroll */
    min-height: 80vh;/*100vh */
    width: 68vw; /* Reduces the width of the container to 80% of the viewport 68vh */
    margin: 0 auto; /* Centers the container */
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #ffffff;
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
    position: relative; /* Ensures it's a stacking context */
}

/* Header Styles */
.holiday-header h1 {
    font-size: 2.5em;
    margin-bottom: 30px;
    text-align: center;
    background: rgba(0, 0, 0, 0.6);
    padding: 10px 20px;
    border-radius: 10px;
}

/* Grid Layout */
.categories-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    width: 90%;
    max-width: 1200px;
}

/* Category Box Styles */
.category-box {
    background: rgba(0, 0, 0, 0.6);
    border: 2px solid rgba(255, 255, 255, 0.8);
    border-radius: 10px;
    text-align: center;
    padding: 20px;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    z-index: 2; /* Ensures boxes appear above the background */
}

.category-box h2 {
    margin-bottom: 15px;
    font-size: 1.5em;
}

.category-box button {
    background: #ffffff;
    color: #008080;
    border: none;
    padding: 10px 15px;
    font-size: 1em;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.2s ease, color 0.2s ease;
}

.category-box button:hover {
    background: #008080;
    color: #ffffff;
}

/* Hover Effect */
.category-box:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
}

/* Responsive Design */
@media (max-width: 768px) {
    .categories-grid {
        grid-template-columns: repeat(2, 1fr);
    }
    .holiday-header h1 {
        font-size: 2em;
    }
}

@media (max-width: 480px) {
    .categories-grid {
        grid-template-columns: 1fr;
    }
    .category-box h2 {
        font-size: 1.2em;
    }
}

/* Snowflake Styling */
.snowflake {
    position: absolute;
    color: white;
    font-size: 1em;
    user-select: none;
    pointer-events: none;
    z-index: 1;
    animation: fall linear infinite;
}

@keyframes fall {
    0% {
        transform: translateY(-10px);
    }
    100% {
        transform: translateY(100vh);
    }
}

/* Animation for snowflakes */
.snowflake:nth-child(odd) {
    animation-duration: 10s;
}

.snowflake:nth-child(even) {
    animation-duration: 15s;
}

/* Adjusting the snowflakes' size and timing */
.snowflake:nth-child(1) {
    font-size: 1.5em;
    animation-duration: 10s;
}

.snowflake:nth-child(2) {
    font-size: 1.3em;
    animation-duration: 12s;
}

.snowflake:nth-child(3) {
    font-size: 1.7em;
    animation-duration: 14s;
}
</style>

<script>
document.addEventListener("DOMContentLoaded", function() {
    // Snowflakes creation
    for (let i = 0; i < 100; i++) {
        let snowflake = document.createElement("div");
        snowflake.classList.add("snowflake");
        snowflake.style.left = `${Math.random() * 100}%`;
        snowflake.style.animationDuration = `${Math.random() * 10 + 5}s`; // random fall time
        snowflake.style.animationDelay = `${Math.random() * 5}s`; // random start time
        snowflake.innerHTML = "❆";
        document.querySelector(".holiday-page").appendChild(snowflake);
    }
});
</script>

