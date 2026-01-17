# roman-batalov.github.io
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Роман Баталов</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    :root{
      --bg:#000;
      --fg:#fff;
      --accent:#c792ea;
    }
    *{box-sizing:border-box;margin:0;padding:0;}
    body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Arial,sans-serif;background:var(--bg);color:var(--fg);min-height:100vh;display:flex;flex-direction:column;align-items:center;padding:4rem 2rem 2rem;line-height:1.45;overflow:hidden;position:relative;}
    
    /* дикий глитч-фон */
    body::before{
      content:'';position:fixed;inset:0;
      background:
        repeating-linear-gradient(0deg,var(--bg) 0 1px,transparent 1px 3px),
        repeating-linear-gradient(90deg,var(--accent) 0 1px,transparent 1px 3px);
      background-size:100% 4px,4px 100%;
      mix-blend-mode:difference;
      opacity:.18;
      animation:scan 2s linear infinite;
      z-index:0;
    }
    @keyframes scan{
      0%{transform:translateY(0);}
      100%{transform:translateY(8px);}
    }
    
    /* rgb-развод */
    body::after{
      content:'';position:fixed;inset:-100px;
      background:linear-gradient(45deg,#ff00ff 0%,#00ffff 50%,#ff00ff 100%);
      mix-blend-mode:multiply;
      filter:blur(80px);
      opacity:.08;
      animation:rgbShift 4s steps(8,end) infinite;
      z-index:0;
    }
    @keyframes rgbShift{
      0%{transform:translate(0,0);}
      25%{transform:translate(5%,-5%);}
      50%{transform:translate(-5%,5%);}
      75%{transform:translate(5%,5%);}
      100%{transform:translate(0,0);}
    }
    
    header,main,footer{position:relative;z-index:1;}
    
    header{width:100%;max-width:700px;text-align:left;margin-bottom:4rem;animation:flicker 2s infinite;}
    h1{font-size:2.2rem;letter-spacing:.05em;}
    nav{display:flex;gap:1.2rem;margin-top:1rem;}
    nav a{color:var(--fg);text-decoration:none;font-size:1rem;position:relative;}
    nav a::after{content:'';position:absolute;left:0;bottom:-4px;width:0;height:2px;background:var(--accent);transition:.3s;}
    nav a:hover::after{width:100%;}
    main{width:100%;max-width:700px;position:relative;}
    
    /* контейнеры секций с плавным переходом */
    .section-wrap{
      position:absolute;top:0;left:0;width:100%;
      opacity:0;transform:translateY(20px);
      transition:opacity .6s ease,transform .6s ease;
      pointer-events:none;
    }
    .section-wrap.active{
      opacity:1;transform:translateY(0);
      pointer-events:auto;position:relative;
    }
    
    @keyframes flicker{
      0%,100%{opacity:1;}
      50%{opacity:.85;}
    }
    .glitch{display:inline-block;position:relative;}
    .glitch::before,.glitch::after{content:attr(data-text);position:absolute;top:0;left:0;width:100%;height:100%;}
    .glitch::before{animation:glitch-1 .15s infinite;color:var(--accent);z-index:-1;}
    .glitch::after{animation:glitch-2 .2s infinite;color:var(--fg);z-index:-2;}
    @keyframes glitch-1{
      0%,100%{clip:rect(0,900px,0,0);transform:translate(0);}
      20%{clip:rect(20px,900px,90px,0);transform:translate(-3px);}
      40%{clip:rect(50px,900px,10px,0);transform:translate(3px);}
      60%{clip:rect(80px,900px,30px,0);transform:translate(-2px);}
      80%{clip:rect(10px,900px,70px,0);transform:translate(2px);}
    }
    @keyframes glitch-2{
      0%,100%{clip:rect(0,900px,0,0);transform:translate(0);}
      20%{clip:rect(60px,900px,40px,0);transform:translate(3px);}
      40%{clip:rect(30px,900px,80px,0);transform:translate(-3px);}
      60%{clip:rect(10px,900px,50px,0);transform:translate(2px);}
      80%{clip:rect(70px,900px,20px,0);transform:translate(-2px);}
    }
    .photo{width:140px;height:140px;border-radius:50%;object-fit:cover;margin:1.5rem 0;border:2px solid var(--accent);filter:contrast(1.2) saturate(1.3);}
    footer{margin-top:auto;padding-top:3rem;font-size:.8rem;color:#555;animation:flicker 3s infinite;}
    
    /* неоновые цветы */
    #flowers{
      position:fixed;inset:0;pointer-events:none;z-index:2;
      overflow:hidden;
    }
    .flower{
      position:absolute;bottom:-250px;width:60px;height:250px;
      transform-origin:bottom center;
      animation:bloom 4s ease-out forwards;
    }
    .flower::before{
      content:'';
      position:absolute;bottom:0;left:50%;transform:translateX(-50%);
      width:8px;height:100%;background:linear-gradient(to top,var(--accent),transparent);
      border-radius:4px;
    }
    .petals{
      position:absolute;bottom:90px;left:50%;transform:translateX(-50%);
      width:60px;height:60px;
      background:radial-gradient(circle,#ff00ff 0%,#00ffff 100%);
      border-radius:50%;
      box-shadow:0 0 20px #ff00ff,0 0 40px #00ffff;
      animation:petal-glow 2s ease-in-out infinite alternate;
    }
    @keyframes bloom{
      0%{transform:translateY(250px) scale(.3);opacity:0;}
      100%{transform:translateY(0) scale(1);opacity:1;}
    }
    @keyframes petal-glow{
      0%{box-shadow:0 0 20px #ff00ff,0 0 40px #00ffff;}
      100%{box-shadow:0 0 30px #ff00ff,0 0 60px #00ffff;}
    }
  </style>
</head>
<body>
  <div id="flowers"></div>

  <header>
    <h1 class="glitch hidden" data-text="Роман Баталов">Роман Баталов</h1>
    <nav>
      <a href="#about">Обо мне</a>
      <a href="#projects">Проекты</a>
      <a href="#contact">Контакты</a>
    </nav>
  </header>

  <main>
    <div class="section-wrap active" id="wrap-about">
      <section id="about">
        <p>Ты здесь не случайно.</p>
        <img src="photo.jpg" alt="" class="photo">
        <p>Достаточно.</p>
        <p>Не переношу крики и мужские духи. Утро начинаю с зеркала — иначе день не считается. Фильм, которому доверяю настроение: <em>The Substance</em>. Если бы никто не узнал — переехал бы. Люблю жилой комплекс PRIVILEGIA: считается никому не нужным, а мне нравится. На столе всегда разбросаны учебники. Когда исчезну, пусть вспомнят <em>Crystal Castles</em>.</p>
      </section>
    </div>

    <div class="section-wrap" id="wrap-projects">
      <section id="projects">
        <p>Пока пусто. Когда появится — здесь будет.</p>
      </section>
    </div>

    <div class="section-wrap" id="wrap-contact">
      <section id="contact">
        <p><a href="https://t.me/SASALELES90" target="_blank" style="color:var(--accent);">Телеграм-канал</a></p>
        <p><a href="https://open.spotify.com/playlist/2Q61GWHMxVHSXNeSUVSXMd?si=UxZPP6eATRKhGNPLkAjNXQ&pi=zG2InzVgR3O_g" target="_blank" style="color:var(--accent);">Spotify-плейлист</a></p>
      </section>
    </div>
  </main>

  <footer>© 2026 Роман Баталов</footer>

  <script>
    // неоновые цветы при заходе
    const flowersBox=document.getElementById('flowers');
    const colors=['#ff00ff','#00ffff','#ff0080','#80ff00','#c792ea'];
    for(let i=0;i<7;i++){
      const f=document.createElement('div');f.className='flower';
      f.style.left=Math.random()*100+'%';
      f.style.animationDelay=(Math.random()*2)+'s';
      const p=document.createElement('div');p.className='petals';
      p.style.background=`radial-gradient(circle,${colors[i%5]} 0%,${colors[(i+2)%5]} 100%)`;
      f.appendChild(p);flowersBox.appendChild(f);
    }

    // показать имя после цветов
    setTimeout(()=>{
      document.querySelector('h1').classList.remove('hidden');
    },2500);

    // плавные переходы между вкладками
    const navLinks=document.querySelectorAll('nav a');
    const wraps=document.querySelectorAll('.section-wrap');
    navLinks.forEach(link=>{
      link.addEventListener('click',e=>{
        e.preventDefault();
        const id=link.getAttribute('href').slice(1);
        wraps.forEach(w=>w.classList.remove('active'));
        document.getElementById('wrap-'+id).classList.add('active');
      });
    });
  </script>
</body>
</html>
