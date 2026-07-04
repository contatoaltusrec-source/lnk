# Diretrizes de design — página de pre-save personalizada (Altus)

Especificação de **design** para um chat/LLM construir uma página de pre-save
(smartlink) com visual exclusivo. O chat deve **entregar o `index.html` pronto**:
um único arquivo completo e autossuficiente (todo o CSS e JS inline).

Os dados da faixa (título, artista, capa, ID do Spotify, plataformas) vêm no
brief gerado pelo painel — cole junto com estas diretrizes.

---

## Regras visuais (obrigatórias)

- **Tema escuro.** Fundo `#000` / `#0a0a0a`. Texto claro.
- **Fonte:** Space Grotesk (Google Fonts).
- **SEM logo da Altus Records.**
- **`<title>` da página:** `"<Título> - <Artista>"` (hífen único).
- **Capa em destaque** com um **botão de play sobreposto**.
- **Botões de plataforma**, um por linha, cada um com o texto de call-to-action.
- **Ícones oficiais (somente ícone)** das plataformas, em `/logos/icons/`:
  `spotify.svg`, `deezer.svg`, `tiktok.svg`, `amazon.svg`, `appleMusic.png`.
  Para plataformas sem ícone na pasta, use o nome em texto.
  (Logos completos com texto, se preferir, ficam em `/logos/<id>.svg`.)
- **Rodapé** com as redes da Altus + o copyright (bloco pronto abaixo).
- **Botão de play** aciona um player do Spotify **escondido** via Spotify iframe
  Embed API (sem credenciais) — trecho pronto abaixo.

---

## `<head>` recomendado

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title><!-- Título - Artista --></title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;700&display=swap" rel="stylesheet">
```

---

## Rodapé oficial (use exatamente)

```html
<footer style="display:flex;flex-direction:column;align-items:center;gap:15px;padding:34px 20px 20px;">
  <div class="socials" style="display:flex;gap:22px;">
    <a href="https://www.instagram.com/altusrec/" target="_blank" rel="noopener" title="Instagram" style="color:rgba(255,255,255,0.4);display:inline-flex;"><svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="5"/><circle cx="17.5" cy="6.5" r="1.2" fill="currentColor" stroke="none"/></svg></a>
    <a href="https://open.spotify.com/user/31iwbmwr6jsnr6hatmlmroumf444" target="_blank" rel="noopener" title="Spotify" style="color:rgba(255,255,255,0.4);display:inline-flex;"><svg width="19" height="19" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.4 0 0 5.4 0 12s5.4 12 12 12 12-5.4 12-12S18.66 0 12 0zm5.521 17.34c-.24.359-.66.48-1.021.24-2.82-1.74-6.36-2.101-10.561-1.141-.418.122-.779-.179-.899-.539-.12-.421.18-.78.54-.9 4.56-1.021 8.52-.6 11.64 1.32.42.18.479.659.301 1.02zm1.44-3.3c-.301.42-.841.6-1.262.3-3.239-1.98-8.159-2.58-11.939-1.38-.479.12-1.02-.12-1.14-.6-.12-.48.12-1.021.6-1.141C9.6 9.9 15 10.561 18.72 12.84c.361.181.54.78.241 1.2zm.12-3.36C15.24 8.4 8.82 8.16 5.16 9.301c-.6.179-1.2-.181-1.38-.721-.18-.601.18-1.2.72-1.381 4.26-1.26 11.28-1.02 15.721 1.621.539.3.719 1.02.419 1.56-.299.421-1.02.599-1.559.3z"/></svg></a>
    <a href="https://discord.gg/yqyPjRggpZ" target="_blank" rel="noopener" title="Discord" style="color:rgba(255,255,255,0.4);display:inline-flex;"><svg width="19" height="19" viewBox="0 0 24 24" fill="currentColor"><path d="M20.317 4.369a19.79 19.79 0 00-4.885-1.515.074.074 0 00-.079.037c-.211.375-.445.864-.608 1.249a18.27 18.27 0 00-5.487 0 12.64 12.64 0 00-.617-1.249.077.077 0 00-.079-.037A19.736 19.736 0 003.677 4.369a.07.07 0 00-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 00.031.057 19.9 19.9 0 005.993 3.03.078.078 0 00.084-.028 14.09 14.09 0 001.226-1.994.076.076 0 00-.041-.106 13.107 13.107 0 01-1.872-.892.077.077 0 01-.008-.128c.126-.094.252-.192.372-.291a.074.074 0 01.077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 01.078.009c.12.099.246.198.373.292a.077.077 0 01-.006.127 12.3 12.3 0 01-1.873.891.077.077 0 00-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 00.084.028 19.839 19.839 0 006.002-3.03.077.077 0 00.032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 00-.031-.03zM8.02 15.331c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"/></svg></a>
    <a href="mailto:contato@altusrec.com.br" title="Email" style="color:rgba(255,255,255,0.4);display:inline-flex;"><svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="M22 4L12 13 2 4"/></svg></a>
  </div>
  <div style="color:rgba(255,255,255,0.35);font-size:12px;">&copy; 2026 Altus Entertainment. Todos os direitos reservados.</div>
</footer>
```

---

## Play sem credencial (Spotify iframe Embed API)

Coloque um `<div id="sp-embed"></div>` escondido e um botão de play sobre a capa
(`id="playBtn"`). `TRACK_ID` é o id da faixa no Spotify.

O iframe deve ficar **invisível**. O Spotify move o iframe pra fora do container
(direto no `<body>`), então esconda pelo `src`:

```css
iframe[src*="open.spotify.com/embed"] {
  position: fixed !important; left: -10000px !important; top: -10000px !important;
  width: 340px !important; height: 80px !important;
  opacity: 0 !important; pointer-events: none !important; z-index: -9999 !important;
}
```

```html
<div id="sp-embed"></div>
<script src="https://open.spotify.com/embed/iframe-api/v1" async></script>
<script>
  const TRACK_ID = 'COLE_O_ID_DA_FAIXA_AQUI';
  let ctrl = null, api = null, pending = null;
  window.onSpotifyIframeApiReady = (a) => { api = a; if (pending) make(pending); };
  function make(uri) {
    api.createController(document.getElementById('sp-embed'), { uri, width: '100%', height: 80 }, (c) => {
      ctrl = c;
      c.addListener('playback_update', (e) => {
        const d = (e && e.data) || {};
        // fim da prévia: o embed manda position === duration sem "pause"
        const ended = d.duration > 0 && d.position >= d.duration;
        const playing = d.isPaused === false && !ended;
        document.getElementById('playBtn').classList.toggle('playing', playing);
      });
    });
  }
  (api ? make : (u => pending = u))('spotify:track:' + TRACK_ID);
  document.getElementById('playBtn').addEventListener('click', () => { if (ctrl) ctrl.togglePlay(); });
</script>
```

---

## Entrega

Entregue **apenas o `index.html` completo e pronto** — nada além do arquivo.
