---
layout: base
title: Vasanth Rajasekaran
description: AP Computer Science Principles Class of 2025
author: Vasanth Rajasekaran
image: /images/mario_animation.png
hide: true
---

<!-- Liquid:  statements -->
{% assign sprite_file = site.baseurl | append: page.image %}
{% assign hash = site.data.mario_metadata %}
{% assign pixels = 256 %}

<!-- Page Content -->
<div class="container">
  <h1>Welcome to Vasanth Rajasekaran's Page</h1>
  <p>AP Computer Science Principles, Class of 2025</p>

  <!-- Mario Sprite -->
  <div class="sprite-container">
    <p id="mario" class="sprite"></p>
  </div>

  <!-- Riddle Section -->
  <div class="riddle-container">
    <p id="riddle" class="riddle-text"></p>
    <button id="nextRiddle" class="riddle-button">Next Riddle</button>
  </div>
</div>

<!-- Styles -->
<style>
  /* General page styles */
  body {
    font-family: 'Roboto', sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f0f4f8;
    color: #333;
  }

  h1 {
    text-align: center;
    color: #4A90E2;
    font-size: 2.5rem;
    margin-top: 20px;
  }

  p {
    text-align: center;
    font-size: 1.2rem;
  }

  .container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 20px;
  }

  /* Sprite container styles */
  .sprite-container {
    text-align: center;
    margin: 20px 0;
  }

  .sprite {
    height: {{pixels}}px;
    width: {{pixels}}px;
    background-image: url('{{sprite_file}}');
    background-repeat: no-repeat;
    display: inline-block;
  }

  #mario {
    background-position: calc({{animations[0].col}} * {{pixels}} * -1px) calc({{animations[0].row}} * {{pixels}} * -1px);
  }

  /* Riddle section styles */
  .riddle-container {
    margin-top: 40px;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    text-align: center;
  }

  .riddle-text {
    font-size: 1.3rem;
    color: #555;
    margin-bottom: 20px;
  }

  .riddle-button {
    padding: 10px 20px;
    background-color: #4A90E2;
    border: none;
    border-radius: 5px;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .riddle-button:hover {
    background-color: #357ABD;
  }

  /* Responsive design for mobile */
  @media (max-width: 768px) {
    h1 {
      font-size: 2rem;
    }

    .riddle-container {
      padding: 15px;
    }

    .riddle-button {
      width: 100%;
    }
  }
</style>

<!-- JavaScript -->
<script>
  var mario_metadata = {};
  {% for key in hash %}
  var key = "{{key | first}}";
  var values = {};
  values["row"] = {{key.row}};
  values["col"] = {{key.col}};
  values["frames"] = {{key.frames}};
  mario_metadata[key] = values;
  {% endfor %}

  class Mario {
    constructor(meta_data) {
      this.tID = null;
      this.positionX = 0;
      this.currentSpeed = 0;
      this.marioElement = document.getElementById("mario");
      this.pixels = {{pixels}};
      this.interval = 100;
      this.obj = meta_data;
      this.marioElement.style.position = "absolute";
    }

    animate(obj, speed) {
      let frame = 0;
      const row = obj.row * this.pixels;
      this.currentSpeed = speed;

      this.tID = setInterval(() => {
        const col = (frame + obj.col) * this.pixels;
        this.marioElement.style.backgroundPosition = `-${col}px -${row}px`;
        this.marioElement.style.left = `${this.positionX}px`;

        this.positionX += speed;
        frame = (frame + 1) % obj.frames;

        const viewportWidth = window.innerWidth;
        if (this.positionX > viewportWidth - this.pixels) {
          document.documentElement.scrollLeft = this.positionX - viewportWidth + this.pixels;
        }
      }, this.interval);
    }

    startWalking() {
      this.stopAnimate();
      this.animate(this.obj["Walk"], 3);
    }

    startRunning() {
      this.stopAnimate();
      this.animate(this.obj["Run1"], 6);
    }

    stopAnimate() {
      clearInterval(this.tID);
    }
  }

  const mario = new Mario(mario_metadata);

  window.addEventListener("keydown", (event) => {
    if (event.key === "ArrowRight") {
      event.preventDefault();
      if (event.repeat) {
        mario.startRunning();
      } else if (mario.currentSpeed === 0) {
        mario.startWalking();
      }
    }
  });



  

  // Riddle Section JavaScript
  const riddles = [
    { question: "I’m tall when I’m young, and I’m short when I’m old. What am I?", answer: "A candle" },
    { question: "What has many keys but can’t open a single lock?", answer: "A piano" },
    // More riddles here...
  ];

  function getRandomRiddle() {
    const randomIndex = Math.floor(Math.random() * riddles.length);
    return riddles[randomIndex];
  }

  function displayRiddle() {
    const riddle = getRandomRiddle();
    const riddleElement = document.getElementById('riddle');
    riddleElement.innerHTML = `<strong>Riddle:</strong> ${riddle.question}<br><strong>Answer:</strong> ${riddle.answer}`;
  }

  document.getElementById('nextRiddle').addEventListener('click', displayRiddle);
  window.addEventListener('DOMContentLoaded', displayRiddle);
</script>


# Games

| Games   | Description                       |
|-----------|-----------------------------------|
| [**Calculator**]({{site.baseurl}}//calculator/)     | Try using my calculator. |
| [**Snake Game**](https://www.wikipedia.org) | Online encyclopedia for information.    |
| [**GitHub**](https://www.github.com)     | Platform for hosting and sharing code.  |




# Game Code

| Games   | Description                       |
|-----------|-----------------------------------|
| [**Calculator**]({{site.baseurl}}//calculator-blog)     | Learn how I made the Snake game. |
| [**Wikipedia**](https://www.wikipedia.org) | Online encyclopedia for information.    |
| [**GitHub**](https://www.github.com)     | Platform for hosting and sharing code.  |
