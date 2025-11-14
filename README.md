# Write an enhanced animated/glitch README directly without pandoc
content = """<!-- 🎉 ULTRA ANIMATED GLITCH README – OPENING SOON 🎉 -->

<div align="center">

<!-- Title -->
<h1 style="font-size:70px; margin-bottom:10px; animation: glow 2s infinite;">
🚫 ACCOUNT TEMPORARILY SHUT DOWN 🚫
</h1>

<p style="font-size:24px;">⚡ We’ll be back online shortly — Reboot in progress... ⚡</p>

<br><br>

<!-- Sliding Animation -->
<div style="
  font-size:55px;
  font-weight:bold;
  overflow:hidden;
  white-space:nowrap;
  width:100%;
  max-width:700px;
  border-right:5px solid #00ffee;
  animation: typing 4s steps(40, end) infinite alternate,
             blink 0.5s step-end infinite;
">
💥 OPENING SOON... PLEASE WAIT 💥
</div>

<br><br>

<!-- RGB Wave Glitch -->
<div style="font-size:42px; font-weight:bold; animation: rgbWave 3s infinite;">
🌈 SYSTEM RESTART IN PROGRESS 🌈
</div>

<br><br>

<!-- Matrix Rain -->
<pre style="
  background:black;
  color:#00ff00;
  padding:20px;
  width:80%;
  font-size:18px;
  border-radius:15px;
  animation: matrix 5s linear infinite;
">
01001101 01100001 01110100 01110010 01101001 01111000
10101010 11001100 00110011 01010101 11110000 00001111
00101010 11110000 10101010 01010101 11001100 11111111
</pre>

<br>

<!-- Cyberpunk Warning -->
<h2 style="font-size:35px; animation: neon 2s ease-in-out infinite;">
⚠️ CYBER-PROTOCOL ACTIVATED — STANDBY ⚠️
</h2>

</div>

<!-- ANIMATIONS -->
<style>
@keyframes typing {
  from { width: 0; }
  to { width: 100%; }
}
@keyframes blink {
  50% { border-color: transparent; }
}
@keyframes rgbWave {
  0% { color: red; text-shadow: 0 0 10px red; }
  33% { color: lime; text-shadow: 0 0 10px lime; }
  66% { color: cyan; text-shadow: 0 0 10px cyan; }
  100% { color: red; text-shadow: 0 0 10px red; }
}
@keyframes glow {
  0% { text-shadow: 0 0 20px #ff0099; color:#ff0099; }
  50% { text-shadow: 0 0 30px #00eaff; color:#00eaff; }
  100% { text-shadow: 0 0 20px #ff0099; color:#ff0099; }
}
@keyframes neon {
  0% { text-shadow: 0 0 15px #ff00ff; }
  50% { text-shadow: 0 0 30px #00ffff; }
  100% { text-shadow: 0 0 15px #ff00ff; }
}
@keyframes matrix {
  0% { opacity: 0.2; }
  50% { opacity: 1; }
  100% { opacity: 0.2; }
}
</style>
"""

output_path = "/mnt/data/GLITCH_OPENING_SOON_README.md"
with open(output_path, "w", encoding="utf-8") as f:
    f.write(content)

output_path
