---
tags: [projeto, arquitetura, técnico]
---

# Arquitetura do Sistema

## Fluxo principal

QR Code → bit.ly/topglamour2026 → GitHub Pages → GAS Web App → Google Sheets

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | Landing page (formulário + tela de sucesso) |
| `style.css` | CSS mobile-first, paleta #1E2459/#D4912C |
| `script.js` | Validação, máscara WhatsApp, localStorage, fetch no-cors |
| `gas/Code.gs` | Apps Script backend (Google Sheets) |

## Decisões técnicas

- `fetch()` com `mode: no-cors` — contorna redirect do GAS sem preflight
- `localStorage` buffer — seguro contra falha de rede 4G
- `LockService` no GAS — evita IDs duplicados em submits simultâneos
- Token `tg2026feira` — anti-spam server-side

## GAS

- URL: `https://script.google.com/macros/s/AKfycbzYM0kC63PqHK43fpDtxyfWx4DyoKgUNDazta-R2PLKlvb2mLp5TbMy_IGfSPHbGFYgfA/exec`
- Token: `tg2026feira`
- Planilha: `Leads - Top Glamour Feira 2026-03-29`
- Qualquer mudança no Code.gs exige redeploy como nova versão
