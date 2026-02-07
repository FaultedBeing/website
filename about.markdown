---
layout: page
title: About
permalink: /about/
---

<style>
  .about-container {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    align-items: flex-start;
  }

  .about-text {
    flex: 1;
    min-width: 300px; /* Ensures text doesn't get too squished before wrapping */
  }

  .reading-list-box {
    flex: 0 0 300px; /* Fixed width for the sidebar on large screens */
    background-color: rgba(128, 128, 128, 0.1);
    padding: 20px;
    border-radius: 8px;
    border: 1px solid rgba(128, 128, 128, 0.2);
    box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  }

  /* On smaller screens, make the box full width and drop it below */
  @media (max-width: 800px) {
    .reading-list-box {
      flex: 1 1 100%;
      width: 100%;
      margin-top: 20px;
    }
  }
</style>

<div class="about-container">
  <div class="about-text">
    <p>In short: an engineer looking to work on fun, interesting, challenging things.</p>
    <p>Previously president of the Caltech Rocketry Club (PARSEC)</p>
  </div>

  <div class="reading-list-box">
    <h3 style="margin-top: 0; font-size: 1.2em;">Currently Reading</h3>
    
    <p style="margin-bottom: 5px; margin-top: 15px; font-weight: bold;">Fiction:</p>
    <ul style="margin-top: 5px; padding-left: 20px;">
      <li><a href="https://www.amazon.com/Wind-Truth-Stormlight-Archive-Book/dp/1250319188" target="_blank">Wind and Truth by Brandon Sanderson</a></li>
    </ul>

    <p style="margin-bottom: 5px; margin-top: 15px; font-weight: bold;">Non-Fiction:</p>
    <ul style="margin-top: 5px; padding-left: 20px;">
      <li><a href="https://www.amazon.com/Power-Beaming-Scientific-Technologies-Bar-Cohen/dp/9819822424/" target="_blank">Power Beaming: History, Theory, and Practice by Paul Jaffe (and three others)</a></li>
      <li><a href="https://www.amazon.com/Escaping-Gravity-Quest-Transform-Launch/dp/1635767709" target="_blank">Escaping Gravity by Lori Garver</a></li>
    </ul>
  </div>
</div>