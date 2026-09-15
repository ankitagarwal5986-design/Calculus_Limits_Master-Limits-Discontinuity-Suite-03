<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Brain &amp; Mind Academy • Calculus I: Comprehensive Limits &amp; Discontinuities</title>

  <!-- MathJax Configuration & Loader -->
  <script>
    window.MathJax = {
      tex: {
        inlineMath: [['\\(', '\\)'], ['$', '$']],
        displayMath: [['\\[', '\\]'], ['$$', '$$']],
        processEscapes: true
      },
      svg: { fontCache: 'global' }
    };
  </script>
  <script type="text/javascript" id="MathJax-script" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>

  <style>
    :root {
      --navy-dark: #0c4a6e;
      --brand-blue: #0284c7;
      --accent-cyan: #0ea5e9;
      --bg-tint: #f0f9ff;
      --card-surf: #ffffff;
      --border-accent: #7dd3fc;
      --border-soft: #bae6fd;
      --green-ok: #059669;
      --green-surf: #d1fae5;
      --red-fail: #dc2626;
      --red-surf: #fee2e2;
      --brand-gold: #f59e0b;
      --gold-dark: #d97706;
      --gold-surf: #fef3c7;
      --text-main: #0f172a;
      --text-muted: #475569;

      /* High-Contrast Clear Light Yellow Options Palette */
      --opt-yellow-bg: #fefce8;
      --opt-yellow-border: #fef08a;
      --opt-yellow-hover: #fef9c3;
      --opt-yellow-active: #fde047;
      --opt-yellow-text: #713f12;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
    }

    body {
      background-color: var(--bg-tint);
      color: var(--text-main);
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    header {
      background: var(--navy-dark);
      color: #fff;
      padding: 12px 24px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 12px rgba(12, 74, 110, 0.15);
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .brand-wrap {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .logo-badge {
      width: 44px;
      height: 44px;
      background: #ffffff;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    }

    .brand-title h1 {
      font-size: 1.15rem;
      font-weight: 700;
      letter-spacing: 0.5px;
    }

    .brand-title p {
      font-size: 0.78rem;
      color: var(--accent-cyan);
      font-weight: 500;
    }

    .header-controls {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .chip {
      background: rgba(255, 255, 255, 0.15);
      border: 1px solid var(--border-accent);
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 0.88rem;
      color: #ffffff;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .chip strong {
      color: #ffffff;
      font-weight: 800;
      letter-spacing: 0.3px;
    }

    .btn-icon {
      background: transparent;
      border: 1px solid var(--border-accent);
      color: #fff;
      border-radius: 50%;
      width: 36px;
      height: 36px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
    }

    nav {
      background: #ffffff;
      border-bottom: 1px solid var(--border-soft);
      display: flex;
      justify-content: center;
      gap: 6px;
      padding: 8px 16px;
      flex-wrap: wrap;
    }

    nav button {
      background: none;
      border: none;
      outline: none;
      padding: 9px 15px;
      font-size: 0.88rem;
      font-weight: 600;
      color: var(--text-muted);
      cursor: pointer;
      border-radius: 8px;
      transition: all 0.2s;
    }

    nav button.active {
      background: var(--bg-tint);
      color: var(--brand-blue);
      border-bottom: 3px solid var(--brand-blue);
    }

    main {
      flex: 1;
      padding: 24px;
      max-width: 1400px;
      margin: 0 auto;
      width: 100%;
    }

    .view {
      display: none;
    }

    .view.active {
      display: block;
    }

    #loginGateView {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(12, 74, 110, 0.92);
      backdrop-filter: blur(6px);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .login-box {
      background: #fff;
      padding: 36px;
      border-radius: 16px;
      width: 100%;
      max-width: 480px;
      text-align: center;
      box-shadow: 0 14px 35px rgba(0,0,0,0.3);
    }

    .login-box h2 {
      font-size: 1.45rem;
      color: var(--navy-dark);
      margin-bottom: 6px;
    }

    .login-box p {
      font-size: 0.88rem;
      color: var(--text-muted);
      margin-bottom: 20px;
      line-height: 1.5;
    }

    .resume-alert {
      display: none;
      background: #eff6ff;
      border: 1px solid var(--border-accent);
      border-radius: 8px;
      padding: 10px 14px;
      margin-bottom: 16px;
      font-size: 0.86rem;
      color: var(--navy-dark);
      text-align: left;
    }

    .login-box input {
      width: 100%;
      padding: 12px 16px;
      border: 1px solid var(--border-soft);
      border-radius: 8px;
      font-size: 1rem;
      margin-bottom: 16px;
      outline: none;
    }

    .btn-primary {
      background: var(--brand-blue);
      color: #fff;
      border: none;
      padding: 12px 24px;
      font-size: 1rem;
      font-weight: 600;
      border-radius: 8px;
      cursor: pointer;
      width: 100%;
      transition: background 0.2s;
    }

    .btn-primary:hover {
      background: var(--navy-dark);
    }

    .btn-secondary {
      background: transparent;
      border: 1px solid var(--border-accent);
      color: var(--navy-dark);
      padding: 9px 18px;
      font-size: 0.88rem;
      font-weight: 600;
      border-radius: 6px;
      cursor: pointer;
      width: 100%;
      margin-top: 10px;
    }

    .btn-secondary:hover {
      background: var(--bg-tint);
    }

    .theory-card {
      background: #fff;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      padding: 24px;
      margin-bottom: 24px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.02);
    }

    .theory-card h3 {
      color: var(--navy-dark);
      margin-bottom: 14px;
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 1.25rem;
    }

    .compendium-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 18px;
      margin: 16px 0;
    }

    .comp-card {
      background: #ffffff;
      border: 1px solid var(--border-soft);
      border-radius: 10px;
      padding: 16px;
      display: flex;
      flex-direction: column;
      box-shadow: 0 2px 6px rgba(12, 74, 110, 0.04);
    }

    .comp-card h4 {
      color: var(--navy-dark);
      border-bottom: 2px solid var(--border-soft);
      padding-bottom: 8px;
      margin-bottom: 10px;
      font-size: 1rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .recap-body {
      font-size: 0.9rem;
      line-height: 1.6;
      color: var(--text-main);
    }

    .formula-box {
      background: #f8fafc;
      border-left: 4px solid var(--brand-blue);
      border-radius: 0 6px 6px 0;
      padding: 8px 12px;
      margin-top: 8px;
    }

    .sheet-grid {
      display: grid;
      grid-template-columns: 1fr 340px;
      gap: 24px;
    }

    @media (max-width: 990px) {
      .sheet-grid {
        grid-template-columns: 1fr;
      }
    }

    .question-card {
      background: #fff;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      padding: 26px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.03);
    }

    .concept-tag {
      display: inline-block;
      padding: 4px 10px;
      border-radius: 14px;
      font-size: 0.75rem;
      font-weight: 700;
      letter-spacing: 0.4px;
      text-transform: uppercase;
      margin-bottom: 8px;
      background: #e0f2fe;
      color: #0369a1;
      border: 1px solid #7dd3fc;
    }

    .mcq-container {
      display: grid;
      grid-template-columns: 1fr;
      gap: 12px;
      margin: 18px 0;
    }

    /* Light Yellow Clear Options */
    .mcq-option-btn {
      background: var(--opt-yellow-bg);
      border: 2px solid var(--opt-yellow-border);
      border-radius: 10px;
      padding: 13px 18px;
      text-align: left;
      font-size: 0.96rem;
      color: var(--opt-yellow-text);
      cursor: pointer;
      transition: all 0.15s ease;
      display: flex;
      align-items: center;
      gap: 14px;
      box-shadow: 0 2px 5px rgba(254, 240, 138, 0.25);
    }

    .mcq-option-btn:hover:not(:disabled) {
      background: var(--opt-yellow-hover);
      border-color: var(--opt-yellow-active);
      transform: translateY(-1px);
    }

    .mcq-option-btn.selected-correct {
      background: var(--green-surf) !important;
      border-color: var(--green-ok) !important;
      color: var(--green-ok) !important;
      font-weight: 700;
      box-shadow: none;
    }

    .mcq-option-btn.selected-wrong {
      background: var(--red-surf) !important;
      border-color: var(--red-fail) !important;
      color: var(--red-fail) !important;
      box-shadow: none;
    }

    .opt-letter {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background: #ffffff;
      border: 2px solid var(--opt-yellow-active);
      font-weight: 800;
      color: var(--opt-yellow-text);
      flex-shrink: 0;
    }

    .attempts-badge {
      font-size: 0.8rem;
      font-weight: 700;
      padding: 4px 10px;
      border-radius: 12px;
      background: #f1f5f9;
      color: #64748b;
      margin-left: 6px;
    }

    .btn-reveal {
      background: var(--brand-gold);
      color: #fff;
      border: none;
      padding: 6px 14px;
      border-radius: 6px;
      font-weight: 600;
      font-size: 0.85rem;
      cursor: pointer;
      margin-left: 8px;
    }

    .btn-reveal:hover {
      background: var(--gold-dark);
    }

    .feedback-box {
      margin-top: 16px;
      padding: 16px;
      border-radius: 8px;
      font-size: 0.95rem;
      line-height: 1.65;
      display: block;
      animation: fadeIn 0.25s ease-in;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(4px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .feedback-box.correct {
      background: #ecfdf5;
      border-left: 5px solid var(--green-ok);
      color: #065f46;
    }

    .feedback-box.incorrect {
      background: #fef2f2;
      border-left: 5px solid var(--red-fail);
      color: #991b1b;
    }

    .svg-container {
      display: flex;
      justify-content: center;
      margin: 16px 0;
      padding: 14px;
      background: var(--bg-tint);
      border-radius: 8px;
      border: 1px solid var(--border-soft);
      overflow-x: auto;
    }

    .nav-toolbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 24px;
      padding-top: 18px;
      border-top: 1px solid var(--border-soft);
    }

    .nav-btn-group {
      display: flex;
      gap: 10px;
    }

    .btn-nav-action {
      background: #f8fafc;
      border: 1px solid var(--border-accent);
      color: var(--navy-dark);
      padding: 8px 18px;
      border-radius: 6px;
      font-weight: 600;
      font-size: 0.9rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: all 0.15s;
    }

    .btn-nav-action:hover:not(:disabled) {
      background: var(--bg-tint);
      border-color: var(--brand-blue);
    }

    .btn-nav-action:disabled {
      opacity: 0.45;
      cursor: not-allowed;
    }

    .btn-skip {
      border-color: var(--brand-gold);
      color: var(--gold-dark);
      background: var(--gold-surf);
    }

    .palette-box {
      background: #fff;
      border: 1px solid var(--border-soft);
      border-radius: 12px;
      padding: 16px;
      margin-bottom: 20px;
    }

    .palette-legend {
      display: flex;
      justify-content: space-between;
      font-size: 0.72rem;
      margin: 8px 0 12px 0;
      padding: 6px 8px;
      background: var(--bg-tint);
      border-radius: 6px;
    }

    .legend-item {
      display: flex;
      align-items: center;
      gap: 4px;
      font-weight: 600;
    }

    .legend-dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
    }

    .palette-grid {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 5px;
      margin-bottom: 12px;
    }

    .palette-btn {
      aspect-ratio: 1;
      border: 1px solid var(--border-soft);
      background: var(--bg-tint);
      border-radius: 6px;
      font-weight: 600;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.15s;
      font-size: 0.8rem;
      color: var(--navy-dark);
    }

    .palette-btn.active {
      border: 2px solid var(--navy-dark) !important;
      background: var(--border-accent);
      color: #fff;
      font-weight: 800;
    }

    .palette-btn.completed {
      background: var(--green-ok) !important;
      color: #fff !important;
      border-color: var(--green-ok) !important;
    }

    .palette-btn.skipped {
      background: var(--brand-gold) !important;
      color: #fff !important;
      border-color: var(--gold-dark) !important;
    }

    .hero-score-card {
      background: #fff;
      border-radius: 12px;
      border: 1px solid var(--border-soft);
      padding: 28px;
      text-align: center;
      margin-bottom: 24px;
      box-shadow: 0 4px 14px rgba(0,0,0,0.03);
    }

    .student-badge {
      display: inline-block;
      background: var(--bg-tint);
      border: 1px solid var(--border-accent);
      padding: 6px 18px;
      border-radius: 20px;
      font-size: 1rem;
      margin-bottom: 14px;
      color: var(--navy-dark);
    }

    .student-badge strong {
      color: var(--brand-blue);
    }

    .score-badge {
      font-size: 3rem;
      font-weight: 800;
      color: var(--brand-blue);
      margin: 8px 0;
    }

    .progress-bar-wrap {
      width: 100%;
      height: 12px;
      background: #e2e8f0;
      border-radius: 6px;
      overflow: hidden;
      margin: 16px 0;
    }

    .progress-bar-fill {
      height: 100%;
      background: var(--green-ok);
      width: 0%;
      transition: width 0.3s ease;
    }

    .toast {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: var(--navy-dark);
      color: #fff;
      padding: 12px 20px;
      border-radius: 8px;
      box-shadow: 0 4px 16px rgba(0,0,0,0.2);
      display: none;
      z-index: 1000;
    }
  </style>
</head>
<body>

  <header>
    <div class="brand-wrap">
      <div class="logo-badge">
        <svg width="34" height="34" viewBox="0 0 100 100" fill="none">
          <path d="M 20 30 Q 50 10 80 30" stroke="#f59e0b" stroke-width="8" stroke-linecap="round"/>
          <path d="M 26 40 Q 50 22 74 40" stroke="#f59e0b" stroke-width="8" stroke-linecap="round"/>
          <path d="M 32 50 Q 50 36 68 50" stroke="#f59e0b" stroke-width="7" stroke-linecap="round"/>
          <path d="M 18 80 Q 50 68 50 82 Q 50 68 82 80 L 82 52 Q 50 42 50 56 Q 50 42 18 52 Z" fill="#ffffff" stroke="#334155" stroke-width="7" stroke-linejoin="round"/>
        </svg>
      </div>
      <div class="brand-title">
        <h1>Brain &amp; Mind Academy</h1>
        <p>B&amp;M – The Experts • Calculus I: Master Limits &amp; Discontinuity Suite</p>
      </div>
    </div>
    <div class="header-controls">
      <div class="chip" id="timerChip">⏱️ 00:00</div>
      <div class="chip" id="userPill"><strong>Student: Guest</strong></div>
      <button class="btn-icon" id="audioToggleBtn" title="Toggle Audio">🔊</button>
    </div>
  </header>

  <nav>
    <button class="tab-btn active" onclick="switchTopicTab(0)">📖 Theory &amp; Classification</button>
    <button class="tab-btn" onclick="switchTopicTab(1)">🎯 Direct Evaluation</button>
    <button class="tab-btn" onclick="switchTopicTab(2)">🔍 Removable (Alg &amp; Trig)</button>
    <button class="tab-btn" onclick="switchTopicTab(3)">⚡ Jumps &amp; Kinks</button>
    <button class="tab-btn" onclick="switchTopicTab(4)">📉 Essential Discontinuities</button>
    <button class="tab-btn" onclick="switchTopicTab(5)">🌌 Limits at Infinity</button>
    <button class="tab-btn" onclick="switchTopicTab(6)">📋 Final Scorecard &amp; Solutions</button>
  </nav>

  <!-- Login Modal with Session Resume -->
  <div id="loginGateView">
    <div class="login-box">
      <h2>Calculus Limits Workstation</h2>
      <p>Continuous Evaluation Across Essential, Removable, Jump, Infinite &amp; Direct Limits</p>
      
      <div id="resumeAlertBox" class="resume-alert">
        <strong>Saved Session Available</strong><br>
        <span id="savedSessionDetails"></span>
      </div>

      <input type="text" id="studentNameInput" placeholder="Enter Student Name" />
      <button class="btn-primary" id="startSessionBtn" onclick="initDirectLogin(false)">Start Session</button>
      <button class="btn-secondary" id="resumeSessionBtn" style="display:none;" onclick="initDirectLogin(true)">Resume Saved Progress</button>
    </div>
  </div>

  <main>
    <!-- View 0: Comprehensive Theory Compendium -->
    <div id="viewTheory" class="view active">
      <div class="theory-card">
        <h3>📐 Mathematical Framework: Limit Behaviors &amp; Discontinuities</h3>
        <p class="theory-intro-text">
          A function \(f(x)\) has a limit \(L\) as \(x \to c\) if and only if both one-sided limits exist and are equal: \(\lim_{x \to c^-} f(x) = \lim_{x \to c^+} f(x) = L\).
        </p>

        <div class="compendium-grid">
          <div class="comp-card">
            <h4>1. Direct Evaluation</h4>
            <div class="recap-body">
              <p>For polynomials, radicals, and rationals within their domain:</p>
              <div class="formula-box">
                \[\lim_{x \to c} f(x) = f(c)\]
                <p>If substitution gives \(\frac{0}{0}\), algebraic simplification is required.</p>
              </div>
            </div>
          </div>

          <div class="comp-card">
            <h4>2. Removable Discontinuities</h4>
            <div class="recap-body">
              <p>Factor out common linear terms or rationalize conjugates:</p>
              <div class="formula-box">
                \[\lim_{x \to 0} \frac{\sin x}{x} = 1, \quad \lim_{x \to 0} \frac{1 - \cos x}{x} = 0\]
                <p>Removes indeterminate forms resulting in a point hole.</p>
              </div>
            </div>
          </div>

          <div class="comp-card">
            <h4>3. Jump Discontinuities &amp; Kinks</h4>
            <div class="recap-body">
              <p>Common in piecewise functions and absolute value ratios:</p>
              <div class="formula-box">
                \[\lim_{x \to c^-} f(x) \ne \lim_{x \to c^+} f(x) \implies \text{Jump}\]
                <p>When one-sided limits match but slopes differ, a <em>kink</em> occurs.</p>
              </div>
            </div>
          </div>

          <div class="comp-card">
            <h4>4. Essential &amp; Infinite Limits</h4>
            <div class="recap-body">
              <p>Occur when the simplified denominator approaches \(0\):</p>
              <div class="formula-box">
                \[\lim_{x \to c} \frac{k}{0^+} = +\infty, \quad \lim_{x \to c} \frac{k}{0^-} = -\infty\]
                <p>Produces vertical asymptotes \(x = c\).</p>
              </div>
            </div>
          </div>

          <div class="comp-card">
            <h4>5. Limits at Infinity &amp; Asymptotes</h4>
            <div class="recap-body">
              <p>Analyze leading powers as \(x \to \pm\infty\):</p>
              <div class="formula-box">
                <p>• Note that \(\sqrt{x^2} = |x| = -x\) for \(x < 0\).</p>
                <p>• Exponential decay: \(\lim_{x \to -\infty} e^x = 0\).</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- View 1: Interactive Question Workstation -->
    <div id="viewPractice" class="view">
      <div class="sheet-grid">
        <div class="question-card" id="activeQuestionCard"></div>

        <aside>
          <div class="palette-box">
            <div style="display: flex; justify-content: space-between; align-items: center;">
              <h4 id="paletteModuleTitle">Question Palette</h4>
              <span style="font-size:0.8rem; color:var(--text-muted);" id="paletteCount">0 / 0</span>
            </div>

            <div class="palette-legend">
              <div class="legend-item"><span class="legend-dot" style="background:var(--green-ok);"></span> Solved</div>
              <div class="legend-item"><span class="legend-dot" style="background:#f59e0b;"></span> Skipped</div>
              <div class="legend-item"><span class="legend-dot" style="background:#7dd3fc;"></span> Active</div>
              <div class="legend-item"><span class="legend-dot" style="background:#f0f9ff; border:1px solid #bae6fd;"></span> Unseen</div>
            </div>
            
            <div class="palette-grid" id="paletteGrid"></div>
            
            <button class="btn-primary" style="margin-top: 10px; background: var(--navy-dark);" onclick="switchTopicTab(6)">
              📊 View Performance Scorecard
            </button>
            <button class="btn-secondary" style="margin-top: 8px; border-color: #cbd5e1;" onclick="resetStudentProgress()">
              🔄 Reset Progress
            </button>
          </div>

          <div class="palette-box" style="background: #f8fafc;">
            <h4 style="font-size: 0.92rem; margin-bottom: 8px; color: var(--navy-dark);">Workstation Features</h4>
            <p style="font-size: 0.82rem; line-height: 1.6; color: var(--text-muted);">
              • Interactive clear light yellow option buttons for visibility.<br/>
              • <strong>2 attempts</strong> per problem before the <strong>Reveal Solution</strong> button unlocks.<br/>
              • Scaled SVG graphs matching worksheet specifications.<br/>
              • Progress auto-saves continuously to your local session.
            </p>
          </div>
        </aside>
      </div>
    </div>

    <!-- View 2: Complete Scorecard & Master Solutions -->
    <div id="viewResults" class="view">
      <div class="hero-score-card">
        <h2>Limits &amp; Discontinuities Diagnostic Scorecard</h2>
        <div class="student-badge" id="reportStudentBadge"><strong>Student: Guest</strong></div>
        <div class="score-badge" id="scoreValue">0 / 25</div>
        <div class="progress-bar-wrap">
          <div class="progress-bar-fill" id="progressBarFill"></div>
        </div>
        <p id="scoreSubtitle" style="font-size:1.02rem; font-weight:600; color:var(--navy-dark); margin-top:8px;">
          Comprehensive review across all 5 calculus limit modules.
        </p>
        <button class="btn-primary" style="margin-top: 14px; max-width: 240px;" onclick="window.print()">🖨️ Print Final Scorecard</button>
      </div>

      <div id="completeSolutionsContainer"></div>
    </div>
  </main>

  <div class="toast" id="toastMessage"></div>

  <script>
    /* ==========================================================================
       COMPLETE CALCULUS LIMITS DATASET (ALL 5 WORKSHEETS MAPPED)
       ========================================================================== */
    const ALL_QUESTIONS = [
      // ---------- MODULE 1: DIRECT EVALUATION ----------
      {
        id: 1,
        module: 1,
        moduleName: "Direct Evaluation",
        source: "01 - Limits by Direct Evaluation.pdf, Q3",
        title: "Cubic Polynomial Direct Evaluation",
        prompt: "Evaluate the limit[cite: 10]: \\[\\lim_{x \\to 2} (x^3 - x^2 - 4)\\]",
        options: [
          { label: "A", text: "0" },
          { label: "B", text: "4" },
          { label: "C", text: "-4" },
          { label: "D", text: "8" }
        ],
        correctIndex: 0,
        explanation: "Polynomials are continuous everywhere. Directly substitute \\(x = 2\\)[cite: 10]:<br>\\[2^3 - 2^2 - 4 = 8 - 4 - 4 = 0\\]"
      },
      {
        id: 2,
        module: 1,
        moduleName: "Direct Evaluation",
        source: "01 - Limits by Direct Evaluation.pdf, Q6",
        title: "Radical Direct Evaluation",
        prompt: "Evaluate the limit[cite: 10]: \\[\\lim_{x \\to \\frac{3}{2}} -\\sqrt{2x + 4}\\]",
        options: [
          { label: "A", text: "-\\sqrt{7}" },
          { label: "B", text: "\\sqrt{7}" },
          { label: "C", text: "-\\sqrt{10}" },
          { label: "D", text: "-7" }
        ],
        correctIndex: 0,
        explanation: "Substitute \\(x = 3/2\\) directly into the radical[cite: 10]:<br>\\[-\\sqrt{2\\left(\\frac{3}{2}\\right) + 4} = -\\sqrt{3 + 4} = -\\sqrt{7}\\]"
      },
      {
        id: 3,
        module: 1,
        moduleName: "Direct Evaluation",
        source: "01 - Limits by Direct Evaluation.pdf, Q7",
        title: "Rational Direct Evaluation",
        prompt: "Evaluate the limit[cite: 10]: \\[\\lim_{x \\to 1} -\\frac{x - 4}{x^2 - 6x + 8}\\]",
        options: [
          { label: "A", text: "1" },
          { label: "B", text: "-1" },
          { label: "C", text: "3/8" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "Denominator at \\(x = 1\\) is \\(1 - 6 + 8 = 3 \\ne 0\\)[cite: 10]. Directly evaluate[cite: 10]:<br>\\[-\\frac{1 - 4}{1 - 6 + 8} = -\\frac{-3}{3} = 1\\]"
      },
      {
        id: 4,
        module: 1,
        moduleName: "Direct Evaluation",
        source: "01 - Limits by Direct Evaluation.pdf, Q10",
        title: "Trigonometric Direct Evaluation",
        prompt: "Evaluate the limit[cite: 10]: \\[\\lim_{x \\to \\frac{3\\pi}{4}} 2\\cos(x)\\]",
        options: [
          { label: "A", text: "-\\sqrt{2}" },
          { label: "B", text: "\\sqrt{2}" },
          { label: "C", text: "-1" },
          { label: "D", text: "-\\frac{\\sqrt{2}}{2}" }
        ],
        correctIndex: 0,
        explanation: "Substitute \\(x = 3\\pi/4\\) into the cosine function[cite: 10]:<br>\\[2\\cos\\left(\\frac{3\\pi}{4}\\right) = 2\\left(-\\frac{\\sqrt{2}}{2}\\right) = -\\sqrt{2}\\]"
      },

      // ---------- MODULE 2: REMOVABLE DISCONTINUITIES ----------
      {
        id: 5,
        module: 2,
        moduleName: "Removable Discontinuities",
        source: "01 - Limits at Removable Discontinuities.pdf, Q1",
        title: "Removable Discontinuity with Isolated Point",
        prompt: "Evaluate the limit from the provided graph and equation[cite: 9]: \\[\\lim_{x \\to 2} f(x), \\quad f(x) = \\begin{cases} -x^2 + 2 & x \\ne 2 \\\\ -5 & x = 2 \\end{cases}\\]",
        svg: `<svg width="100%" height="220" viewBox="0 0 380 200" style="max-width:380px;">
          <rect width="380" height="200" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <!-- Grid -->
          <defs><pattern id="g1" width="20" height="20" patternUnits="userSpaceOnUse"><path d="M 20 0 L 0 0 0 20" fill="none" stroke="#f1f5f9" stroke-width="1"/></pattern></defs>
          <rect width="380" height="200" fill="url(#g1)"/>
          <line x1="20" y1="80" x2="360" y2="80" stroke="#64748b" stroke-width="1.5"/>
          <line x1="160" y1="15" x2="160" y2="185" stroke="#64748b" stroke-width="1.5"/>
          <text x="350" y="95" font-size="11" fill="#475569">x</text><text x="166" y="25" font-size="11" fill="#475569">f(x)</text>
          <!-- Parabola y = -x^2 + 2, vertex (160, 60), hole at x=2 (200, 100) -->
          <path d="M 100,180 Q 160,20 220,180" fill="none" stroke="#0284c7" stroke-width="2.5"/>
          <circle cx="200" cy="100" r="4.5" fill="#ffffff" stroke="#0284c7" stroke-width="2.2"/>
          <text x="210" y="98" font-size="10" fill="#0284c7">Hole: (2, −2)</text>
          <!-- Point (2, -5) -> (200, 130) -->
          <circle cx="200" cy="130" r="4.5" fill="#0c4a6e"/>
          <text x="210" y="134" font-size="10" fill="#0c4a6e">(2, −5)</text>
        </svg>`,
        options: [
          { label: "A", text: "-2" },
          { label: "B", text: "-5" },
          { label: "C", text: "2" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "Limits inspect behavior arbitrarily close to \\(x = 2\\), not at \\(x = 2\\)[cite: 9]:<br>\\[\\lim_{x \\to 2} (-x^2 + 2) = -(2)^2 + 2 = -2\\]<br>The isolated point \\(f(2) = -5\\) creates a removable discontinuity but does not change the limit[cite: 9]."
      },
      {
        id: 6,
        module: 2,
        moduleName: "Removable Discontinuities",
        source: "01 - Limits at Removable Discontinuities.pdf, Q2",
        title: "Canceled Factor Removable Discontinuity",
        prompt: "Evaluate the limit[cite: 9]: \\[\\lim_{x \\to -2} -\\frac{x^2 - 4}{x + 2}\\]",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="130" x2="360" y2="130" stroke="#64748b" stroke-width="1.5"/>
          <line x1="190" y1="15" x2="190" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <!-- Line y = -(x-2) = -x + 2, hole at (-2, 4) -> (150, 50) -->
          <line x1="50" y1="10" x2="330" y2="150" stroke="#0284c7" stroke-width="2.5"/>
          <circle cx="150" cy="50" r="4.5" fill="#ffffff" stroke="#0284c7" stroke-width="2.2"/>
          <text x="160" y="48" font-size="10" font-weight="bold" fill="#0284c7">Hole: (−2, 4)</text>
        </svg>`,
        options: [
          { label: "A", text: "4" },
          { label: "B", text: "-4" },
          { label: "C", text: "0" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "Factor the numerator[cite: 9]:<br>\\[-\\frac{x^2 - 4}{x + 2} = -\\frac{(x - 2)(x + 2)}{x + 2} = -(x - 2) = -x + 2\\quad (x \\ne -2)\\]<br>Now evaluate the limit[cite: 9]:<br>\\[\\lim_{x \\to -2} (-x + 2) = -(-2) + 2 = 4\\]"
      },
      {
        id: 7,
        module: 2,
        moduleName: "Removable Discontinuities",
        source: "01 - Limits at Removable Discontinuities.pdf, Q11",
        title: "Complex Fraction Removable Limit",
        prompt: "Evaluate the limit[cite: 9]: \\[\\lim_{x \\to 0} \\frac{\\frac{1}{-4 + x} + \\frac{1}{4}}{x}\\]",
        options: [
          { label: "A", text: "-\\frac{1}{16}" },
          { label: "B", text: "\\frac{1}{16}" },
          { label: "C", text: "-\\frac{1}{4}" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "Find a common denominator in the numerator[cite: 9]:<br>\\[\\frac{\\frac{4 + (-4 + x)}{4(-4 + x)}}{x} = \\frac{\\frac{x}{4(-4 + x)}}{x} = \\frac{1}{4(-4 + x)}\\]<br>Taking \\(x \\to 0\\)[cite: 9]:<br>\\[\\frac{1}{4(-4 + 0)} = -\\frac{1}{16}\\]"
      },
      {
        id: 8,
        module: 2,
        moduleName: "Removable Discontinuities",
        source: "01 - Limits at Removable Discontinuities.pdf, Q13",
        title: "Conjugate Radical Rationalization",
        prompt: "Evaluate the limit[cite: 9]: \\[\\lim_{x \\to 5} \\frac{x - 5}{\\sqrt{x + 4} - 3}\\]",
        options: [
          { label: "A", text: "6" },
          { label: "B", text: "3" },
          { label: "C", text: "1/6" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "Multiply numerator and denominator by the conjugate \\(\\sqrt{x + 4} + 3\\)[cite: 9]:<br>\\[\\frac{(x - 5)(\\sqrt{x + 4} + 3)}{(x + 4) - 9} = \\frac{(x - 5)(\\sqrt{x + 4} + 3)}{x - 5} = \\sqrt{x + 4} + 3\\]<br>As \\(x \\to 5\\)[cite: 9]: \\(\\sqrt{9} + 3 = 3 + 3 = 6\\)."
      },
      {
        id: 9,
        module: 2,
        moduleName: "Removable Discontinuities",
        source: "01 - Limits at Removable Discontinuities Trig.pdf, Q3",
        title: "Tangent Trig Limit",
        prompt: "Evaluate the trigonometric limit[cite: 8]: \\[\\lim_{x \\to 0} \\frac{\\tan(x)}{3x}\\]",
        options: [
          { label: "A", text: "1/3" },
          { label: "B", text: "3" },
          { label: "C", text: "1" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "Rewrite \\(\\tan(x) = \\frac{\\sin(x)}{\\cos(x)}\\)[cite: 8]:<br>\\[\\lim_{x \\to 0} \\frac{1}{3} \\cdot \\frac{\\sin(x)}{x} \\cdot \\frac{1}{\\cos(x)} = \\frac{1}{3}(1)(1) = \\frac{1}{3}\\]"
      },
      {
        id: 10,
        module: 2,
        moduleName: "Removable Discontinuities",
        source: "01 - Limits at Removable Discontinuities Trig.pdf, Q6",
        title: "Squared Sine Trigonometric Limit",
        prompt: "Evaluate the limit[cite: 8]: \\[\\lim_{x \\to 0} \\frac{\\sin^2(2x)}{x^2}\\]",
        options: [
          { label: "A", text: "4" },
          { label: "B", text: "2" },
          { label: "C", text: "1" },
          { label: "D", text: "16" }
        ],
        correctIndex: 0,
        explanation: "Rewrite as a square of a standard limit[cite: 8]:<br>\\[\\left(\\lim_{x \\to 0} \\frac{\\sin(2x)}{x}\\right)^2 = \\left(2 \\lim_{x \\to 0} \\frac{\\sin(2x)}{2x}\\right)^2 = (2 \\times 1)^2 = 4\\]"
      },

      // ---------- MODULE 3: JUMP DISCONTINUITIES & KINKS ----------
      {
        id: 11,
        module: 3,
        moduleName: "Jump Discontinuities & Kinks",
        source: "01 - Limits at Jump Discontinuities and Kinks.pdf, Q1",
        title: "One-Sided Absolute Value Limit",
        prompt: "Evaluate the limit[cite: 7]: \\[\\lim_{x \\to -1^+} \\frac{4x + 4}{|x + 1|}\\]",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="90" x2="360" y2="90" stroke="#64748b" stroke-width="1.5"/>
          <line x1="190" y1="15" x2="190" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <!-- Ray at y = 4 for x > -1 (x=160 to 360) -->
          <line x1="164" y1="40" x2="360" y2="40" stroke="#0284c7" stroke-width="2.5"/>
          <circle cx="160" cy="40" r="4.5" fill="#ffffff" stroke="#0284c7" stroke-width="2.2"/>
          <!-- Ray at y = -4 for x < -1 -->
          <line x1="20" y1="140" x2="156" y2="140" stroke="#0284c7" stroke-width="2.5"/>
          <circle cx="160" cy="140" r="4.5" fill="#ffffff" stroke="#0284c7" stroke-width="2.2"/>
          <text x="170" y="35" font-size="10" font-weight="bold" fill="#0284c7">y = 4 (x > −1)</text>
          <text x="50" y="155" font-size="10" font-weight="bold" fill="#0284c7">y = −4 (x < −1)</text>
        </svg>`,
        options: [
          { label: "A", text: "4" },
          { label: "B", text: "-4" },
          { label: "C", text: "0" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "For \\(x > -1\\), \\(x + 1 > 0\\), so \\(|x + 1| = x + 1\\)[cite: 7]:<br>\\[\\lim_{x \\to -1^+} \\frac{4(x + 1)}{x + 1} = 4\\]"
      },
      {
        id: 12,
        module: 3,
        moduleName: "Jump Discontinuities & Kinks",
        source: "01 - Limits at Jump Discontinuities and Kinks.pdf, Q3",
        title: "Kink / Continuous Corner Point",
        prompt: "Evaluate the two-sided limit[cite: 7]: \\[\\lim_{x \\to -3} f(x), \\quad f(x) = \\begin{cases} -x^2 - 10x - 24 & x \\le -3 \\\\ 2x + 3 & x > -3 \\end{cases}\\]",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="60" x2="360" y2="60" stroke="#64748b" stroke-width="1.5"/>
          <line x1="220" y1="15" x2="220" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <!-- Parabola left of -3 meeting line at (-3, -3) -> (140, 120) -->
          <path d="M 60,165 Q 100,60 140,120" fill="none" stroke="#0284c7" stroke-width="2.5"/>
          <line x1="140" y1="120" x2="260" y2="30" stroke="#0284c7" stroke-width="2.5"/>
          <circle cx="140" cy="120" r="4.5" fill="#059669"/>
          <text x="148" y="130" font-size="10" font-weight="bold" fill="#059669">Kink: (−3, −3)</text>
        </svg>`,
        options: [
          { label: "A", text: "-3" },
          { label: "B", text: "3" },
          { label: "C", text: "-9" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "Check both one-sided limits[cite: 7]:<br>• Left: \\(\\lim_{x \\to -3^-} (-x^2 - 10x - 24) = -(-3)^2 - 10(-3) - 24 = -9 + 30 - 24 = -3\\)[cite: 7]<br>• Right: \\(\\lim_{x \\to -3^+} (2x + 3) = 2(-3) + 3 = -3\\)[cite: 7]<br>Because both one-sided limits are equal to \\(-3\\), the limit is \\(-3\\) (forming a continuous kink)[cite: 7]."
      },
      {
        id: 13,
        module: 3,
        moduleName: "Jump Discontinuities & Kinks",
        source: "01 - Limits at Jump Discontinuities and Kinks.pdf, Q4",
        title: "Two-Sided Jump Discontinuity Limit",
        prompt: "Evaluate the limit[cite: 7]: \\[\\lim_{x \\to -1} f(x), \\quad f(x) = \\begin{cases} x & x < -1 \\\\ -x^2 + 2x & x \\ge -1 \\end{cases}\\]",
        options: [
          { label: "A", text: "Does not exist" },
          { label: "B", text: "-1" },
          { label: "C", text: "-3" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "• Left limit: \\(\\lim_{x \\to -1^-} x = -1\\)[cite: 7]<br>• Right limit: \\(\\lim_{x \\to -1^+} (-x^2 + 2x) = -(-1)^2 + 2(-1) = -1 - 2 = -3\\)[cite: 7]<br>Since the one-sided limits differ (\\(-1 \\ne -3\\)), the two-sided limit does not exist[cite: 7]."
      },
      {
        id: 14,
        module: 3,
        moduleName: "Jump Discontinuities & Kinks",
        source: "01 - Limits at Jump Discontinuities and Kinks.pdf, Q9",
        title: "Greatest Integer / Floor Function Limit",
        prompt: "Evaluate the one-sided limit[cite: 7]: \\[\\lim_{x \\to 0^+} \\lfloor -2x + 1 \\rfloor\\]",
        options: [
          { label: "A", text: "0" },
          { label: "B", text: "1" },
          { label: "C", text: "-1" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "As \\(x \\to 0^+\\) (e.g., \\(x = 0.01\\)), \\(-2x + 1 = 1 - 0.02 = 0.98\\)[cite: 7].<br>The floor of any number in \\([0, 1)\\) is \\(0\\)[cite: 7]. Thus, \\(\\lim_{x \\to 0^+} \\lfloor -2x + 1 \\rfloor = 0\\)[cite: 7]."
      },

      // ---------- MODULE 4: ESSENTIAL / INFINITE DISCONTINUITIES ----------
      {
        id: 15,
        module: 4,
        moduleName: "Essential Discontinuities",
        source: "01 - Limits at Essential Discontinuities.pdf, Q1",
        title: "Vertical Asymptote with One-Sided Infinite Limit",
        prompt: "Evaluate the one-sided limit from the provided graph[cite: 5]: \\[\\lim_{x \\to -3^+} \\frac{x + 2}{x^2 + 5x + 6}\\]",
        svg: `<svg width="100%" height="220" viewBox="0 0 380 200" style="max-width:380px;">
          <rect width="380" height="200" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <!-- Grid -->
          <defs><pattern id="g2" width="20" height="20" patternUnits="userSpaceOnUse"><path d="M 20 0 L 0 0 0 20" fill="none" stroke="#f1f5f9" stroke-width="1"/></pattern></defs>
          <rect width="380" height="200" fill="url(#g2)"/>
          <line x1="20" y1="100" x2="360" y2="100" stroke="#64748b" stroke-width="1.5"/>
          <line x1="260" y1="15" x2="260" y2="185" stroke="#64748b" stroke-width="1.5"/>
          <text x="350" y="115" font-size="11" fill="#475569">x</text><text x="266" y="25" font-size="11" fill="#475569">f(x)</text>
          <!-- Vertical asymptote at x = -3 (scaled: x=140) -->
          <line x1="140" y1="15" x2="140" y2="185" stroke="#dc2626" stroke-width="1.5" stroke-dasharray="4"/>
          <!-- Left branch -> -infinity -->
          <path d="M 40,105 Q 120,110 135,185" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <!-- Right branch from +infinity down through hole at (-2, 1) -> (180, 80) -->
          <path d="M 145,15 Q 155,75 178,79" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <circle cx="180" cy="80" r="4.5" fill="#ffffff" stroke="#0284c7" stroke-width="2.2"/>
          <path d="M 182,81 Q 220,90 350,98" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <text x="100" y="30" font-size="10" fill="#dc2626">x = −3 (VA)</text>
          <text x="188" y="75" font-size="9" fill="#0284c7">Hole: (−2, 1)</text>
        </svg>`,
        options: [
          { label: "A", text: "∞" },
          { label: "B", text: "-∞" },
          { label: "C", text: "1" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "Factor the denominator[cite: 5]:<br>\\[\\frac{x + 2}{(x + 2)(x + 3)} = \\frac{1}{x + 3} \\quad (x \\ne -2)\\]<br>As \\(x \\to -3^+\\), \\(x + 3 > 0\\) approaches \\(0^+\\)[cite: 5]:<br>\\[\\lim_{x \\to -3^+} \\frac{1}{x + 3} = \\frac{1}{0^+} = +\\infty\\]"
      },
      {
        id: 16,
        module: 4,
        moduleName: "Essential Discontinuities",
        source: "01 - Limits at Essential Discontinuities.pdf, Q2",
        title: "Two-Sided Limit at Vertical Asymptote",
        prompt: "Evaluate the two-sided limit[cite: 5]: \\[\\lim_{x \\to -4} \\frac{x^2}{4x + 16}\\]",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="100" x2="360" y2="100" stroke="#64748b" stroke-width="1.5"/>
          <line x1="260" y1="15" x2="260" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <!-- VA at x = -4 -> x=120 -->
          <line x1="120" y1="15" x2="120" y2="165" stroke="#dc2626" stroke-width="1.5" stroke-dasharray="4"/>
          <!-- Left branch plunging to -infinity -->
          <path d="M 30,130 Q 90,140 115,165" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <!-- Right branch shooting to +infinity -->
          <path d="M 125,15 Q 150,90 260,100 T 350,85" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <text x="80" y="30" font-size="10" fill="#dc2626">x = −4 (VA)</text>
        </svg>`,
        options: [
          { label: "A", text: "Does not exist" },
          { label: "B", text: "∞" },
          { label: "C", text: "-∞" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "Numerator at \\(x = -4\\) is \\((-4)^2 = 16 > 0\\)[cite: 5]. Denominator is \\(4(x + 4)\\)[cite: 5]:<br>• As \\(x \\to -4^-\\): \\(\\frac{16}{0^-} = -\\infty\\)[cite: 5]<br>• As \\(x \\to -4^+\\): \\(\\frac{16}{0^+} = +\\infty\\)[cite: 5]<br>Since the left and right limits are opposite infinities, the two-sided limit does not exist[cite: 5]."
      },
      {
        id: 17,
        module: 4,
        moduleName: "Essential Discontinuities",
        source: "01 - Limits at Essential Discontinuities.pdf, Q3",
        title: "Rational Function One-Sided Limit",
        prompt: "Evaluate the limit[cite: 5]: \\[\\lim_{x \\to -2^+} \\frac{3x}{x + 2}\\]",
        options: [
          { label: "A", text: "-∞" },
          { label: "B", text: "∞" },
          { label: "C", text: "3" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "As \\(x \\to -2^+\\), numerator approaches \\(3(-2) = -6 < 0\\), and denominator approaches \\(0^+\\)[cite: 5]:<br>\\[\\lim_{x \\to -2^+} \\frac{3x}{x + 2} = \\frac{-6}{0^+} = -\\infty\\]"
      },
      {
        id: 18,
        module: 4,
        moduleName: "Essential Discontinuities",
        source: "01 - Limits at Essential Discontinuities.pdf, Q11",
        title: "Trigonometric Essential Limit",
        prompt: "Evaluate the limit[cite: 5]: \\[\\lim_{x \\to \\frac{\\pi}{4}^-} 2\\sec(2x)\\]",
        options: [
          { label: "A", text: "∞" },
          { label: "B", text: "-∞" },
          { label: "C", text: "2" },
          { label: "D", text: "0" }
        ],
        correctIndex: 0,
        explanation: "Rewrite in terms of cosine[cite: 5]: \\(2\\sec(2x) = \\frac{2}{\\cos(2x)}\\)[cite: 5].<br>As \\(x \\to (\\pi/4)^-\\), \\(2x \\to (\\pi/2)^-\\), where \\(\\cos(2x) > 0\\) approaches \\(0^+\\)[cite: 5]:<br>\\[\\lim_{x \\to \\frac{\\pi}{4}^-} \\frac{2}{\\cos(2x)} = \\frac{2}{0^+} = +\\infty\\]"
      },

      // ---------- MODULE 5: LIMITS AT INFINITY ----------
      {
        id: 19,
        module: 5,
        moduleName: "Limits at Infinity",
        source: "01 - Limits at Infinity.pdf, Q1",
        title: "Rational Function Decaying to Zero",
        prompt: "Evaluate the limit at negative infinity[cite: 6]: \\[\\lim_{x \\to -\\infty} \\frac{x + 2}{x^2 + x + 1}\\]",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="100" x2="360" y2="100" stroke="#64748b" stroke-width="1.5"/>
          <line x1="190" y1="15" x2="190" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <!-- Curve y = (x+2)/(x^2+x+1) -->
          <path d="M 20,99 Q 100,98 120,100 Q 140,105 180,60 Q 210,75 360,98" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <text x="50" y="85" font-size="10" font-weight="bold" fill="#0284c7">y → 0 as x → −∞</text>
        </svg>`,
        options: [
          { label: "A", text: "0" },
          { label: "B", text: "1" },
          { label: "C", text: "-∞" },
          { label: "D", text: "∞" }
        ],
        correctIndex: 0,
        explanation: "Divide both numerator and denominator by highest degree \\(x^2\\)[cite: 6]:<br>\\[\\lim_{x \\to -\\infty} \\frac{\\frac{1}{x} + \\frac{2}{x^2}}{1 + \\frac{1}{x} + \\frac{1}{x^2}} = \\frac{0 + 0}{1 + 0 + 0} = 0\\]"
      },
      {
        id: 20,
        module: 5,
        moduleName: "Limits at Infinity",
        source: "01 - Limits at Infinity.pdf, Q3",
        title: "Horizontal Asymptote Evaluation",
        prompt: "Evaluate the limit[cite: 6]: \\[\\lim_{x \\to -\\infty} \\frac{2x^2}{x^2 - 4}\\]",
        svg: `<svg width="100%" height="200" viewBox="0 0 380 180" style="max-width:380px;">
          <rect width="380" height="180" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5" rx="6"/>
          <line x1="20" y1="120" x2="360" y2="120" stroke="#64748b" stroke-width="1.5"/>
          <line x1="190" y1="15" x2="190" y2="165" stroke="#64748b" stroke-width="1.5"/>
          <!-- Horizontal asymptote at y = 2 -> (y=70) -->
          <line x1="20" y1="70" x2="360" y2="70" stroke="#dc2626" stroke-width="1.5" stroke-dasharray="4"/>
          <!-- Outer branches approaching y = 2 -->
          <path d="M 20,72 Q 100,75 130,20" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <path d="M 250,20 Q 280,75 360,72" fill="none" stroke="#0284c7" stroke-width="2.2"/>
          <text x="40" y="60" font-size="10" font-weight="bold" fill="#dc2626">HA: y = 2</text>
        </svg>`,
        options: [
          { label: "A", text: "2" },
          { label: "B", text: "0" },
          { label: "C", text: "-2" },
          { label: "D", text: "∞" }
        ],
        correctIndex: 0,
        explanation: "Degrees of numerator and denominator are equal[cite: 6]:<br>\\[\\lim_{x \\to -\\infty} \\frac{2x^2}{x^2 - 4} = \\lim_{x \\to -\\infty} \\frac{2}{1 - \\frac{4}{x^2}} = \\frac{2}{1} = 2\\]"
      },
      {
        id: 21,
        module: 5,
        moduleName: "Limits at Infinity",
        source: "01 - Limits at Infinity.pdf, Q9",
        title: "Radical Ratio with Negative Infinity Sign Change",
        prompt: "Evaluate the limit[cite: 6]: \\[\\lim_{x \\to -\\infty} \\frac{\\sqrt{2x^2 + 3}}{2x + 3}\\]",
        options: [
          { label: "A", text: "-\\frac{\\sqrt{2}}{2}" },
          { label: "B", text: "\\frac{\\sqrt{2}}{2}" },
          { label: "C", text: "\\sqrt{2}" },
          { label: "D", text: "-\\sqrt{2}" }
        ],
        correctIndex: 0,
        explanation: "For \\(x < 0\\), \\(\\sqrt{x^2} = |x| = -x\\), so \\(x = -\\sqrt{x^2}\\)[cite: 6].<br>Dividing numerator by \\(\\sqrt{x^2}\\) and denominator by \\(-x\\)[cite: 6]:<br>\\[\\lim_{x \\to -\\infty} \\frac{\\frac{\\sqrt{2x^2 + 3}}{\\sqrt{x^2}}}{\\frac{2x + 3}{-(-x)}} = \\lim_{x \\to -\\infty} \\frac{\\sqrt{2 + \\frac{3}{x^2}}}{-2 - \\frac{3}{x}} = -\\frac{\\sqrt{2}}{2}\\]"
      },
      {
        id: 22,
        module: 5,
        moduleName: "Limits at Infinity",
        source: "01 - Limits at Infinity.pdf, Q11",
        title: "Logarithmic Dominance Limit",
        prompt: "Evaluate the limit[cite: 6]: \\[\\lim_{x \\to \\infty} \\left(-\\frac{\\ln x}{x^4} + 1\\right)\\]",
        options: [
          { label: "A", text: "1" },
          { label: "B", text: "0" },
          { label: "C", text: "-∞" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "Polynomial growth dominates logarithmic growth as \\(x \\to \\infty\\)[cite: 6]:<br>\\[\\lim_{x \\to \\infty} \\frac{\\ln x}{x^4} = 0 \\implies 0 + 1 = 1\\]"
      },
      {
        id: 23,
        module: 5,
        moduleName: "Limits at Infinity",
        source: "01 - Limits at Infinity.pdf, Q12",
        title: "Exponential Decay Limit",
        prompt: "Evaluate the limit[cite: 6]: \\[\\lim_{x \\to \\infty} (-e^{-3x} - 1)\\]",
        options: [
          { label: "A", text: "-1" },
          { label: "B", text: "0" },
          { label: "C", text: "-∞" },
          { label: "D", text: "1" }
        ],
        correctIndex: 0,
        explanation: "As \\(x \\to \\infty\\), \\(e^{-3x} = \\frac{1}{e^{3x}} \\to 0\\)[cite: 6]:<br>\\[\\lim_{x \\to \\infty} (-e^{-3x} - 1) = -(0) - 1 = -1\\]"
      },
      {
        id: 24,
        module: 5,
        moduleName: "Limits at Infinity",
        source: "01 - Limits at Infinity.pdf, Q15",
        title: "Oscillating Trigonometric Limit",
        prompt: "Evaluate the limit[cite: 6]: \\[\\lim_{x \\to \\infty} \\cos(2x)\\]",
        options: [
          { label: "A", text: "Does not exist (oscillates)" },
          { label: "B", text: "0" },
          { label: "C", text: "1" },
          { label: "D", text: "-1" }
        ],
        correctIndex: 0,
        explanation: "As \\(x \\to \\infty\\), \\(\\cos(2x)\\) oscillates continuously between \\(-1\\) and \\(1\\) without approaching any single fixed value[cite: 6]. Thus, the limit does not exist[cite: 6]."
      },
      {
        id: 25,
        module: 5,
        moduleName: "Limits at Infinity",
        source: "01 - Limits at Infinity.pdf, Q18",
        title: "Composite Trigonometric Limit",
        prompt: "Evaluate the limit[cite: 6]: \\[\\lim_{x \\to \\infty} x \\cos\\left(\\frac{1}{x}\\right)\\]",
        options: [
          { label: "A", text: "∞" },
          { label: "B", text: "0" },
          { label: "C", text: "1" },
          { label: "D", text: "Does not exist" }
        ],
        correctIndex: 0,
        explanation: "As \\(x \\to \\infty\\), \\(1/x \\to 0\\), which means \\(\\cos(1/x) \\to \\cos(0) = 1\\)[cite: 6].<br>Therefore[cite: 6]:<br>\\[\\lim_{x \\to \\infty} x \\cdot 1 = +\\infty\\]"
      }
    ];

    /* ==========================================================================
       SESSION PERSISTENCE, TABBING & INTERACTIVE ENGINE
       ========================================================================== */
    const STORAGE_KEY = "bm_limits_suite_v1";

    let currentStudentName = "Guest";
    let currentModuleTab = 0; // 0: Theory, 1-5: Modules, 6: Scorecard
    let activeQuestionId = 1;

    let questionStates = ALL_QUESTIONS.map(q => ({
      id: q.id,
      attempts: 0,
      selectedIndex: null,
      isResolved: false,
      isCorrect: false,
      status: "unseen"
    }));

    let audioMuted = false;
    let totalSeconds = 0;
    let timerInterval = null;

    function saveSessionProgress() {
      try {
        const payload = {
          studentName: currentStudentName,
          currentModuleTab: currentModuleTab,
          activeQuestionId: activeQuestionId,
          totalSeconds: totalSeconds,
          questionStates: questionStates
        };
        localStorage.setItem(STORAGE_KEY, JSON.stringify(payload));
      } catch (e) {
        console.warn("Storage save warning", e);
      }
    }

    function checkSavedSession() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (!raw) return;
        const data = JSON.parse(raw);
        if (data && data.studentName) {
          const alertBox = document.getElementById('resumeAlertBox');
          const detailsSpan = document.getElementById('savedSessionDetails');
          const resumeBtn = document.getElementById('resumeSessionBtn');
          const startBtn = document.getElementById('startSessionBtn');
          const input = document.getElementById('studentNameInput');

          input.value = data.studentName;
          const completed = data.questionStates.filter(q => q.isResolved).length;
          detailsSpan.innerText = `Candidate: ${data.studentName} • ${completed}/25 completed • Session Time: ${Math.floor(data.totalSeconds / 60)}m ${data.totalSeconds % 60}s`;
          alertBox.style.display = 'block';
          resumeBtn.style.display = 'inline-block';
          startBtn.innerText = 'Start Fresh Session';
        }
      } catch (e) {
        console.warn("Resume check warning", e);
      }
    }

    const AudioEngine = {
      ctx: null,
      init() {
        if (!this.ctx) {
          this.ctx = new (window.AudioContext || window.webkitAudioContext)();
        }
      },
      playTone(freq, type, duration, delay = 0) {
        if (audioMuted || !this.ctx) return;
        setTimeout(() => {
          try {
            const osc = this.ctx.createOscillator();
            const gain = this.ctx.createGain();
            osc.type = type;
            osc.frequency.setValueAtTime(freq, this.ctx.currentTime);
            gain.gain.setValueAtTime(0.12, this.ctx.currentTime);
            gain.gain.exponentialRampToValueAtTime(0.0001, this.ctx.currentTime + duration);
            osc.connect(gain);
            gain.connect(this.ctx.destination);
            osc.start();
            osc.stop(this.ctx.currentTime + duration);
          } catch (e) {
            console.warn(e);
          }
        }, delay * 1000);
      },
      correct() {
        this.init();
        this.playTone(659.25, 'sine', 0.15, 0);
        this.playTone(880.00, 'sine', 0.25, 0.12);
      },
      incorrect() {
        this.init();
        this.playTone(196.00, 'triangle', 0.2, 0);
        this.playTone(146.83, 'triangle', 0.3, 0.12);
      }
    };

    function startTimer() {
      if (timerInterval) clearInterval(timerInterval);
      timerInterval = setInterval(() => {
        totalSeconds++;
        const mins = String(Math.floor(totalSeconds / 60)).padStart(2, '0');
        const secs = String(totalSeconds % 60).padStart(2, '0');
        document.getElementById('timerChip').innerText = `⏱️ ${mins}:${secs}`;
        saveSessionProgress();
      }, 1000);
    }

    function showToast(msg) {
      const t = document.getElementById('toastMessage');
      t.innerText = msg;
      t.style.display = 'block';
      setTimeout(() => { t.style.display = 'none'; }, 2600);
    }

    function initDirectLogin(isResume = false) {
      const nameInput = document.getElementById('studentNameInput').value.trim() || 'Student';
      
      if (isResume) {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (raw) {
          const data = JSON.parse(raw);
          currentStudentName = data.studentName || nameInput;
          currentModuleTab = data.currentModuleTab || 1;
          activeQuestionId = data.activeQuestionId || 1;
          totalSeconds = data.totalSeconds || 0;
          if (Array.isArray(data.questionStates)) {
            questionStates = data.questionStates;
          }
          showToast(`Welcome back, ${currentStudentName}!`);
        }
      } else {
        currentStudentName = nameInput;
        totalSeconds = 0;
        currentModuleTab = 1;
        activeQuestionId = 1;
        saveSessionProgress();
      }

      document.getElementById('userPill').innerHTML = `<strong>Student: ${currentStudentName}</strong>`;
      document.getElementById('reportStudentBadge').innerHTML = `<strong>Student: ${currentStudentName}</strong>`;
      document.getElementById('loginGateView').style.display = 'none';
      
      AudioEngine.init();
      startTimer();
      switchTopicTab(currentModuleTab || 1);
    }

    function resetStudentProgress() {
      if (confirm("Reset all stored problem attempts and scorecard progress?")) {
        localStorage.removeItem(STORAGE_KEY);
        location.reload();
      }
    }

    function switchTopicTab(tabIdx) {
      currentModuleTab = tabIdx;
      document.querySelectorAll('nav button').forEach((b, idx) => {
        b.classList.toggle('active', idx === tabIdx);
      });

      document.getElementById('viewTheory').classList.toggle('active', tabIdx === 0);
      document.getElementById('viewPractice').classList.toggle('active', tabIdx >= 1 && tabIdx <= 5);
      document.getElementById('viewResults').classList.toggle('active', tabIdx === 6);

      if (tabIdx >= 1 && tabIdx <= 5) {
        // Find first question of this module if active question is outside module
        const moduleQuestions = ALL_QUESTIONS.filter(q => q.module === tabIdx);
        const existsInModule = moduleQuestions.some(q => q.id === activeQuestionId);
        if (!existsInModule && moduleQuestions.length > 0) {
          activeQuestionId = moduleQuestions[0].id;
        }
        renderModulePalette();
        loadQuestion(activeQuestionId);
      } else if (tabIdx === 6) {
        renderScorecard();
      }

      saveSessionProgress();
      if (window.MathJax && window.MathJax.typesetPromise) {
        MathJax.typesetPromise();
      }
    }

    function renderModulePalette() {
      const moduleQuestions = ALL_QUESTIONS.filter(q => q.module === currentModuleTab);
      const grid = document.getElementById('paletteGrid');
      grid.innerHTML = '';

      let solved = 0;
      moduleQuestions.forEach((q) => {
        const state = questionStates.find(s => s.id === q.id);
        if (state && state.isResolved) solved++;

        const btn = document.createElement('button');
        let stateClass = '';
        if (q.id === activeQuestionId) {
          stateClass = 'active';
        } else if (state && state.isResolved) {
          stateClass = 'completed';
        } else if (state && state.status === 'skipped') {
          stateClass = 'skipped';
        }

        btn.className = `palette-btn ${stateClass}`;
        btn.innerText = q.id;
        btn.title = `${q.moduleName}: Q${q.id}`;
        btn.onclick = () => loadQuestion(q.id);
        grid.appendChild(btn);
      });

      document.getElementById('paletteModuleTitle').innerText = `${moduleQuestions[0]?.moduleName || 'Module'}`;
      document.getElementById('paletteCount').innerText = `${solved} / ${moduleQuestions.length} Done`;
    }

    function loadQuestion(qId) {
      activeQuestionId = qId;
      saveSessionProgress();
      renderModulePalette();

      const q = ALL_QUESTIONS.find(item => item.id === qId);
      const state = questionStates.find(s => s.id === qId);
      const card = document.getElementById('activeQuestionCard');

      let optionsHtml = '';
      q.options.forEach((opt, optIdx) => {
        let optClass = '';
        if (state.isResolved) {
          if (optIdx === q.correctIndex) {
            optClass = 'selected-correct';
          } else if (state.selectedIndex === optIdx) {
            optClass = 'selected-wrong';
          }
        }

        optionsHtml += `
          <button class="mcq-option-btn ${optClass}" 
            onclick="handleOptionSelect(${q.id}, ${optIdx})"
            ${state.isResolved ? 'disabled' : ''}>
            <span class="opt-letter">${opt.label}</span>
            <span>\\(${opt.text}\\)</span>
          </button>
        `;
      });

      let feedbackHtml = '';
      if (state.isResolved) {
        feedbackHtml = `
          <div class="feedback-box ${state.isCorrect ? 'correct' : 'incorrect'}">
            <strong>${state.isCorrect ? '✓ Correct Solution' : '✗ Solution Revealed'}</strong> (Option ${q.options[q.correctIndex].label})<br/>
            <div style="margin-top: 8px;">${q.explanation}</div>
          </div>
        `;
      }

      const moduleQuestions = ALL_QUESTIONS.filter(item => item.module === q.module);
      const mIdx = moduleQuestions.findIndex(item => item.id === q.id);
      const prevDisabled = mIdx === 0 ? 'disabled' : '';
      const nextDisabled = mIdx === moduleQuestions.length - 1 ? 'disabled' : '';

      card.innerHTML = `
        <span class="concept-tag">${q.moduleName}</span>
        <span style="font-size:0.8rem; color:var(--text-muted); margin-left:8px;">[${q.source}]</span>
        <h2 style="color:var(--navy-dark); margin: 6px 0 10px 0;">Problem ${q.id}: ${q.title}</h2>
        <div style="margin-top: 8px; line-height: 1.65; font-size:1.02rem;">${q.prompt}</div>
        ${q.svg ? `<div class="svg-container">${q.svg}</div>` : ''}
        <div class="mcq-container">${optionsHtml}</div>
        
        <div style="display:flex; align-items:center; margin-top:12px;">
          <span class="attempts-badge">Attempts: ${state.attempts}/2</span>
          ${!state.isResolved && state.attempts >= 2 ? `
            <button class="btn-reveal" onclick="revealSolution(${q.id})">Reveal Solution</button>
          ` : ''}
        </div>

        ${feedbackHtml}

        <div class="nav-toolbar">
          <button class="btn-nav-action" onclick="navigateModuleQuestion(-1)" ${prevDisabled}>
            ⏮ Previous
          </button>
          <div class="nav-btn-group">
            <button class="btn-nav-action btn-skip" onclick="skipQuestion(${q.id})">
              ⏭ Skip
            </button>
            <button class="btn-nav-action" onclick="navigateModuleQuestion(1)" ${nextDisabled}>
              Next ❯
            </button>
          </div>
        </div>
      `;

      if (window.MathJax && window.MathJax.typesetPromise) {
        MathJax.typesetPromise();
      }
    }

    function handleOptionSelect(qId, optIdx) {
      const q = ALL_QUESTIONS.find(item => item.id === qId);
      const state = questionStates.find(s => s.id === qId);
      if (state.isResolved) return;

      state.selectedIndex = optIdx;
      state.attempts++;

      if (optIdx === q.correctIndex) {
        state.isResolved = true;
        state.isCorrect = true;
        state.status = 'completed';
        AudioEngine.correct();
        showToast("Correct! Response registered.");
      } else {
        AudioEngine.incorrect();
        if (state.attempts >= 2) {
          showToast("2 attempts reached. You can retry or click 'Reveal Solution'.");
        } else {
          showToast("Incorrect option. You have 1 attempt remaining!");
        }
      }

      saveSessionProgress();
      renderModulePalette();
      loadQuestion(qId);
    }

    function revealSolution(qId) {
      const state = questionStates.find(s => s.id === qId);
      state.isResolved = true;
      state.status = 'completed';
      AudioEngine.incorrect();
      showToast("Solution revealed.");
      saveSessionProgress();
      renderModulePalette();
      loadQuestion(qId);
    }

    function navigateModuleQuestion(delta) {
      const moduleQuestions = ALL_QUESTIONS.filter(item => item.module === currentModuleTab);
      const mIdx = moduleQuestions.findIndex(item => item.id === activeQuestionId);
      const target = mIdx + delta;
      if (target >= 0 && target < moduleQuestions.length) {
        loadQuestion(moduleQuestions[target].id);
      }
    }

    function skipQuestion(qId) {
      const state = questionStates.find(s => s.id === qId);
      if (!state.isResolved) {
        state.status = 'skipped';
      }
      showToast(`Problem ${qId} marked as skipped.`);
      navigateModuleQuestion(1);
    }

    function renderScorecard() {
      const container = document.getElementById('completeSolutionsContainer');
      let score = 0;

      ALL_QUESTIONS.forEach((q) => {
        const state = questionStates.find(s => s.id === q.id);
        if (state && state.isCorrect) score++;
      });

      const total = ALL_QUESTIONS.length;
      const pct = Math.round((score / total) * 100);

      document.getElementById('scoreValue').innerText = `${score} / ${total}`;
      document.getElementById('progressBarFill').style.width = `${pct}%`;
      document.getElementById('reportStudentBadge').innerHTML = `<strong>Student: ${currentStudentName}</strong> (${pct}% Solved)`;

      let html = '';
      ALL_QUESTIONS.forEach((q) => {
        const state = questionStates.find(s => s.id === q.id);
        let statusBadge = `<span style="color:var(--text-muted); font-weight:bold;">Unattempted</span>`;

        if (state && state.isResolved) {
          statusBadge = state.isCorrect
            ? `<span style="color:var(--green-ok); font-weight:bold;">✓ Correct (1/1)</span>`
            : `<span style="color:var(--red-fail); font-weight:bold;">✗ Solution Revealed (0/1)</span>`;
        }

        const selText = (state && state.selectedIndex !== null) 
          ? `(${q.options[state.selectedIndex].label}) \\(${q.options[state.selectedIndex].text}\\)` 
          : 'None';

        html += `
          <div class="theory-card">
            <div style="display:flex; justify-content:space-between; align-items:center;">
              <span class="concept-tag">${q.moduleName}</span>
              ${statusBadge}
            </div>
            <h3 style="margin-top:6px;">Problem ${q.id}: ${q.title}</h3>
            <div style="margin: 8px 0; font-size:0.95rem;">${q.prompt}</div>
            ${q.svg ? `<div class="svg-container" style="max-width:320px; margin:12px 0;">${q.svg}</div>` : ''}
            
            <div style="background:#f8fafc; border-left:4px solid var(--brand-blue); padding:14px; margin-top:12px; border-radius:0 6px 6px 0;">
              <strong>Correct Option:</strong> (${q.options[q.correctIndex].label}) \\(${q.options[q.correctIndex].text}\\)<br/>
              <strong>Your Choice:</strong> ${selText}<br/>
              <div style="margin-top:8px;"><strong>Worked Derivation:</strong><br/>${q.explanation}</div>
            </div>
          </div>
        `;
      });

      container.innerHTML = html;
      if (window.MathJax && window.MathJax.typesetPromise) {
        MathJax.typesetPromise();
      }
    }

    document.getElementById('audioToggleBtn').onclick = () => {
      audioMuted = !audioMuted;
      document.getElementById('audioToggleBtn').innerText = audioMuted ? '🔇' : '🔊';
    };

    window.addEventListener('DOMContentLoaded', checkSavedSession);
  </script>
</body>
</html>
