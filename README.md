# Site — Dr. Arthur Dal Cortivo · Ortopedia Pediátrica

Site institucional do **Dr. Arthur Cartonilho Dal Cortivo** (Ortopedia e Traumatologia · Ortopedia Pediátrica · CRM 10898).

🔗 **Acesse:** https://willpine1992.github.io/SITE-ARTHUR/

Página única, estática (HTML + CSS + JS puros, sem build), com design inspirado na Apple e efeito de **vidro líquido** (liquid glass).

---

## Estrutura

```
.
├── index.html          # site inteiro (HTML, CSS e JS inline)
├── assets/
│   ├── logo-mark.png   # monograma "AC" + árvore, fundo transparente
│   ├── logo-full.png   # logo completa com textos, fundo transparente
│   ├── xray-quadril.webp
│   ├── xray-maos.webp
│   └── xray-pe.webp    # radiografias tingidas na cor da marca
└── README.md
```

## Seções

| Âncora       | Conteúdo                                                        |
|--------------|-----------------------------------------------------------------|
| `#inicio`    | Hero com chamada principal, CRM e cartão de vidro com a logo     |
| (faixa)      | Letreiro rolante com as condições tratadas                       |
| `#sobre`     | Apresentação do médico, credenciais e imagem de raio-X           |
| `#atuacao`   | Grade "bento" com as áreas de atuação                           |
| (sinais)     | Quando procurar o ortopedista pediátrico                         |
| `#consulta`  | Como funciona a consulta (3 passos)                              |
| `#duvidas`   | Perguntas frequentes (acordeão)                                  |
| `#contato`   | WhatsApp, endereço, telefone, Instagram e horário                |

## Identidade visual

Paleta extraída da logo (variáveis CSS em `:root`, no topo do `<style>`):

| Token         | Cor       | Uso                                  |
|---------------|-----------|--------------------------------------|
| `--petroleo`  | `#1F4A5E` | cor principal, botões, ícones         |
| `--petroleo-900` | `#122F3D` | gradientes escuros                |
| `--folha`     | `#5B93A8` | azul das folhas, destaques            |
| `--cobre`     | `#B07F55` | letra "A", detalhes e selos           |
| `--tronco`    | `#7A5440` | marrom do tronco                      |
| `--papel`     | `#EEECE8` | fundo claro                           |

- **Tipografia:** fonte do sistema Apple (SF Pro) com fallback para Inter.
- **Tema claro/escuro:** segue o sistema do visitante; o botão da lua alterna manualmente (preferência salva no navegador).

## Efeito de vidro líquido

Qualquer elemento com a classe `.glass` vira um painel de vidro:

- `backdrop-filter: blur() saturate()` — desfoque e saturação do que está atrás;
- `::before` — borda especular (brilho nas bordas);
- `::after` — reflexo de luz que segue o cursor (variáveis `--mx` / `--my`, atualizadas via JS);
- `.refract` — adiciona **refração real** usando o filtro SVG `#liquid` (`feTurbulence` + `feDisplacementMap`). Só é ativado no Chrome/Edge (classe `.liquid` no `<html>`); Safari e Firefox recebem o vidro fosco normal.

Os "blobs" coloridos animados no fundo (`.ambient`) são o que dá vida ao vidro — sem algo atrás, o efeito não aparece.

Animações respeitam `prefers-reduced-motion`.

## ✏️ O que falta preencher

Procure por `TODO` no `index.html`:

1. **WhatsApp** — trocar `5592000000000` no link `wa.me` pelo número real (formato: 55 + DDD + número, só dígitos).
2. **Endereço do consultório** — texto e link (pode ser link do Google Maps).
3. **Telefone** — texto e `href="tel:+55..."`.
4. **Instagram** — usuário e link.
5. **Horário de atendimento.**
6. **RQE** — a Resolução CFM nº 2.336/2023 exige o número do RQE ao anunciar especialidade. Adicionar ao lado do CRM (hero, seção "Sobre" e rodapé), ex.: `CRM-XX 10898 · RQE 0000`.
7. **UF do CRM** — confirmar o estado (ex.: CRM-AM).
8. **Foto profissional** do médico (opcional, recomendada na seção "Sobre").

## ⚠️ Imagens de raio-X

As radiografias em `assets/` foram derivadas de imagens de banco de imagens (Dreamstime, 123RF) usadas como **provisórias**. Antes de divulgar o site, substitua por imagens licenciadas, de banco gratuito (Unsplash, Pexels, Wikimedia Commons) ou próprias e anonimizadas. Basta manter os mesmos nomes de arquivo.

## Como editar e publicar

```bash
# visualizar localmente
python3 -m http.server 8000
# abrir http://localhost:8000

# publicar alterações
git add -A
git commit -m "Atualiza contatos"
git push
```

O GitHub Pages republica automaticamente em ~1 minuto após cada `push` na branch `main`.

### Domínio próprio (opcional)

1. Registrar o domínio (ex.: `drarthurortopedia.com.br` no Registro.br).
2. Em *Settings → Pages → Custom domain*, informar o domínio.
3. No DNS, criar um `CNAME` de `www` para `willpine1992.github.io` (e registros `A` para os IPs do GitHub Pages no domínio raiz).

---

As informações do site têm caráter educativo e não substituem a consulta médica.
