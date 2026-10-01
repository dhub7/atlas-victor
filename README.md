> Proposta para avaliação em 01/10/2026. Ainda não está instalada como plano canônico dentro da pasta do projeto. O envio B2 da Erica não foi mexido.
# Projeto Victor — reorganização e novo plano

Data da leitura: 2026-10-01, ~20:00 Brasília. Nada disto constrói agente, automação ou arquivo novo no repo. O Mandar da Erica continua intocável.

A mudança de fase é esta: a fábrica B1–B8 não é mais o caminho. O chão agora é operar o que Victor e Erica já filmaram e já editaram, com o DaVinci deles como lugar do corte, e uma esteira que mostra o status de cada peça.

## 1. Como o projeto está hoje

ATLAS.victor continua sendo a produtora na nuvem de *The Places in Between* (Victor diretor/DP, Erica host/cor). Nome interno ATLAS. Nome que eles usam com a IA: Berlota. Zero auto-publish. Telegram quieto até o Daniel dizer **manda**.

O que está vivo agora é o cofre, não a publicação.

- Job da Erica, versão `2026.09.23.2`, desde 25/09, Mac `Ericas-MacBook-Pro-2`, origem `~/ATLAS/TRANSFER`, destino `b2:atlas-victor-bruto/YT-MAIN/00_INBOX/TRANSFER/`.
- Fechados neste clique: 15/04 ~94 GB, 10/04 ~76 GB, `A023C972` 82 GiB, `A023C985` 145 GiB.
- Aberto, único multipart: `04.20.2026/A023C982_260420WC_CANON_P.CRM`, 181 GiB, fatia 19 MiB, **parte 5908/9733 (~61%)** no fim do log escrito 19:58 Brasília de 01/10. Starlink segue quebrando o pipe; o script espera e não pula o arquivo. É o 2/2 da pasta. Quando der `FECHOU`, este clique acaba.
- Não clicar Mandar. Não republicar o app. Não Control+C. O Drive (https://driveatlasvictor.vercel.app) só mostra objeto fechado. `LastModified` de large file é a hora que começou.

O lançamento escrito **07/10/2026** está a seis dias. O critério antigo (1 episódio ponta a ponta no sistema, 1 publish com OK, 8 pacotes, Manager no Telegram) não foi atingido. Tratar 07/10 como data de sistema é falso. A operação começa pelo que eles já têm pronto, publicado na mão, com OK humano.

## 2. O que já foi construído

| Peça | Estado real |
|---|---|
| B0 | Fechado. Hetzner CX33 `62.238.99.33`, n8n, bucket `atlas-victor-bruto`, Lucid `artluzstudio`, bot `@artluz_atlas_bot` (FSM, sem LLM), matriz de roles |
| Inbox/Mandar + Drive web | No ar. É o cano do RAW e o índice do que já fechou. Não é o disco de edição |
| Cérebro v0 | Markdown em `07_Execucao/B2_Cerebro/v0/`. Vozes, tom, Shorts ≠ longo, aprovações. Store Notion/Airtable segue aberto e perde prioridade |
| Piloto `south-dakota-p2` | Mapeado no Lucid (`SOUTH DAKOTA` + `SOUTH DAKOTA PARTE 2`, 598 arquivos em ago/26). Não liberado para corte. Não copiar esses 598 para o B2 |
| STT | Rode do dia 09 aceito (Tartaruga1/2 = lavaliers). Lavalier 19–20 não |
| Shorts 1–5 do dia 09 | Paper-cut + preview local. Execução **descartada** em 25/09. Página http://62.238.99.33/?k=places-p2 ainda no ar, não é a fila |
| B4 cineasta | Foi ffmpeg + YuNet no PC, não job no Hetzner. Não vira o fluxo novo |
| B5–B8 | SEO, publish com gate, dashboard, buffer de 8 eps: não feitos |
| Site | https://atlas-vitor.vercel.app é apresentação, não o sistema de produção |
| Hermes | Stack pessoal em `Desktop/hermes-local` (v0.20.0, Qwen 9B na RTX 3060). Frota `daniel-ops` + `science`. **Não é a frota do ATLAS** |

Conteúdo que eles já produziram, fora do sistema: o inventário do Dropbox de **11/08** (foto velha, não recontada) mostra `YouTube_EXPORTS` com finais de Micanopy (`micanopy-Y-FC01/02`, `THE PLACES IN BETWEEN - MICANOPY.mp4`), pasta `SHORTS/short01.mp4`, `REELS_TIKTOK`, `CORTES`, e um `.drp` `SOUTH DAKOTA - 4 JULY.drp` ao lado do material. Washington e Novo México aparecem como pastas de captura. Isso confirma que a edição humana já existe. Não dá para dizer o que está pronto hoje sem a planilha deles.

## 3. Decisões que continuam e decisões que mudam

Continuam:

- Nunca publicar sozinho. Short aprova o Caio. Longo aprova Victor e/ou Erica.
- Shorts usam footage diferente do longo. Gancho em 3–5s. Imagem + entrevista. Sem talking-head. Sem cortar frase no meio.
- Nome nativo do clip. Proxy Canon só ganha `p`. Tag de cena em nota, não no filename.
- Pasta real: lugar → câmera → BRUTO ou PROXY → data. Victor pediu para manter `SOUTH DAKOTA` e `09.07.26`.
- Lucid = proxy e trabalho. B2 = cofre. HD da van = RAW que ainda não subiu. Quem sobe esta fila é a Erica. Mac do Victor quieto.
- Música famosa no YouTube Shorts segue pergunta do Daniel (alcance contra receita). IG/TT já usam. Não decidir no escuro.

Mudam:

- O roadmap B1–B8 e o calendário até 07/10 passam a histórico. `00_TUDO_DO_PROJETO.md` e o §0 do roadmap já eram foto de julho. `quadro/AGORA.md` continua sendo o agora operacional do cofre até este plano ser aceito e instalado.
- O cineasta não cria um fluxo paralelo de corte (ffmpeg, preview solto, `.drp` novo por short). O short nasce **dentro do projeto Resolve que eles já usam**.
- A árvore `YT-MAIN/episodes/{slug}` não é imposta em cima da mídia que já está no Lucid. O slug é índice. A pasta física continua a deles.
- Não ligar dez agentes. A operação pede poucos papéis e uma esteira.
- Airtable, Notion e Supabase deixam de ser candidatos do dia 1. A planilha que eles já usam é o quadro. O markdown do Cérebro continua sendo a voz e as regras.

## 4. Storage — o papel de cada um

Três lugares, um mapa. Eles não se espelham byte a byte. O que os liga é o **stem do clip** e o **projeto Resolve**.

```
HD da van (RAW que ainda não subiu)
        │  Mandar, um clique, copy sem delete
        ▼
B2 atlas-victor-bruto          cofre frio
  YT-MAIN/00_INBOX/TRANSFER/   RAW desta fila (câmera / data)
  dropbox-mirror/              histórico já copiado
  00_APPS/inbox-mac/           o app e o log
        │  mesmo stem; proxy Canon com p
        ▼
LucidLink artluzstudio         disco de trabalho
  proxies, áudio de edição, .drp, exports leves de revisão
        │
        ▼
DaVinci (projeto do lugar)     timelines do longo e dos shorts
```

**LucidLink.** Continua sendo o disco em que Erik e o Resolve trabalham, como se fosse um HD. Lição confirmada na prática e na documentação atual da Lucid: cache do filespace em SSD local; o filespace **não** fica no topo de Media Storage (senão cache do Resolve vai para a nuvem); Direct I/O desligado; banco de projetos do Resolve **fora** do Lucid. Os 598 de South Dakota não se movem e não se copiam para o B2. Pasta nova de proxy entra no padrão que eles já têm, não numa árvore ATLAS paralela.

**B2 / Mandar.** Cofre do bruto e arquivo do que não pode depender da Starlink no meio do corte. Aprendizados que ficam na arquitetura: uma fila só; fatia serial (32 MB × 3 deu zero fatia); teto de 10.000 partes com fatia automática; Python nativo nos gordos (rclone cancela large file); processo vivo não puxa versão nova; prova de fechado = objeto na lista + `FECHOU` no log. O B2 não é montado como disco de edição do dia a dia. Na finalização e na cor, o Resolve relinka o proxy do Lucid para o original no HD ou, quando o bruto já fechou, para uma cópia local tirada do B2. Não há sync contínuo Lucid↔B2.

**“Drive” são duas coisas, e só uma é storage.** O site driveatlasvictor é a janela do B2 para celular e PC: lista o que já fechou, não recebe o upload, não guarda TB. Google Drive, se entrar, guarda documento: a planilha, cards, stills de revisão. Não guarda footage.

**Organização dos arquivos.** Índice ATLAS (`meta` por lugar) aponta para o path real. Não renomeia. Exports pesados de YouTube ficam onde eles já ficam (`YouTube_EXPORTS`, `SOCIAL MEDIA_EXPORTS`) até a esteira dizer o contrário. Um short aprovado exporta **de dentro da timeline daquele projeto**, para a pasta de export que o projeto já usa.

## 5. DaVinci — o corte mora no projeto deles

Decisão de operação: o short é uma timeline dentro do `.drp` do lugar (o hábito deles já é esse: `SOUTH DAKOTA - 4 JULY.drp` ao lado do material). Se não gostarem, abrem aquele projeto e ajustam um segundo, uma legenda, um corte. Não existe uma ilha de edição da IA.

O que a pesquisa de setembro/2026 muda no plano:

- **Resolve Studio 21.1** (8/09/2026) traz MCP nativo. Em File > Setup AI Assistants o Resolve grava o servidor nos clientes que a Blackmagic nomeia: Claude, Claude Code e ChatGPT Codex. Exemplos oficiais: organizar mídia, montar highlight, tirar corte curto demais, render em lote. A API nova inclui multicam, auto-align, transições, transcrição de clip no Media Pool com falante e tempo, e presets de render.
- Isso é **Studio**. Licença perpétua em torno de US$ 295, ou assento Blackmagic Cloud. No 21.1 a Blackmagic tirou o scripting Python externo da edição grátis. Free 21.1 não é caminho de agente.
- O processo do agente tem de rodar **na mesma máquina em que o Resolve está aberto**, com o Lucid montado e o projeto carregado. Não é o Hetzner. Não é um job cego no Windows do Daniel, a menos que essa máquina tenha Resolve + Lucid + o projeto.
- **Grok** fala MCP e já tem o B2. A Blackmagic não lista o Grok no botão oficial. Caminho real: ou o cliente genérico conseguir apontar para o MCP local do Studio 21.1 (a confirmar na máquina deles, porque o setup oficial só escreve config do Claude e do Codex), ou um MCP de terceiros na mesma máquina (`dvr` 1.7.0, set/2026, CLI + biblioteca + MCP; ou `davinci-resolve-mcp`). Hermes também é cliente MCP e pode ser o agente sentado nesse Mac.
- Risco: esses servidores conseguem apagar projeto e sobrescrever grade, e um cliente de nuvem pode enviar frame do footage para o modelo. Regra: o agente só cria ou edita timelines com prefixo `ATLAS-SHORT-` dentro do projeto já aberto; não cria projeto novo; não mexe em grade; não renderiza master; export de revisão só com OK. Frame de footage não vai para modelo de nuvem sem o Daniel autorizar.

Fluxo do short, quando a licença estiver confirmada:

1. Abrir o projeto do lugar que eles já usam.
2. Achar no Media Pool o proxy já linkado (Lucid).
3. Criar a timeline do short dentro desse projeto, com IN/OUT e o porquê (por que não é o momento do longo).
4. Legenda e título nascem nessa timeline.
5. Export de revisão sai dessa timeline.
6. Eles ajustam ali mesmo. O OK volta para a esteira. O publish continua humano.

Enquanto a edição Studio 21.1 não estiver confirmada, o mesmo desenho vale na mão: a pessoa cria a timeline no projeto existente. A IA entrega o paper-cut (in, out, fala, porquê). Não volta o ffmpeg como editor.

Blackmagic Cloud (sync de projeto, “sync proxies only”) não substitui o Lucid. Se um dia servir, é só para o arquivo de projeto entre duas máquinas. A mídia continua no Lucid. O banco local do Resolve não vai para o filespace.

## 6. Agentes e Hermes

O Hermes que existe no PC do Daniel é o harness (Nous Research): profile, SOUL, memória, skills, MCP, e desde o v0.21 (31/08/2026) Bot Mode, kanban com claim único, e `hermes peer` para um agente falar com outro. A instalação local documentada é **0.20.0** e a frota é pessoal. ATLAS ganha profiles próprios, sem misturar SOUL de LiveMode/ciência.

Quatro papéis. Não dez.

| Profile | Onde roda | Função | Não faz |
|---|---|---|---|
| **Berlota** (Manager) | PC do Daniel, Hermes | Única voz com Victor e Erica. Lê a esteira, responde status, cobra o próximo passo | Não corta, não publica, não mexe no Mandar |
| **Cineasta** | Máquina do Resolve, com Lucid montado | Cria a timeline `ATLAS-SHORT-` dentro do projeto aberto. Entrega in/out e export de revisão | Não cria projeto novo, não publica, não relinka bruto |
| **Mesa** | Pode ser skill do Berlota no começo | Traduz a planilha em “o que está em cada estágio” e no próximo passo | Não é a dona criativa da peça |
| **Texto** | PC do Daniel | Título, descrição, legenda, a partir do Cérebro + transcript da timeline | Não posta. Dudinha e Caio editam |

Comunicação: a planilha é o estado compartilhado. Um escritor só (Mesa/Berlota), para não repetir o problema que o Victor descreveu no Airtable: campo aberto demais, um erro apaga a verdade. Entre agentes, kanban do Hermes com uma tarefa por peça (`lugar / short / estágio`). O Cineasta devolve o nome da timeline e o path do export; o Berlota atualiza a linha. Telegram continua sendo o canal humano e fica mudo até **manda**. O bot FSM atual não ganha LLM nesta fase.

n8n no Hetzner fica para coisa burra e estável: lembrar que o log do Mandar parou, avisar estágio atrasado. Não orquestra o Resolve.

Grok, neste desenho, é o lugar onde o Daniel planeja e olha o B2. Não é o editor sentado no Resolve, até o MCP genérico do Studio estar provado na máquina deles.

## 7. Ferramentas — o que fica, o que sai, o que só se olha

Fica: LucidLink, B2 + Mandar, Drive web como índice, DaVinci como NLE, Cérebro em markdown, Telegram como gate, Hetzner/n8n para aviso, ffmpeg só para checagem pontual.

Sai do caminho: cineasta ffmpeg/YuNet como produto, `.drp` novo por short, inbox watch clássico antes da primeira publicação, GPU no Hetzner, Airtable/Notion/Supabase como quadro, dashboard novo antes de existir uma esteira que eles abram.

Avaliar depois, sem instalar agora:

- Studio 21.1 na máquina de quem edita. É a porta do agente dentro do projeto. Sem isso, o fluxo é humano dentro do mesmo projeto.
- Hermes 0.21+ só quando for criar o profile Berlota. Não atualizar no meio deste plano.
- Transcrição dentro do Media Pool (API 21.1) num timeline piloto, no lugar de manter um Whisper separado para todo áudio novo. O pack do dia 09 continua válido.
- Publicação: o primeiro lote sai pelo YouTube Studio, agendado por uma pessoa, com OK na planilha. Rede extra (IG/TT) usa a pasta `SOCIAL MEDIA_EXPORTS` que eles já têm. Scheduler de terceiro (Publer, Blotato e afins) só entra se o lote manual doer. Blotato escreveu sobre Resolve MCP → rede social; isso não vira stack.
- Thumbnail: still exportado da própria timeline, acabamento da Dudinha. Ferramenta de thumbnail por IA fica fora até esse gesto estar chato de repetir.
- Música: continua a pergunta aberta. Não escolher biblioteca nova antes dela.

## 8. Esteira e a planilha

A esteira é uma linha por peça publicável (longo, short, corte legado), não por arquivo de câmera.

`existe → em edição (projeto Resolve) → finalização → short (timeline) → thumbnail → texto → revisão → aprovado → agendado → publicado → teste`

Quem mexe em cada coluna: Erik/Victor/Erica na edição e na finalização; Cineasta ou eles na timeline do short; Dudinha na thumbnail e no título; Caio no OK do short; Victor/Erica no OK do longo; uma pessoa no agendamento; ninguém publica sem a coluna de aprovado preenchida. O teste é uma coluna curta: o que se mediu (retenção dos 3s, inscrição, comentário) e se a peça seguinte muda por causa disso. Sem isso, “teste” vira feeling.

A planilha deles é a fonte dessa esteira. Não está no repo. Busca no Google Drive desta conta, por planilha com Places / Victor / Short / conteúdo, voltou vazia. Até o arquivo chegar (link ou cópia), o quadro de conteúdo **não se inventa**. O inventário de 11/08 e o paper-cut do dia 09 são contexto, não status.

Quando a planilha chegar, o trabalho é mapear as colunas que eles já têm para os estágios acima, acrescentar só o que faltar (projeto Resolve, nome da timeline, quem aprovou, data de agenda, link publicado). Não se cria uma segunda tabela.

O que já dá para dizer sem a planilha, e com data:

- Pronto como sistema de publish: nada.
- Pronto como ideia de short do dia 09: cinco paper-cuts. Execução descartada. Não estão dentro de um projeto Resolve nosso.
- Pronto como cofre desta fila: quatro CRM fechados; C982 aberto.
- Pronto como edição humana: há exports e pelo menos um `.drp` na foto de agosto. A lista viva está com eles.

## 9. Próximas etapas — só depois deste plano aceito

Nenhuma destas etapas começa nesta conversa.

1. Deixar o C982 terminar. Acompanhar pelo log. Não encostar no Mac.
2. Receber a planilha e escrever o mapa de colunas. Uma página, sem migrar os dados.
3. Listar os projetos Resolve que eles consideram “o projeto” de cada lugar, e em qual máquina abrem. Confirmar Free ou Studio, e a versão.
4. Instalar este texto como plano canônico do projeto e marcar o roadmap B4–B8 como histórico. `AGORA.md` passa a apontar para a esteira, sem apagar o aviso do Mandar enquanto o job viver.
5. Escolher com eles o primeiro lote que a planilha diz que está pronto e publicar esse lote na mão, com OK, pelo YouTube Studio. Esse é o teste da esteira. Não é um agente.
6. Só então: profile Hermes `berlota` que lê a planilha e responde status. Um short piloto como timeline `ATLAS-SHORT-` dentro de um projeto existente, na máquina certa, se o Studio 21.1 estiver lá.

## 10. O que precisa do Daniel antes do passo 2

- Onde está a planilha (link ou arquivo) e quem é o dono.
- Resolve de quem edita é Studio? Qual versão, qual máquina?
- 07/10 ainda é lançamento público ou a data já escorregou na conversa com eles?
- Música famosa no YouTube Shorts: alcance ou receita?

## 11. O que não fazer

- Não clicar Mandar, não matar o upload, não republicar o inbox, não retomar C972/C985.
- Não copiar os 598 do Lucid para o B2.
- Não criar projeto Resolve novo para cada short.
- Não ligar o bot no grupo.
- Não construir o cineasta, o dashboard nem o publish automático antes da esteira e do primeiro lote manual.

