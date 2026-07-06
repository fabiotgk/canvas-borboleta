# Canvas Borboleta 🦋

Tapete de facilitação (**A3 paisagem, monocromático**) do método **Arquitetura Borboleta** — com
**post-its digitais editáveis** e saída para impressão.

**Ao vivo:** https://fabiotgk.github.io/canvas-borboleta/

---

## O que é

Junta a estrutura do método (do PDF original) com uso de aula/workshop:

- **Anatomia da borboleta:** asas de aquisição em cima (**Outbound** + **Inbound**), **funil de vendas**
  no corpo (100% → 22%), **Cliente** no núcleo, asas de crescimento embaixo (**Retenção** + **Expansão**),
  e os **6 canais de aquisição** no topo.
- **20 slots** (uma etapa cada) com código + nome, esperando a anotação.
- **Mono de propósito:** o canvas é todo preto-no-papel; **a cor vem só dos post-its**.

## Como usar

- **Clicar num quadrinho** → cola um post-it já etiquetado com a etapa (editar, arrastar, trocar cor, apagar).
- **+ Post-it** → nota solta livre.
- **Imprimir A3** → sai limpo em A3 paisagem (barra some; título/resumo/instruções ficam impressos no canvas
  para colar post-it físico).
- O conteúdo escrito é salvo no navegador (`localStorage`), então volta ao reabrir.

## Estrutura

```
canvas-borboleta/
├── index.html      ← a peça inteira (HTML + CSS + JS, tudo inline, zero dependências)
├── README.md
└── referencia/     ← material do cliente (NÃO versionado — ver .gitignore)
    └── borboleta_receita_mono.pdf
```

## Manutenção / como mexer

Tudo vive em `index.html`. Os pontos de edição mais comuns estão no `<script>`:

- **Textos das etapas / zonas:** objeto `ZONES` (nome, tagline e as 5 `stages` `[código, nome]` de cada asa).
- **Funil:** array `FUNNEL` (`[nome, porcentagem]`).
- **Canais de aquisição:** `CHAN_L` e `CHAN_R`.
- **Formato das asas:** arrays `FORE` / `HIND` (pontos das curvas Bézier, offsets a partir do tórax).
- **Posição dos slots:** `FORE_SLOTS` / `HIND_SLOTS` (grade 3+2 por asa).
- **Cores do post-it:** variáveis `--pi-*` no `<style>` e objeto `COLORS`.
- **Marca/cores do canvas:** variáveis CSS em `:root` (`--paper`, `--ink`, etc.).

### Rodar localmente

Como usa `localStorage` e `fetch` implícito de nada, basta abrir o arquivo — mas o ideal é servir:

```bash
cd canvas-borboleta
python3 -m http.server 8000
# abrir http://localhost:8000
```

(O `<meta charset="utf-8">` já garante os acentos corretos em qualquer servidor.)

## Ideias de evolução

- Versão **A3 retrato**.
- Aplicar **marca do cliente** (logo + paleta) — hoje é neutro de propósito.
- **Exportar/importar** o preenchimento (JSON) para salvar sessões de workshop.
- Botão **exportar PNG/PDF** direto (hoje via Imprimir → salvar como PDF).

---

Feito por DevNX.
