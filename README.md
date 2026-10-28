
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Daniel | Portfólio Interativo</title>

  <style>
    :root {
      --bg: #080d1a;
      --cyan: #67d5ff;
      --purple: #b8a1ff;
      --text: #eef3ff;
      --muted: #aab6d0;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      font-family: "Segoe UI", Arial, sans-serif;
      color: var(--text);
      background:
        radial-gradient(circle at 80% 0%, #25215a, transparent 30%),
        radial-gradient(circle at 10% 30%, #103b52, transparent 28%),
        var(--bg);
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    .wrap {
      width: min(1100px, 92%);
      margin: auto;
    }

    header {
      padding: 22px 0;
      border-bottom: 1px solid #273552;
      position: sticky;
      top: 0;
      z-index: 10;
      background: #080d1ae8;
      backdrop-filter: blur(12px);
    }

    nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 18px;
      flex-wrap: wrap;
    }

    .brand {
      font-weight: 900;
      letter-spacing: 2px;
      color: var(--cyan);
    }

    .navlinks {
      display: flex;
      gap: 18px;
      flex-wrap: wrap;
      color: var(--muted);
      font-size: .92rem;
    }

    .navlinks a:hover {
      color: var(--cyan);
    }

    .hero {
      min-height: 70vh;
      display: grid;
      align-content: center;
      padding: 72px 0;
    }

    .eyebrow {
      color: var(--cyan);
      text-transform: uppercase;
      letter-spacing: 3px;
      font-size: .8rem;
      font-weight: 800;
    }

    h1 {
      font-size: clamp(2.8rem, 8vw, 5.8rem);
      line-height: .98;
      margin: 16px 0;
      letter-spacing: -3px;
    }

    h1 span,
    .section-title span {
      color: var(--cyan);
    }

    .lead {
      color: var(--muted);
      max-width: 680px;
      font-size: 1.15rem;
      line-height: 1.8;
    }

    .actions {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      margin-top: 22px;
    }

    .btn {
      display: inline-flex;
      justify-content: center;
      align-items: center;
      padding: 12px 18px;
      border-radius: 12px;
      background: linear-gradient(120deg, #06b6d4, #818cf8);
      color: #06101f;
      font-weight: 800;
      border: 0;
      cursor: pointer;
      transition: .2s;
    }

    .btn:hover {
      transform: translateY(-2px);
      filter: brightness(1.08);
    }

    .btn.secondary {
      background: #111b31;
      color: var(--text);
      border: 1px solid #344567;
    }

    section {
      padding: 50px 0;
    }

    .section-title {
      font-size: clamp(1.7rem, 4vw, 2.5rem);
      margin: 0 0 22px;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 16px;
    }

    .card {
      background: linear-gradient(150deg, #121e36ef, #0d1528f2);
      border: 1px solid #263654;
      padding: 22px;
      border-radius: 18px;
      box-shadow: 0 16px 50px #0002;
    }

    .card h3 {
      margin-top: 0;
    }

    .card p {
      color: var(--muted);
      line-height: 1.7;
    }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .tag {
      font-size: .85rem;
      border: 1px solid #31516d;
      border-radius: 999px;
      padding: 7px 10px;
      color: #c9efff;
      background: #0c2635;
    }

    .game-top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    .scorebox {
      display: flex;
      gap: 10px;
    }

    .score {
      padding: 9px 12px;
      border-radius: 10px;
      background: #081224;
      border: 1px solid #2d4262;
      color: var(--cyan);
      font-weight: 800;
    }

    #arena {
      margin-top: 18px;
      position: relative;
      height: 270px;
      border: 1px solid #304568;
      border-radius: 14px;
      overflow: hidden;
      background: linear-gradient(#101e39, #0b1326);
      touch-action: manipulation;
    }

    #arena::before {
      content: "";
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(#25385755 1px, transparent 1px),
        linear-gradient(90deg, #25385755 1px, transparent 1px);
      background-size: 28px 28px;
      opacity: .55;
    }

    #target {
      position: absolute;
      display: none;
      width: 48px;
      height: 48px;
      border: 0;
      border-radius: 14px;
      color: #07101f;
      background: linear-gradient(135deg, var(--cyan), var(--purple));
      font-size: 1.35rem;
      font-weight: 900;
      cursor: pointer;
      box-shadow: 0 0 25px #67d5ff55;
      z-index: 2;
    }

    #overlay {
      position: absolute;
      inset: 0;
      display: grid;
      place-items: center;
      text-align: center;
      padding: 20px;
      z-index: 3;
    }

    #overlay p {
      color: var(--muted);
      max-width: 420px;
      line-height: 1.7;
    }

    .small {
      font-size: .9rem;
      color: var(--muted);
    }

    .timeline {
      border-left: 2px solid #31516d;
      padding-left: 20px;
      display: grid;
      gap: 18px;
    }

    .timeline article {
      position: relative;
    }

    .timeline article::before {
      content: "";
      position: absolute;
      width: 10px;
      height: 10px;
      background: var(--cyan);
      border-radius: 50%;
      left: -26px;
      top: 5px;
      box-shadow: 0 0 12px var(--cyan);
    }

    footer {
      padding: 35px 0 55px;
      text-align: center;
      color: var(--muted);
      border-top: 1px solid #263654;
    }

    @media (max-width: 760px) {
      .grid {
        grid-template-columns: 1fr;
      }

      .hero {
        min-height: auto;
        padding: 65px 0;
      }

      h1 {
        letter-spacing: -1.5px;
      }

      .navlinks {
        gap: 12px;
      }

      #arena {
        height: 240px;
      }
    }
  </style>
</head>

<body>

<header>
  <div class="wrap">
    <nav>
      <a class="brand" href="#inicio">DANIEL.DEV</a>

      <div class="navlinks">
        <a href="#sobre">Sobre</a>
        <a href="#skills">Tecnologias</a>
        <a href="#jogo">Mini game</a>
        <a href="#projetos">Projetos</a>
        <a href="#contato">Contato</a>
      </div>
    </nav>
  </div>
</header>

<main class="wrap">

  <section class="hero" id="inicio">
    <div class="eyebrow">
      Análise e Desenvolvimento de Sistemas · Unicid
    </div>

    <h1>Olá, eu sou<br><span>Daniel.</span></h1>

    <p class="lead">
      Estou construindo minha jornada na tecnologia com curiosidade,
      prática e vontade de transformar ideias em projetos reais.
      Explore a página e teste seu reflexo no mini game!
    </p>

    <div class="actions">
      <a class="btn" href="#jogo">🎮 Jogar mini game</a>

      <a class="btn secondary"
         href="https://github.com/danielgabrieleduardo2020-maker"
         target="_blank" rel="noreferrer">
        Ver meu GitHub ↗
      </a>
    </div>
  </section>

  <section id="sobre">
    <div class="eyebrow">01 / Quem sou</div>

    <h2 class="section-title">
      Aprender. Praticar. <span>Evoluir.</span>
    </h2>

    <div class="card">
      <p>
        Sou estudante de <strong>Análise e Desenvolvimento de Sistemas
        na Unicid</strong>, desenvolvendo conhecimentos em lógica de
        programação, desenvolvimento web e modelagem de dados.
      </p>

      <p>
        Minha experiência como auxiliar de produção na Artshow fortalece
        minha organização, responsabilidade e trabalho em equipe.
        Uso este espaço para compartilhar estudos e acompanhar minha evolução.
      </p>
    </div>
  </section>

  <section id="skills">
    <div class="eyebrow">02 / Tecnologias</div>

    <h2 class="section-title">
      Ferramentas que estou <span>explorando</span>
    </h2>

    <div class="grid">
      <article class="card">
        <h3>🌐 Desenvolvimento web</h3>
        <p>Estrutura, estilo e interatividade para páginas.</p>
        <div class="tags">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
          <span class="tag">JavaScript</span>
        </div>
      </article>

      <article class="card">
        <h3>⌨️ Programação</h3>
        <p>Prática de lógica, algoritmos e resolução de problemas.</p>
        <div class="tags">
          <span class="tag">C</span>
          <span class="tag">Lógica</span>
        </div>
      </article>

      <article class="card">
        <h3>🗄️ Dados e ferramentas</h3>
        <p>Organização de código e fundamentos de banco de dados.</p>
        <div class="tags">
          <span class="tag">MySQL / SQL</span>
          <span class="tag">Git</span>
          <span class="tag">GitHub</span>
          <span class="tag">VS Code</span>
        </div>
      </article>
    </div>
  </section>

  <!-- JOGO INTEGRADO À APRESENTAÇÃO -->
  <section id="jogo">
    <div class="eyebrow">03 / Pausa para jogar</div>

    <h2 class="section-title">
      Reflexo <span>em código</span>
    </h2>

    <div class="card">
      <div class="game-top">
        <div>
          <h3>⚡ Clique no alvo!</h3>
          <div class="small">
            Você tem 20 segundos. Clique no quadrado brilhante
            o máximo que conseguir.
          </div>
        </div>

        <div class="scorebox">
          <div class="score">
            Pontos: <span id="score">0</span>
          </div>

          <div class="score">
            Recorde: <span id="best">0</span>
          </div>
        </div>
      </div>

      <div id="arena" aria-label="Área do jogo">
        <button id="target" aria-label="Clique no alvo">✦</button>

        <div id="overlay">
          <div>
            <h3 id="gameTitle">Pronto para o desafio?</h3>

            <p id="gameText">
              Clique em iniciar e acerte o alvo antes que o tempo acabe.
              Funciona com mouse ou toque.
            </p>

            <button class="btn" id="start">Iniciar jogo</button>
          </div>
        </div>
      </div>

      <p class="small">
        Dica: o alvo muda de lugar a cada clique.
        Tente superar seu próprio recorde!
      </p>
    </div>
  </section>

  <section id="projetos">
    <div class="eyebrow">04 / Projetos e estudos</div>

    <h2 class="section-title">
      Construindo com <span>prática</span>
    </h2>

    <div class="grid">
      <article class="card">
        <h3>🧩 Desenvolvimento web</h3>
        <p>
          Páginas de estudo com HTML e CSS, praticando estrutura,
          layout e responsividade.
        </p>

        <a class="btn secondary"
           href="https://github.com/danielgabrieleduardo2020-maker?tab=repositories"
           target="_blank" rel="noreferrer">
          Explorar repositórios ↗
        </a>
      </article>

      <article class="card">
        <h3>💻 Lógica em C</h3>
        <p>
          Exercícios para praticar variáveis, condições, repetições
          e pensamento computacional.
        </p>

        <a class="btn secondary"
           href="https://github.com/danielgabrieleduardo2020-maker?tab=repositories"
           target="_blank" rel="noreferrer">
          Ver códigos ↗
        </a>
      </article>

      <article class="card">
        <h3>🗃️ Modelagem de dados</h3>
        <p>
          Estudos de entidades, relacionamentos, regras de negócio
          e consultas SQL.
        </p>

        <a class="btn secondary"
           href="https://github.com/danielgabrieleduardo2020-maker?tab=repositories"
           target="_blank" rel="noreferrer">
          Ver estudos ↗
        </a>
      </article>
    </div>
  </section>

  <section>
    <div class="eyebrow">05 / Minha jornada</div>

    <h2 class="section-title">
      Um passo de cada <span>vez</span>
    </h2>

    <div class="timeline">
      <article>
        <strong>Fundamentos</strong>
        <p class="small">
          Praticando lógica de programação e algoritmos.
        </p>
      </article>

      <article>
        <strong>Desenvolvimento web</strong>
        <p class="small">
          Criando páginas com HTML, CSS e JavaScript.
        </p>
      </article>

      <article>
        <strong>Projetos e colaboração</strong>
        <p class="small">
          Organizando repositórios e documentando aprendizados no GitHub.
        </p>
      </article>
    </div>
  </section>

  <section id="contato">
    <div class="eyebrow">06 / Conexão</div>

    <h2 class="section-title">
      Vamos trocar <span>ideias?</span>
    </h2>

    <div class="card">
      <p>
        Estou aberto a aprender com a comunidade, compartilhar conhecimento
        e conhecer pessoas da área de tecnologia.
      </p>

      <div class="actions">
        <a class="btn"
           href="https://github.com/danielgabrieleduardo2020-maker"
           target="_blank" rel="noreferrer">
          GitHub ↗
        </a>

        <a class="btn secondary"
           href="https://www.linkedin.com/"
           target="_blank" rel="noreferrer">
          LinkedIn ↗
        </a>
      </div>
    </div>
  </section>

</main>

<footer>
  <div class="wrap">
    Feito com HTML, CSS e JavaScript ·
    <span style="color:var(--cyan)">
      Construindo meu caminho na tecnologia, um projeto de cada vez. 🚀
    </span>
  </div>
</footer>

<script>
  const arena = document.getElementById("arena");
  const target = document.getElementById("target");
  const overlay = document.getElementById("overlay");
  const startBtn = document.getElementById("start");
  const scoreEl = document.getElementById("score");
  const bestEl = document.getElementById("best");
  const titleEl = document.getElementById("gameTitle");
  const textEl = document.getElementById("gameText");

  let score = 0;
  let timeLeft = 20;
  let running = false;
  let timerId = null;

  let best = Number(
    localStorage.getItem("danielReflexoBest") || 0
  );

  bestEl.textContent = best;

  // Move o alvo para uma posição aleatória.
  function moveTarget() {
    const maxX = Math.max(
      0,
      arena.clientWidth - target.offsetWidth - 12
    );

    const maxY = Math.max(
      0,
      arena.clientHeight - target.offsetHeight - 12
    );

    target.style.left = (6 + Math.random() * maxX) + "px";
    target.style.top = (6 + Math.random() * maxY) + "px";
  }

  // Encerra o jogo e atualiza o recorde.
  function finishGame() {
    running = false;
    clearInterval(timerId);

    target.style.display = "none";
    overlay.style.display = "grid";

    titleEl.textContent =
      `Fim de jogo! Você fez ${score} ponto${score === 1 ? "" : "s"}.`;

    if (score > best) {
      best = score;

      localStorage.setItem(
        "danielReflexoBest",
        String(best)
      );

      bestEl.textContent = best;
      textEl.textContent =
        "Novo recorde! Mandou bem. Quer tentar de novo?";
    } else {
      textEl.textContent =
        "Tente novamente para superar seu recorde.";
    }

    startBtn.textContent = "Jogar novamente";
  }

  // Inicia ou reinicia a partida.
  function startGame() {
    clearInterval(timerId);

    score = 0;
    timeLeft = 20;
    running = true;

    scoreEl.textContent = score;
    overlay.style.display = "none";
    target.style.display = "block";

    target.style.width = "48px";
    target.style.height = "48px";

    moveTarget();
    startBtn.blur();

    titleEl.textContent = "Tempo restante: 20s";

    timerId = setInterval(() => {
      timeLeft--;

      titleEl.textContent =
        `Tempo restante: ${timeLeft}s`;

      if (timeLeft <= 0) {
        finishGame();
      }
    }, 1000);
  }

  // Cada clique no alvo vale um ponto.
  target.addEventListener("click", () => {
    if (!running) return;

    score++;
    scoreEl.textContent = score;

    // O alvo diminui gradualmente conforme a pontuação aumenta.
    const size = Math.max(
      30,
      48 - Math.floor(score / 5) * 2
    );

    target.style.width = size + "px";
    target.style.height = size + "px";

    moveTarget();
  });

  startBtn.addEventListener("click", startGame);

  window.addEventListener("resize", () => {
    if (running) {
      moveTarget();
    }
  });
</script>

</body>
</html>
