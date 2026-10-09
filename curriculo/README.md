# 📄 Currículo Online

Currículo em formato de página web que imita uma **folha A4**, feito só com HTML e CSS. Funciona como página online e também pode ser **salvo em PDF** direto do navegador, já ajustado para caber em uma página.

**🌐 Ver online:** [paxtel-source.github.io/Projetos-HTML-CSS/curriculo](https://paxtel-source.github.io/Projetos-HTML-CSS/curriculo/)

![Prévia do currículo](docs/preview.png)

## Funcionalidades

- Layout de duas colunas: **lateral** com contato, habilidades e idiomas e **principal** com sobre mim, projetos, formação e cursos
- **Barras de habilidade** feitas só com CSS, controladas por uma variável (`--nivel`)
- Seção de **projetos** com links para os repositórios do GitHub
- **Versão para PDF:** com <kbd>Ctrl</kbd> + <kbd>P</kbd> → "Salvar como PDF", sai uma folha A4 com as cores mantidas
- Na impressão, os links mostram o endereço completo, já que no papel não dá para clicar
- Responsivo: no celular, a coluna lateral vai para cima
- Acessível: os níveis das habilidades são lidos por leitores de tela ("nível 3 de 5")

## Estrutura

```
curriculo/
├── index.html
├── css/
│   ├── style.css   # Estilo da tela
│   └── print.css   # Estilo da impressão e do PDF (A4)
└── docs/
    └── preview.png
```

## Como personalizar

Abra o `index.html` e troque os textos entre colchetes, como `[Nome do curso]`, `[Instituição de ensino]` e `[Cidade] – [UF]`, pelos seus dados. Troque também o e-mail de exemplo.

**Nível das habilidades:** mude o número em `style="--nivel: 3"` (de 1 a 5) e o texto oculto `nível 3 de 5` logo abaixo:

```html
<li style="--nivel: 4">
  <span class="habilidades__nome">Python</span>
  <span class="barra" aria-hidden="true"></span>
  <span class="visualmente-oculto">nível 4 de 5</span>
</li>
```

## Como gerar o PDF

1. Abra o `index.html` no navegador.
2. Aperte <kbd>Ctrl</kbd> + <kbd>P</kbd>.
3. Em **Destino**, escolha **Salvar como PDF**.
4. Em **Mais definições**, deixe **Gráficos de plano de fundo** marcado (para manter a coluna colorida).

## Detalhes técnicos

- **Barra de habilidade com uma variável:** o preenchimento é um `linear-gradient` cuja largura é `calc(var(--nivel) * 20%)`. Nível 3 vira 60%.
- **Fonte com largura variável:** o nome usa a fonte Archivo com `font-stretch: 62%`, uma versão condensada da mesma família.
- **Folha A4 na impressão:** `@page { size: A4; margin: 0; }` e `print-color-adjust: exact` para manter as cores de fundo.
- **Endereço dos links no papel:** `a::after { content: " (" attr(href) ")"; }`.

## Conceitos praticados

HTML semântico (`aside`, `article`, `time`), CSS Grid, variáveis CSS, `calc()`, fontes variáveis, texto oculto acessível, `@page`, `@media print`, `attr()`.
