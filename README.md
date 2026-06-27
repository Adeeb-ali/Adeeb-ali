html_content = '''<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>F1 Digital Twin — Race Strategy Platform</title>
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --surface-2: #1a1a24;
    --border: #252535;
    --text: #e8e8f0;
    --text-dim: #8888a0;
    --accent: #e10600;
    --accent-glow: rgba(225, 6, 0, 0.15);
    --green: #00d26a;
    --yellow: #ffaa00;
    --blue: #00a8ff;
    --purple: #a855f7;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    line-height: 1.7;
    min-height: 100vh;
  }

  /* ── Header ── */
  header {
    text-align: center;
    padding: 80px 20px 60px;
    background: linear-gradient(180deg, var(--surface) 0%, var(--bg) 100%);
    border-bottom: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }

  header::before {
    content: '';
    position: absolute;
    top: 0; left: 50%;
    transform: translateX(-50%);
    width: 600px; height: 300px;
    background: radial-gradient(ellipse, var(--accent-glow) 0%, transparent 70%);
    pointer-events: none;
  }

  .badge {
    display: inline-block;
    background: var(--accent);
    color: #fff;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 6px 16px;
    border-radius: 4px;
    margin-bottom: 24px;
    position: relative;
    z-index: 1;
  }

  h1 {
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 800;
    letter-spacing: -1px;
    line-height: 1.1;
    margin-bottom: 16px;
    position: relative;
    z-index: 1;
  }

  h1 span { color: var(--accent); }

  .subtitle {
    font-size: 1.15rem;
    color: var(--text-dim);
    max-width: 600px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  /* ── Layout ── */
  main { max-width: 900px; margin: 0 auto; padding: 0 24px 80px; }

  section { margin-top: 64px; }

  h2 {
    font-size: 1.4rem;
    font-weight: 700;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  h2::before {
    content: '';
    width: 4px; height: 24px;
    background: var(--accent);
    border-radius: 2px;
    flex-shrink: 0;
  }

  /* ── Cards ── */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px;
    margin-bottom: 16px;
    transition: border-color 0.2s, transform 0.2s;
  }

  .card:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
  }

  .card h3 {
    font-size: 1.1rem;
    font-weight: 700;
    margin-bottom: 12px;
    color: var(--text);
  }

  .card p, .card li {
    color: var(--text-dim);
    font-size: 0.95rem;
  }

  .card ul { list-style: none; padding-left: 0; }
  .card li { padding: 6px 0; padding-left: 20px; position: relative; }
  .card li::before {
    content: '›';
    position: absolute;
    left: 0;
    color: var(--accent);
    font-weight: 700;
  }

  /* ── IO Grid ── */
  .io-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  @media (max-width: 640px) { .io-grid { grid-template-columns: 1fr; } }

  .io-box {
    background: var(--surface-2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
  }

  .io-box h4 {
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: var(--accent);
    margin-bottom: 16px;
    font-weight: 700;
  }

  .io-box ul { list-style: none; }
  .io-box li {
    padding: 8px 0;
    border-bottom: 1px solid var(--border);
    font-size: 0.9rem;
    color: var(--text-dim);
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .io-box li:last-child { border-bottom: none; }

  .dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .dot-in { background: var(--green); box-shadow: 0 0 8px var(--green); }
  .dot-out { background: var(--blue); box-shadow: 0 0 8px var(--blue); }

  /* ── Feature Cards ── */
  .feature-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 16px;
  }

  .feature-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px;
    position: relative;
    overflow: hidden;
  }

  .feature-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--accent), var(--purple));
  }

  .feature-card h3 {
    font-size: 1.05rem;
    font-weight: 700;
    margin-bottom: 10px;
  }

  .feature-card p {
    font-size: 0.9rem;
    color: var(--text-dim);
  }

  .tag {
    display: inline-block;
    font-size: 0.65rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    padding: 3px 10px;
    border-radius: 4px;
    margin-bottom: 14px;
  }

  .tag-wow { background: rgba(168, 85, 247, 0.15); color: var(--purple); }
  .tag-core { background: rgba(0, 168, 255, 0.15); color: var(--blue); }
  .tag-eng { background: rgba(0, 210, 106, 0.15); color: var(--green); }

  /* ── Architecture ── */
  .arch-flow {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    gap: 8px;
    padding: 32px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
  }

  .arch-node {
    background: var(--surface-2);
    border: 1px solid var(--border);
    padding: 12px 20px;
    border-radius: 8px;
    font-size: 0.85rem;
    font-weight: 600;
    white-space: nowrap;
  }

  .arch-arrow {
    color: var(--accent);
    font-size: 1.2rem;
    font-weight: 700;
  }

  /* ── Physics Models ── */
  .physics-list {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 12px;
  }

  .physics-item {
    background: var(--surface-2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 16px 20px;
    font-size: 0.9rem;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .physics-item .icon {
    width: 32px; height: 32px;
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1rem;
    flex-shrink: 0;
  }

  /* ── Telemetry Comparison ── */
  .telemetry-bar {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px;
  }

  .driver-compare {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-bottom: 20px;
  }

  .driver {
    flex: 1;
    text-align: center;
    padding: 16px;
    border-radius: 8px;
    font-weight: 700;
  }

  .driver-a { background: rgba(0, 82, 147, 0.2); border: 1px solid #005293; color: #4aa8ff; }
  .driver-b { background: rgba(0, 210, 106, 0.2); border: 1px solid var(--green); color: var(--green); }

  .vs {
    font-size: 0.75rem;
    font-weight: 800;
    color: var(--text-dim);
    letter-spacing: 2px;
  }

  .trace-list {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 10px;
    margin-top: 16px;
  }

  .trace {
    background: var(--surface-2);
    padding: 10px 14px;
    border-radius: 6px;
    font-size: 0.8rem;
    color: var(--text-dim);
    text-align: center;
    border: 1px solid var(--border);
  }

  /* ── Strategy Decision ── */
  .decision-box {
    background: linear-gradient(135deg, var(--surface) 0%, var(--surface-2) 100%);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 32px;
    text-align: center;
  }

  .decision-prompt {
    font-size: 1.1rem;
    color: var(--text-dim);
    margin-bottom: 24px;
  }

  .decision-options {
    display: flex;
    gap: 16px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .decision-btn {
    padding: 14px 32px;
    border-radius: 8px;
    font-size: 1rem;
    font-weight: 700;
    border: 2px solid;
    cursor: default;
    transition: all 0.2s;
  }

  .btn-box {
    background: rgba(225, 6, 0, 0.1);
    border-color: var(--accent);
    color: var(--accent);
  }

  .btn-stay {
    background: rgba(0, 168, 255, 0.1);
    border-color: var(--blue);
    color: var(--blue);
  }

  .explanation {
    margin-top: 20px;
    font-size: 0.9rem;
    color: var(--text-dim);
    font-style: italic;
  }

  /* ── Tech Stack ── */
  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .tech-pill {
    background: var(--surface-2);
    border: 1px solid var(--border);
    padding: 8px 16px;
    border-radius: 20px;
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--text-dim);
  }

  /* ── Footer ── */
  footer {
    text-align: center;
    padding: 40px 20px;
    border-top: 1px solid var(--border);
    color: var(--text-dim);
    font-size: 0.85rem;
  }

  footer a {
    color: var(--accent);
    text-decoration: none;
    font-weight: 600;
  }

  /* ── Animations ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  section { animation: fadeUp 0.6s ease-out both; }
  section:nth-child(1) { animation-delay: 0.1s; }
  section:nth-child(2) { animation-delay: 0.2s; }
  section:nth-child(3) { animation-delay: 0.3s; }
  section:nth-child(4) { animation-delay: 0.4s; }
  section:nth-child(5) { animation-delay: 0.5s; }
  section:nth-child(6) { animation-delay: 0.6s; }
  section:nth-child(7) { animation-delay: 0.7s; }

</style>
</head>
<body>

<header>
  <div class="badge">Professional-Grade System</div>
  <h1>Formula 1 <span>Digital Twin</span><br>& Race Strategy Platform</h1>
  <p class="subtitle">Not a toy simulator. A physics-first, explainable AI system that answers: <em>"Given this track, weather, tire compound, fuel load, and driver — what is the fastest race strategy?"</em></p>
</header>

<main>

  <section>
    <h2>What It Does</h2>
    <div class="io-grid">
      <div class="io-box">
        <h4>Input Parameters</h4>
        <ul>
          <li><span class="dot dot-in"></span>Track layout & elevation</li>
          <li><span class="dot dot-in"></span>Weather conditions</li>
          <li><span class="dot dot-in"></span>Tire compound & age</li>
          <li><span class="dot dot-in"></span>Fuel load & burn rate</li>
          <li><span class="dot dot-in"></span>Safety car probability</li>
          <li><span class="dot dot-in"></span>Driver telemetry profile</li>
        </ul>
      </div>
      <div class="io-box">
        <h4>Output Predictions</h4>
        <ul>
          <li><span class="dot dot-out"></span>Predicted lap times</li>
          <li><span class="dot dot-out"></span>Tire degradation curve</li>
          <li><span class="dot dot-out"></span>Fuel consumption model</li>
          <li><span class="dot dot-out"></span>Optimal pit stop windows</li>
          <li><span class="dot dot-out"></span>Race position probabilities</li>
          <li><span class="dot dot-out"></span>Explainable strategy rationale</li>
        </ul>
      </div>
    </div>
  </section>

  <section>
    <h2>Why This Stands Out</h2>
    <div class="card">
      <p>F1 teams spend <strong>millions</strong> on simulation and race strategy tools. Building even 10–20% of such a system correctly signals:</p>
      <ul style="margin-top: 14px;">
        <li>Deep understanding of <strong>physical modeling</strong> and system dynamics</li>
        <li>Ability to handle <strong>uncertainty</strong> and probabilistic decision-making</li>
        <li>Experience architecting <strong>large, integrated systems</strong></li>
        <li>Engineering mindset — not just coding, but <strong>problem-solving at scale</strong></li>
      </ul>
    </div>
  </section>

  <section>
    <h2>Core Features</h2>
    <div class="feature-grid">
      <div class="feature-card">
        <span class="tag tag-core">Core System</span>
        <h3>Telemetry Replay Engine</h3>
        <p>Ingest publicly available F1 telemetry data. Replay laps with full speed, brake, throttle, and tire temperature traces. Corner-by-corner driver comparison.</p>
      </div>
      <div class="feature-card">
        <span class="tag tag-wow">Wow Factor</span>
        <h3>Strategy Optimization AI</h3>
        <p>Transparent, explainable model — not a black-box neural net. Recommends "Box Now" or "Stay Out" with full engineering rationale based on live race state.</p>
      </div>
      <div class="feature-card">
        <span class="tag tag-eng">Engineering</span>
        <h3>Custom Physics Models</h3>
        <p>Self-built tire degradation, fuel burn, aerodynamic drag, cornering dynamics, and track surface models. No Unity. No Unreal. Pure physics.</p>
      </div>
    </div>
  </section>

  <section>
    <h2>System Architecture</h2>
    <div class="arch-flow">
      <div class="arch-node">Telemetry Ingestion</div>
      <span class="arch-arrow">→</span>
      <div class="arch-node">Physics Engine</div>
      <span class="arch-arrow">→</span>
      <div class="arch-node">Degradation Models</div>
      <span class="arch-arrow">→</span>
      <div class="arch-node">Strategy Optimizer</div>
      <span class="arch-arrow">→</span>
      <div class="arch-node">Explainable Output</div>
    </div>
  </section>

  <section>
    <h2>Telemetry Replay & Driver Comparison</h2>
    <div class="telemetry-bar">
      <div class="driver-compare">
        <div class="driver driver-a">Max Verstappen</div>
        <div class="vs">VS</div>
        <div class="driver driver-b">Lewis Hamilton</div>
      </div>
      <p style="text-align:center; color: var(--text-dim); font-size: 0.9rem; margin-bottom: 8px;">Corner-by-corner trace analysis</p>
      <div class="trace-list">
        <div class="trace">Speed Traces</div>
        <div class="trace">Brake Traces</div>
        <div class="trace">Throttle Traces</div>
        <div class="trace">Tire Temperatures</div>
        <div class="trace">Time Delta</div>
        <div class="trace">Why They Gain</div>
      </div>
    </div>
  </section>

  <section>
    <h2>Strategy Optimization AI</h2>
    <div class="decision-box">
      <p class="decision-prompt">
        <strong>Current State:</strong> Lap 32 · Tire Age: 18 laps · Weather: Light Rain incoming · SC Probability: 15%
      </p>
      <div class="decision-options">
        <div class="decision-btn btn-box">BOX NOW — Inters</div>
        <div class="decision-btn btn-stay">STAY OUT 7 LAPS</div>
      </div>
      <p class="explanation">
        "Rain probability crosses 60% in 4 laps. Current tire delta vs. pit loss favors staying. <br>
        However, queue position risk and undercut threat from P3 suggest boxing this lap."
      </p>
    </div>
  </section>

  <section>
    <h2>Physics Models — Built From Scratch</h2>
    <div class="physics-list">
      <div class="physics-item">
        <div class="icon" style="background: rgba(225,6,0,0.15); color: var(--accent);">🛞</div>
        Tire Degradation Model
      </div>
      <div class="physics-item">
        <div class="icon" style="background: rgba(0,168,255,0.15); color: var(--blue);">⛽</div>
        Fuel Burn & Mass Model
      </div>
      <div class="physics-item">
        <div class="icon" style="background: rgba(0,210,106,0.15); color: var(--green);">🌬️</div>
        Aerodynamic Drag Model
      </div>
      <div class="physics-item">
        <div class="icon" style="background: rgba(255,170,0,0.15); color: var(--yellow);">🏎️</div>
        Cornering Dynamics
      </div>
      <div class="physics-item">
        <div class="icon" style="background: rgba(168,85,247,0.15); color: var(--purple);">🗺️</div>
        Track Surface & Grip Map
      </div>
      <div class="physics-item">
        <div class="icon" style="background: rgba(225,6,0,0.15); color: var(--accent);">🌡️</div>
        Thermal Degradation Curve
      </div>
    </div>
  </section>

  <section>
    <h2>Tech Stack</h2>
    <div class="tech-grid">
      <span class="tech-pill">C++</span>
      <span class="tech-pill">Python</span>
      <span class="tech-pill">PyTorch</span>
      <span class="tech-pill">FastAPI</span>
      <span class="tech-pill">Docker</span>
      <span class="tech-pill">NumPy / SciPy</span>
      <span class="tech-pill">Pandas</span>
      <span class="tech-pill">Matplotlib</span>
      <span class="tech-pill">Git</span>
      <span class="tech-pill">Linux</span>
      <span class="tech-pill">REST APIs</span>
      <span class="tech-pill">FPGA-Ready Pipeline</span>
    </div>
  </section>

</main>

<footer>
  <p>Built by <a href="https://linkedin.com/in/adeebali521" target="_blank">Adeeb Ali</a> · Electronics Engineer · FPGA & Edge AI · Motorsport Enthusiast</p>
  <p style="margin-top: 8px; font-size: 0.75rem; opacity: 0.6;">Not a toy. A system built with engineering rigor.</p>
</footer>

</body>
</html>'''

with open('/mnt/agents/output/f1_digital_twin.html', 'w', encoding='utf-8') as f:
    f.write(html_content)

print("Saved successfully!")
