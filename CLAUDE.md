# CLAUDE.md — Top Glamour Viagens · Formulário de Captura de Leads

## Sobre o Projeto

Landing page de captura de leads para eventos presenciais da **Top Glamour Viagens** (agência de viagens).
Substitui formulário em papel por QR Code → formulário mobile → Google Sheets → Octadesk.

## Paleta de Cores CANÔNICA

```css
--navy:      #1E2459   /* azul profundo — fundo e headers */
--gold:      #D4912C   /* âmbar — destaques, CTAs, setas */
--warm-gray: #B7AAAA   /* cinza quente — textos secundários */
--cream:     #FDFBF8   /* fundo do card do formulário */
```

> O arquivo `fontes_cliente/Identidade Visual - Paleta de cores.txt` contém erros de HEX.
> Usar SEMPRE as variáveis CSS acima como referência canônica.

## Regras de Copy

- **NUNCA** usar ` —` (em dash) em frases visíveis ao usuário. Substituir por ponto ou vírgula.
- **NUNCA** usar exclamações em headlines. Tom: confiante e direto.
- `@topglamourviagens` aparece em negrito azul no subtítulo do formulário.
- Seguir os princípios da skill `copywriting` para qualquer novo texto.

## Regras de Design

- Logo mínima: **80px** de altura. Tela de sucesso: **100px**.
- Mobile-first. Inputs com `font-size: 1rem` (evita auto-zoom iOS).
- Sem `maximum-scale` no viewport.
- Áreas de toque: mínimo 48px de altura.
- Referência visual: screenshot do site `topglamourviagens.com.br` (azul profundo + âmbar).

## Arquitetura

| Arquivo | Função |
|---|---|
| `index.html` | Landing page completa (form + tela de sucesso) |
| `style.css` | CSS com variáveis de paleta e layout mobile-first |
| `script.js` | Validação, máscara WhatsApp, localStorage buffer, fetch no-cors |
| `gas/Code.gs` | Apps Script Web App (backend → Google Sheets) |
| `forms/backup-form-config.md` | Passo a passo Google Forms backup |
| `docs/qrcode-instrucoes.md` | Guia de geração e impressão do QR Code |

## Google Apps Script

- URL do Web App: `https://script.google.com/macros/s/AKfycbzYM0kC63PqHK43fpDtxyfWx4DyoKgUNDazta-R2PLKlvb2mLp5TbMy_IGfSPHbGFYgfA/exec`
- Token anti-spam: `tg2026feira` (deve coincidir em `script.js` e `Code.gs`)
- Planilha: `Leads - Top Glamour Feira 2026-03-29`
- Qualquer mudança no `Code.gs` exige **redeploy** como nova versão

## Segurança e Qualidade

- `LockService.getScriptLock()` no GAS evita IDs duplicados em submits simultâneos
- `localStorage` salva cada lead antes do envio (seguro contra falha 4G)
- `rel="noopener noreferrer"` obrigatório em todos os `target="_blank"`
- Rodar a skill `requesting-code-review` antes de qualquer mudança significativa

## Links da Tela de Sucesso

- Instagram: `https://instagram.com/topglamourviagens`
- Site: `https://topglamourviagens.com.br/`
- WhatsApp atendimento: `https://wa.me/557184688744`
- Grupos por cidade: Salvador, Aracaju, Foz do Iguaçu, São Paulo, Brasília/Goiânia, Rio de Janeiro, Recife/João Pessoa, Curitiba

## Próximos Passos (deploy)

1. Redeploy do Apps Script (Code.gs foi atualizado)
2. Push para GitHub → ativar GitHub Pages
3. Encurtar URL com bit.ly
4. Gerar QR Code com cor `#1E2459` em qrcode-monkey.com
5. Salvar link do Google Forms backup no celular da promoter
