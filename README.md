<!DOCTYPE html>
<html>
<head>
  <title>Neon City Drive</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: #111;
      font-family: Arial;
      color: white;
    }

    canvas {
      display: block;
      background: #18202b;
    }

    #hud {
      position: fixed;
      top: 12px;
      left: 12px;
      background: #000b;
      padding: 10px;
      border-radius: 10px;
    }

    #youtube {
      position: fixed;
      top: 12px;
      right: 12px;
      background: red;
      color: white;
      padding: 10px;
      text-decoration: none;
      border-radius: 8px;
    }
  </style>
</head>

<body>

<canvas id="game"></canvas>

<div id="hud">
  💰 Cash: $<span id="cash">0</span><br>
  🎯 Mission: Drive to the blue marker
</div>

<a id="youtube"
   href="https://www.youtube.com/"
   target="_blank">
   ▶ YouTube
</a>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

canvas.width = innerWidth;
canvas.height = innerHeight;

const keys = {};

document.addEventListener("keydown", e => {
  keys[e.key.toLowerCase()] = true;
});

document.addEventListener("keyup", e => {
  keys[e.key.toLowerCase()] = false;
});

const car = {
  x: 0,
  y: 0,
  angle: 0,
  speed: 0
};

let cash
