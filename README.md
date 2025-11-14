# Create animated SVG and README that embeds it (SVG uses SMIL animations, which display on GitHub when referenced as an image file)
svg_content = r'''<?xml version="1.0" encoding="utf-8"?>
<svg xmlns="http://www.w3.org/2000/svg" width="900" height="220" viewBox="0 0 900 220" preserveAspectRatio="xMidYMid meet">
  <defs>
    <linearGradient id="g" x1="0" x2="1">
      <stop offset="0%" stop-color="#ff0066"/>
      <stop offset="50%" stop-color="#00eaff"/>
      <stop offset="100%" stop-color="#7cff00"/>
    </linearGradient>
    <style type="text/css"><![CDATA[
      .bg { fill: #0b0f14; }
      .label { font-family: 'Segoe UI', Roboto, Arial, sans-serif; font-weight:700; font-size:48px; fill: url(#g); }
      .sub { font-size:18px; fill:#cbd5e1; font-weight:500; }
      .glow { filter: url(#f1); }
    ]]></style>
    <filter id="f1" x="-50%" y="-50%" width="200%" height="200%">
      <feGaussianBlur stdDeviation="6" result="b"/>
      <feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <!-- background -->
  <rect class="bg" width="100%" height="100%" rx="12" ry="12"/>

  <!-- matrix lines (decorative) -->
  <g opacity="0.18">
    <text x="20" y="40" font-family="monospace" font-size="12" fill="#00ff66">010101 110011 101010 111000</text>
    <text x="20" y="60" font-family="monospace" font-size="12" fill="#00ff66">101100 001111 010101 100110</text>
    <text x="20" y="80" font-family="monospace" font-size="12" fill="#00ff66">111000 000111 101010 010101</text>
  </g>

  <!-- sliding "OPENING SOON..." label group -->
  <g class="glow">
    <rect x="-20" y="60" width="940" height="70" fill="transparent"/>
    <text id="mainLabel" class="label" x="-900" y="110">🔥 OPENING SOON... PLEASE WAIT 🔥</text>

    <!-- animate the x attribute to slide text in and out -->
    <animate xlink:href="#mainLabel" attributeName="x"
             values="-900;60;960" keyTimes="0;0.5;1" dur="4s" repeatCount="indefinite" />
    <!-- slight horizontal jitter to give glitch effect -->
    <animate xlink:href="#mainLabel" attributeName="x" from="60" to="62" begin="0.5s" dur="0.12s" repeatCount="indefinite" />
  </g>

  <!-- underline neon bar that pulses -->
  <rect x="60" y="120" width="0" height="6" rx="3" fill="url(#g)">
    <animate attributeName="width" values="0;780;0" dur="4s" repeatCount="indefinite" />
    <animate attributeName="opacity" values="0.2;1;0.2" dur="4s" repeatCount="indefinite" />
  </rect>

  <!-- sub text -->
  <text class="sub" x="60" y="160">⚠️ Account temporarily closed — we’re preparing something awesome. Reopening shortly.</text>

  <!-- pulsing RGB circles -->
  <g transform="translate(820,40)">
    <circle r="10" fill="#ff0066" opacity="0.9">
      <animate attributeName="r" values="6;12;6" dur="1.6s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.6;1;0.6" dur="1.6s" repeatCount="indefinite"/>
    </circle>
    <circle r="10" fill="#00eaff" cx="-26" opacity="0.8">
      <animate attributeName="r" values="6;12;6" dur="1.9s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.6;1;0.6" dur="1.9s" repeatCount="indefinite"/>
    </circle>
    <circle r="10" fill="#7cff00" cx="-52" opacity="0.7">
      <animate attributeName="r" values="6;12;6" dur="2.2s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.6;1;0.6" dur="2.2s" repeatCount="indefinite"/>
    </circle>
  </g>

</svg>
'''

readme_content = """# 🚫 Account Temporarily Closed — Opening Soon

This repository is currently paused. We're working on improvements and will be back shortly.

<!-- Embed the animated SVG below. On GitHub, this displays as an animated image when the SVG file is added to the repo root. -->
![Opening Soon](opening_soon.svg)

---

**Why the previous README didn't animate on GitHub**

- GitHub strips or sanitizes many inline HTML and `<style>` tags inside README.md for security — so CSS animations placed directly inside README often won't run.
- Solutions that do work on GitHub:
  1. **Embed an animated SVG file** (like this repo provides) and reference it from README as an image — GitHub shows animated SVGs when they are image files in the repo.
  2. **Use an animated GIF/APNG** and embed it in README (works reliably everywhere).
  3. **Host a full HTML page with GitHub Pages** for full control (best for complex interactive animations).

**What I created for you right now**

- `opening_soon.svg` — animated SVG with sliding "OPENING SOON..." text and RGB effects.
- `README.md` — embeds that SVG so GitHub renders the animation when both files are in your repository root.

---

**How to use**

1. Add both `opening_soon.svg` and this `README.md` to your repository root. Commit & push.
2. On GitHub, the animation should display automatically in the README preview.
3. If GitHub's preview in your browser still shows a static image, open the SVG file directly in a new tab (click the SVG file in the repo) — animated SVGs usually play there.

If you want, I can also:
- Produce an animated **GIF/APNG** version (more foolproof for GitHub) — I can generate it and provide it for download.
- Create a **GitHub Pages** HTML page and a short README link to it.
- Customize the SVG text, colors, fonts, or size to match your GitHub profile (add your username, profile link, or custom message).

Tell me which option you prefer and I’ll give you the files."""

# Write files to /mnt/data
svg_path = "/mnt/data/opening_soon.svg"
readme_path = "/mnt/data/README_OPENING_SOON.md"
with open(svg_path, "w", encoding="utf-8") as f:
    f.write(svg_content)
with open(readme_path, "w", encoding="utf-8") as f:
    f.write(readme_content)

{"svg": svg_path, "readme": readme_path}
