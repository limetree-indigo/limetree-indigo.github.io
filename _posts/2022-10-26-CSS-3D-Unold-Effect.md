---
layout: post
title: CSS 3D Image Hover Effects - Unfold Effect
categories: CSS
tags: ['HTML', 'CSS']
---

<style>
  #fold-effect-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: #2f364f;
  }
  #fold-effect-wrapper>.box{
    position: relative;
    top: 50px;
    width: 640px;
    height: 360px;
    transform: rotate(-25deg) skew(25deg);
    transition: 0.5s;
    display: flex;
  }
  #fold-effect-wrapper>.box:hover {
    transform: rotate(-25deg) skew(-25deg) translateY(-20px);
  }
  #fold-effect-wrapper>.box span {
    width: 25%;
    height: 100%;
    background: url(/assets/images/unfold-image.jpg);
    background-size: cover;
    background-position: calc(-160px * var(--i));
    display: block;
    transition: 0.5s;
    pointer-events: none;
    border-top: 5px solid #fff;
    border-bottom: 5px solid #fff;
  }
  #fold-effect-wrapper>.box:hover span:nth-child(odd) {
    transform: skewY(25deg);
    box-shadow: inset 20px 0 50px rgba(0, 0, 0, 0.5);
  }
  #fold-effect-wrapper>.box:hover span:nth-child(even) {
    transform: skewY(-25deg);
    box-shadow: inset 20px 0 50px rgba(0, 0, 0, 0.5);

  }
  #fold-effect-wrapper>.box span:first-child {
    border-left: 5px solid #fff;
  }
  #fold-effect-wrapper>.box span:last-child {
    border-right: 5px solid #fff;
  }

  
</style>
<div id="fold-effect-wrapper">
  <div class="box">
    <span style="--i:0;"></span>
    <span style="--i:1;"></span>
    <span style="--i:2;"></span>
    <span style="--i:3;"></span>
  </div>
</div>




