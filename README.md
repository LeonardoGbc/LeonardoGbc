<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Perfil Interativo — ${process.env.GITHUB_USER || 'LeonardoGbc'}</title>
  <style>
    :root{
      --bg:#0b1220;
      --card:#071028;
      --text:#e6eef8;
      --muted:#9fb6d6;
      --accent:#7dd3fc;
    }
    *{box-sizing:border-box}
    body{margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,Arial;background:var(--bg);color:var(--text)}
    .container{max-width:900px;margin:2rem auto;padding:1rem}
    .card{background:linear-gradient(180deg,var(--card),#071124);padding:1rem;border-radius:10px;margin-bottom:1rem;box-shadow:0 6px 18px rgba(2,6,23,.6)}
    .hero{padding:1.2rem}
    h1,h2{margin:0 0 .5rem 0}
    a{color:var(--accent)}
    ul{padding-left:1rem}
    .contact-form label{display:block;margin-bottom:.6rem}
    .contact-form input,.contact-form textarea{width:100%;padding:.5rem;border-radius:6px;border:1px solid #1e2a44;background:#071124;color:var(--text)}
    .contact-form button{margin-top:.6rem;padding:.6rem 1rem;border-radius:8px;border:0;background:var(--accent);color:#022;cursor:pointer}
    .desc{margin:0.2rem 0 0;color:var(--muted);font-size:.95rem}
    .status{margin-top:.5rem;color:var(--muted)}
    .grid{display:grid;gap:1rem;grid-template-columns:1fr 320px;align-items:start}
    .typing{color:#7c3aed;font-weight:600}
    header .links{margin-top:.4rem}
    .repo-list li{margin-bottom:.6rem}
    .quote{font-style:italic;color:var(--muted)}
    footer{margin-top:1rem;color:#7a8ca6;font-size:.9rem;text-align:center}
    @media (max-width:760px){ .grid{grid-template-columns:1fr} }
  </style>
</head>
<body>
  <div class="container">
    <section class="hero card">
      <h1>Olá 👋, eu sou <strong id="name">${process.env.GITHUB_USER || 'LeonardoGbc'}</strong></h1>
      <p class="typing" id="type">Carregando...</p>
      <div class="links">
        <a id="githubLink" href="#" target="_blank">GitHub</a> •
        <a id="siteLink" href="#" target="_blank">Website</a>
      </div>
    </section>

    <main class="grid">
      <div>
        <section class="card">
          <h2>Quote do dia</h2>
          <p id="quote" class="quote">Carregando...</p>
        </section>

        <section class="card">
          <h2>Projetos em destaque</h2>
          <ul id="repos" class="repo-list"><li>Carregando repositórios...</li></ul>
        </section>

        <section class="card">
          <h2>Contato</h2>
          <form id="contactForm" class="contact-form">
            <label>Nome
              <input name="name" required />
            </label>
            <label>Email
              <input name="email" type="email" required />
            </label>
            <label>Mensagem
              <textarea name="message" rows="4" required></textarea>
            </label>
            <button type="submit">Enviar</button>
            <p id="status" class="status" aria-live="polite"></p>
          </form>
        </section>
      </div>

      <aside>
        <section class="card">
          <h3>Sobre mim</h3>
          <p id="about">Front-end developer • React • UI/UX • Também mantenho pequenos serviços backend.</p>
        </section>

        <section class="card">
          <h3>Contatos</h3>
          <p id="email">Email: <span>seu-email@exemplo.com</span></p>
          <p><a id="linkedin" href="#" target="_blank">LinkedIn</a></p>
        </section>
      </aside>
    </main>

    <footer>
      Perfil interativo — servido por <code>app.js</code>
    </footer>
  </div>

  <script>
    // Basic typewriter
    (function(){
      const texts = ['Desenvolvedor • Open Source • Automação', 'Construindo interfaces bonitas', 'Aprendendo Rust e GraphQL']
      let idx = 0, pos = 0, el = document.getElementById('type')
      function type(){ if(pos < texts[idx].length){ el.textContent += texts[idx].charAt(pos++); setTimeout(type,60) } else setTimeout(erase,1200) }
      function erase(){ if(pos>0){ el.textContent = texts[idx].slice(0, --pos); setTimeout(erase,40) } else { idx=(idx+1)%texts.length; setTimeout(type,200) } }
      type()
    })();

    // Fetch quote
    fetch('/api/quote').then(r=>r.json()).then(j=>{ document.getElementById('quote').textContent = j.quote }).catch(()=>{})

    // Fetch repos
    const user = '${process.env.GITHUB_USER || 'LeonardoGbc'}'
    document.getElementById('githubLink').href = 'https://github.com/' + user
    document.getElementById('siteLink').href = 'https://' + user + '.github.io'
    document.getElementById('linkedin').href = '#'
    document.getElementById('email').querySelector('span').textContent = 'seu-email@exemplo.com'

    fetch('/api/repos?user=' + user).then(r=>r.json()).then(list=>{
      const ul = document.getElementById('repos')
      ul.innerHTML = ''
      if(!Array.isArray(list) || list.length === 0){ ul.innerHTML = '<li>Nenhum repositório encontrado.</li>'; return }
      list.forEach(r=>{
        const li = document.createElement('li')
        li.innerHTML = '<a href="'+r.html_url+'" target="_blank">'+r.name+'</a> — '+(r.stargazers_count||0)+' ⭐' +
                       (r.description? '<div class="desc">'+r.description+'</div>' : '')
        ul.appendChild(li)
      })
    }).catch(e=>{ document.getElementById('repos').innerHTML = '<li>Erro ao carregar repositórios.</li>' })

    // Contact form
    const form = document.getElementById('contactForm')
    const statusEl = document.getElementById('status')
    form.addEventListener('submit', async (ev)=>{
      ev.preventDefault()
      statusEl.textContent = 'Enviando...'
      const data = {
        name: form.name.value,
        email: form.email.value,
        message: form.message.value
      }
      try {
        const res = await fetch('/api/contact', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(data)
        })
        if(res.ok){
          statusEl.textContent = 'Mensagem enviada — obrigado!'
          form.reset()
        } else {
          const err = await res.json().catch(()=>({}))
          statusEl.textContent = err.error || 'Falha ao enviar. Tente novamente.'
        }
      } catch (err) {
        statusEl.textContent = 'Erro de rede. Tente novamente.'
      }
    })
  </script>
</body>
</html>`)
})

// API: /api/repos?user=...
app.get('/api/repos', async (req, res) => {
  try {
    const user = req.query.user || process.env.GITHUB_USER || 'LeonardoGbc'
    const headers = { Accept: 'application/vnd.github.v3+json', 'User-Agent': 'profile-app' }
    if (process.env.GITHUB_TOKEN) headers.Authorization = `token ${process.env.GITHUB_TOKEN}`

    const { data } = await axios.get(`https://api.github.com/users/${encodeURIComponent(user)}/repos?per_page=100`, { headers, timeout: 8000 })
    const sorted = (Array.isArray(data) ? data : []).sort((a,b) => (b.stargazers_count||0)-(a.stargazers_count||0)).slice(0,5)
    res.json(sorted.map(r => ({
      name: r.name,
      html_url: r.html_url,
      description: r.description,
      stargazers_count: r.stargazers_count || 0
    })))
  } catch (err) {
    console.error('GET /api/repos error:', err.message || err)
    res.status(500).json({ error: 'Failed to fetch repos' })
  }
})

// API: /api/quote
app.get('/api/quote', async (req, res) => {
  try {
    const { data } = await axios.get('https://api.quotable.io/random', { timeout: 5000 })
    res.json({ quote: `${data.content} — ${data.author}` })
  } catch (err) {
    console.error('GET /api/quote error:', err.message || err)
    res.status(500).json({ quote: 'Keep building. — Unknown' })
  }
})

// API: /api/contact
app.post('/api/contact', async (req, res) => {
  const { name, email, message } = req.body || {}
  if (!name || !email || !message) return res.status(400).json({ error: 'Missing fields' })

  if (process.env.SMTP_HOST && process.env.SMTP_USER && process.env.SMTP_PASS && process.env.TO_EMAIL) {
    try {
      const transporter = nodemailer.createTransport({
        host: process.env.SMTP_HOST,
        port: Number(process.env.SMTP_PORT) || 587,
        secure: (process.env.SMTP_SECURE === 'true'),
        auth: {
          user: process.env.SMTP_USER,
          pass: process.env.SMTP_PASS
        }
      })

      await transporter.sendMail({
        from: `"Perfil" <${process.env.SMTP_USER}>`,
        to: process.env.TO_EMAIL,
        subject: `Contato de ${name} (${email})`,
        text: message,
        html: `<p>${message.replace(/\\n/g,'<br>')}</p><p>From: ${name} — ${email}</p>`
      })

      return res.status(200).json({ ok: true })
    } catch (err) {
      console.error('SMTP error:', err)
      return res.status(500).json({ error: 'Failed to send email' })
    }
  } else {
    // Dev mode: log to console
    console.log('CONTACT (dev mode):', { name, email, message })
    return res.status(202).json({ ok: true, note: 'No SMTP configured; message logged on server.' })
  }
})

app.listen(PORT, () => {
  console.log(\`App listening on http://localhost:\${PORT}\`)
})
