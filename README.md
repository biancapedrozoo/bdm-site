# Site BDM — Bianca Digital Marketing + BDM Creative

Site de uma página (marketing) com loja de papelaria personalizada (BDM Creative)
no mesmo domínio. Um só domínio, duas marcas.

## O que está nesta pasta

```
bdm-site/
├── index.html            → www.biancadigitalmarketing.pt  (site de marketing)
├── bdmcreative/
│   └── index.html        → www.biancadigitalmarketing.pt/bdmcreative/  (loja)
├── CNAME                 → diz ao GitHub qual é o teu domínio
├── .nojekyll             → ficheiro técnico, deixa ficar
└── README.md             → este guia
```

## ⚠️ ANTES DE SUBIR — falta adicionar 3 imagens

O site de marketing (`index.html`) usa 3 ficheiros de imagem que TENS de colocar
dentro da pasta `bdm-site/` (ao lado do `index.html`), com estes nomes exatos:

- `logo.png`        → logo BDM escuro (para o menu no topo)
- `logo-light.png`  → logo BDM claro (para o rodapé escuro)
- `bianca.jpg`      → a tua foto (hero e secção "A Fundadora")

Se quiseres, manda-me estes ficheiros que eu ligo-os e confirmo os nomes.
(O logo da loja BDM Creative é em texto, não precisa de imagem.)

### Fotos dos produtos (carrossel)
Cada produto da loja tem um carrossel de 3 fotos. Coloca-as em
`bdmcreative/img/` com os nomes indicados no ficheiro
`bdmcreative/img/COMO-ADICIONAR-FOTOS.txt`. Enquanto não as adicionas, aparece
um placeholder com o emoji e o nome do produto — o site funciona na mesma.

---

## Como subir para o GitHub (sem usar terminal — pela página)

1. Cria conta em https://github.com (se ainda não tens).
2. Carrega no **+** (canto superior direito) → **New repository**.
3. Em *Repository name* escreve: **biancadigitalmarketing.pt** (ou outro nome).
   Deixa **Public** marcado. Carrega em **Create repository**.
4. Na página do repositório, carrega em **"uploading an existing file"**.
5. Arrasta para lá **todo o conteúdo de dentro da pasta `bdm-site`**
   (o `index.html`, a pasta `bdmcreative`, o `CNAME`, o `.nojekyll` e as 3 imagens).
   ⚠️ Arrasta o *conteúdo*, não a pasta `bdm-site` em si.
6. Em baixo, carrega em **Commit changes**.

## Pôr o site online (GitHub Pages)

1. No repositório, vai a **Settings** (engrenagem) → **Pages** (menu da esquerda).
2. Em *Source*, escolhe **Deploy from a branch**.
3. Em *Branch*, escolhe **main** e a pasta **/ (root)**. Carrega em **Save**.
4. Espera 1–2 minutos. O site fica online.

## Ligar o teu domínio (www.biancadigitalmarketing.pt)

O ficheiro `CNAME` já tem `www.biancadigitalmarketing.pt` lá dentro, por isso o
GitHub já sabe o domínio. Falta só apontar o domínio para o GitHub, no painel
onde compraste o domínio (ex: GoDaddy, Namecheap, etc.):

1. Vai às definições de **DNS** do teu domínio.
2. Cria um registo do tipo **CNAME**:
   - **Nome/Host:** `www`
   - **Valor/Destino:** `OTEU-UTILIZADOR.github.io`  (troca pelo teu utilizador GitHub)
3. (Opcional, para o domínio sem o "www") cria 4 registos **A** com o nome `@`
   a apontar para estes IP do GitHub:
   `185.199.108.153` · `185.199.109.153` · `185.199.110.153` · `185.199.111.153`
4. Pode demorar algumas horas a propagar. Depois, em **Settings → Pages**,
   ativa **Enforce HTTPS**.

Resultado final:
- **www.biancadigitalmarketing.pt** → site de marketing
- **www.biancadigitalmarketing.pt/bdmcreative/** → loja BDM Creative

---

## Como editar depois (preços, produtos, número, textos)

Tudo o que muda na loja está num só sítio: abre `bdmcreative/index.html` e
procura por **`const PRODUTOS`** (perto do fim do ficheiro).

- **Número de WhatsApp:** procura `const WHATSAPP` (está nos dois ficheiros).
- **Produto com preço fixo:** usa `tiers` com `{ qty, unit, price }`.
- **Produto "sob orçamento":** tem `quote: true` e só `{ qty }` nos tiers.
  Quando tiveres a tabela, apaga o `quote: true` e acrescenta `unit` e `price`.

Exemplo de produto com preço:
```js
{
  categoria: "Papel & Cartolina",
  id: "tags-sacolas",
  nome: "Tags para Sacolas",
  emoji: "🛍️",
  desc: "Etiquetas pendentes para sacolas.",
  tiers: [
    { qty: 50,  unit: 0.40, price: 20 },
    { qty: 100, unit: 0.30, price: 30 }
  ]
}
```

Para qualquer alteração no GitHub: abre o ficheiro no site do GitHub, carrega no
lápis ✏️ (editar), faz a mudança e carrega em **Commit changes**. Fica online sozinho.
