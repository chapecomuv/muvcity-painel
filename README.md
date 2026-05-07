# MuvCity Transfer — Painel de Gestão de Frota

Sistema de gestão financeira completo para frota de transporte executivo.

## Estrutura

- `index.html` — Página inicial (escolhe entre painel completo ou lançamento rápido)
- `FleetControl_Pro.html` — Painel completo do gestor (dashboard, viagens, despesas, relatórios)
- `FleetControl_Socio.html` — Mini-app de lançamento rápido para sócio/motoristas
- `manifest.json` — Configuração PWA (instalável como app)

## Como hospedar no GitHub Pages

### Passo 1 — Criar conta e repositório
1. Vá em https://github.com e crie uma conta (ou faça login)
2. No canto superior direito, clique em `+` → **New repository**
3. Nome: `muvcity-painel` (ou o que preferir)
4. Escolha **Public** (necessário pro GitHub Pages funcionar de graça)
5. NÃO marque "Add README"
6. Clique em **Create repository**

### Passo 2 — Subir os arquivos
Na tela do novo repositório vai aparecer "uploading an existing file" — clique nesse link.

Arraste os 4 arquivos da pasta `DASHBOARD MUV` pra dentro do navegador:
- `index.html`
- `FleetControl_Pro.html`
- `FleetControl_Socio.html`
- `manifest.json`

Em "Commit changes" digite `subindo o painel` e clique em **Commit changes**.

### Passo 3 — Ativar o GitHub Pages
1. Ainda no repositório, clique em **Settings** (no topo)
2. Na coluna esquerda, clique em **Pages**
3. Em "Source", escolha **Deploy from a branch**
4. Em "Branch", selecione **main** e a pasta **/(root)**
5. Clique em **Save**

Aguarde 1-2 minutos. Volte na aba Pages — vai aparecer um link tipo:
```
https://SEU_USUARIO.github.io/muvcity-painel/
```

Esse é o link que você compartilha com sócio e motoristas. Eles abrem no celular.

### Passo 4 — Testar
1. Abre o link no PC → deve aparecer a tela com 2 cards (Painel Completo / Lançamento Rápido)
2. Clica em "Painel Completo" → carrega a interface
3. Abre o mesmo link no celular → mesma coisa, layout adaptado pra mobile

## Como atualizar (depois)

Sempre que fizer alterações nos arquivos no PC, no GitHub:
1. Abre o repositório
2. Clica no arquivo (ex: `FleetControl_Pro.html`)
3. Clica no ícone de lápis (Edit) — ou arrasta o arquivo novo
4. **Commit changes** — em ~1 minuto a versão pública atualiza

## Como funciona o fluxo com sócio/motorista

**Atualmente** o sistema usa armazenamento local do navegador (`localStorage`). Cada dispositivo tem seu próprio banco. **Não há sincronização automática entre dispositivos.**

### Fluxo recomendado:

**Você (gestor) no PC:**
- Abre `FleetControl_Pro.html`
- Cadastra veículos, motoristas, clientes, despesas fixas
- Lança viagens e despesas próprias

**Sócio ou motorista no celular:**
- Abre o link, escolhe **Lançamento Rápido**
- Lança a viagem ou despesa que precisa
- Clica em **Exportar para o gestor** → gera um arquivo `.json`
- Manda o arquivo via WhatsApp pra você

**Você recebe e importa:**
- No painel completo, clica em **Importar do Sócio** (botão na topbar)
- Seleciona o arquivo `.json`
- O sistema acumula as viagens/despesas no seu banco

Esse fluxo funciona sem internet (depois de carregada a página) e mantém seus dados privados — não passa por nenhum servidor de terceiros.

## Próximos passos (opcional)

Se quiser **sincronização automática real** entre dispositivos, é necessário plugar um backend. Opções:

- **Firebase Realtime DB** — Google, free tier generoso, fácil
- **Supabase** — Postgres gerenciado, free tier, muito popular
- **JSONBin.io** — Solução simples, REST puro, free

Qualquer uma dessas exige criar uma conta e configurar credenciais no painel. Pergunte sobre isso quando estiver pronto pra esse upgrade.

## Adicionar à tela inicial (PWA)

Tanto pra você quanto pro sócio/motorista:

**No Android (Chrome):**
1. Abre o link
2. Menu (⋮) → **Adicionar à tela inicial**
3. Confirma — vira um ícone na home, abre como app sem barra do navegador

**No iPhone (Safari):**
1. Abre o link
2. Botão Compartilhar (quadrado com seta) → **Adicionar à Tela de Início**
3. Confirma

## Backup

Sempre faça backup antes de alterar dados:

1. Painel completo → **Configurações**
2. Role até **Backup & Transferência de Dados**
3. Clica em **Exportar todos os dados** — baixa um arquivo `FleetControl_backup_AAAA-MM-DD.json`
4. Guarda em local seguro (Google Drive, OneDrive, etc.)

Em caso de necessidade, basta importar esse arquivo de volta.

---

**Versão atual:** Design v3.9 — Mobile Ready
