# ATLAS.victor — projeto inteiro em 12/10/2026

Documento para avaliação. Descreve o desenho, o que existe e o que não existe. Não é o quadro do dia e não manda operar nada.

Não contém chave, token, senha nem application key. Números de upload abaixo são fotos velhas. Quem for citar porcentagem do Mandar tem que reler o log.

A pasta `Desktop\Projeto Vitor` não é um repositório git. Este texto é a cópia que vai para o GitHub `dhub7/atlas-victor`, que até 12/10 só tinha o plano de reorganização de 01/10.

## O que o projeto é

Produtora na nuvem de *The Places in Between*. Victor é diretor, DP e editor. Erica é host, produtora e colorista. Erik edita. Caio aprova Shorts. Dudinha faz thumb e título. Daniel faz a arquitetura.

Nome interno: ATLAS. Nome que eles usam com a IA: Berlota. Instância: ATLAS.victor.

Regra que não muda: nada publica sozinho. Short aprova o Caio. Longo aprova Victor e/ou Erica. Telegram fica quieto até o Daniel dizer **manda**.

A frase que o diretor deveria ver, e que ainda não acontece:

```
filmo → sobe proxy e, quando der, o RAW
     → chega um pacote no Telegram
     → assisto, peço ajuste, dou OK
     → uma pessoa publica
     → eu dirijo o próximo
```

O lançamento escrito no roadmap era 07/10/2026. No WhatsApp de 22/09 o Victor mudou para quinta **29/10/2026, 14:00 em Nova York** (15:00 em Brasília; a partir de 05/11, 16:00). A planilha não foi reescrita desde 15/09 e ainda marca o episódio 1 em 07/10. Hoje é 12/10. O sistema não tem um episódio pronto para publicar.

## Três textos, três datas

| Texto | Data | O que é | O que não é |
|---|---|---|---|
| `06_Roadmap_Execucao.md` | desenho de julho, reancorado em 11/08 | Blocos B0–B8, dez agentes, calendário até 07/10 | O agora |
| README deste repo | 01/10 | Proposta de reorganização: parar a fábrica, operar o que eles já editaram, corte dentro do Resolve deles, planilha como esteira | Plano instalado na pasta. Os números de upload desse README são de 01/10 |
| Este arquivo | 12/10 | Retrato do projeto inteiro para outra IA avaliar | Quadro do upload. O plano novo está na seção «Plano aceito em 12/10» e em `PLANO.md` |

O quadro operacional da pasta continua `07_Execucao/quadro/AGORA.md`, fechado em 02/10 no teste do DaVinci. A foto do Mandar dentro dele é de 30/09.

## Arquitetura que existe hoje

```
Van (RAW no HD)
    │  Mandar, um clique, copy sem delete. Mac da Erica
    ▼
B2 atlas-victor-bruto                 cofre
    YT-MAIN/00_INBOX/TRANSFER/        RAW desta fila
    dropbox-mirror/                   cópia de setembro do Dropbox
    00_APPS/inbox-mac/                app e log
    │
    │  proxy no Lucid, mesmo stem. Proxy Canon ganha p
    ▼
LucidLink artluzstudio                disco de trabalho
    proxies, áudio, .drp, revisão leve
    │
    ▼
DaVinci Resolve Studio                dois MacBooks do Victor
    chave Blackmagic, duas ativações dele
    corte humano. Nenhum agente ligado

Hetzner CX33  62.238.99.33
    n8n em 127.0.0.1:5678
    bot Telegram @artluz_atlas_bot (FSM, sem LLM, quieto)
    página de revisão dos Shorts 1–5 (execução descartada, página ainda no ar)
    servidor do Drive (o site só lista objeto já fechado)

Vercel
    https://atlas-vitor.vercel.app          apresentação. Não é o sistema
    https://driveatlasvictor.vercel.app     capa do Drive. A chave entra pela Vercel

PC do Daniel
    Resolve gratuito 21.1.1. A API externa não conecta
    Hermes local (daniel-ops, science). Não é deste projeto
```

Três lugares de arquivo, sem espelho byte a byte. O que liga é o stem do clip e o projeto Resolve. Lucid não carrega bruto. B2 não é disco de edição. O site Drive não recebe upload.

## Blocos

O roadmap parte o trabalho em B0–B8, mais o site como B9. Estado real em 12/10:

| Bloco | No papel | Hoje |
|---|---|---|
| **B0 Infra** | Contas, B2, Lucid, VPS, n8n, Telegram, matriz de papéis | Feito em 17/08. Hetzner no lugar de AWS. Bot é FSM, não LLM. Veio depois, e está no ar: app Mandar e o Drive web. Plano de 12/10, não construído: um Hermes novo na VM, só para os agentes deste projeto. O Hermes do PC do Daniel não entra |
| **B1 Ingestão** | Watch de proxy para o Lucid, bruto para o B2, meta por episódio, n8n criando pasta | Não existe watch. O bruto sobe pelo Mandar, na mão, no Mac da Erica. Catálogo do piloto em `B1_Ingestao/catalog.json`. Os 598 de South Dakota no Lucid não foram copiados para o B2, de propósito. Espelho Dropbox→B2 de setembro terminou (2138 objetos, 1,12 TiB). Em 12/10 o espelho ainda falta Ozark, Chicago e 17 arquivos de YouTube. Essa cópia não foi autorizada |
| **B2 Cérebro** | Store de estilo e um Manager que responde o que está pendente | Cards em markdown, `B2_Cerebro/v0/`. Alma, programa e nomes de pasta fechados em agosto. Notion/Airtable não foi escolhido. O bot não responde pendência de episódio. Telegram quieto |
| **B3 Transcrição** | Um episódio inteiro com tempo e falante | Whisper `small` no VPS. Pacote do Rode do dia 09 aceito (Tartaruga1 e Tartaruga2 são os lavaliers, não blocos). Lavalier 19–20 não. Não virou job contínuo |
| **B4 Cineasta** | Rough cut, Shorts, export e `.drp`, Caio aprova no Telegram | Não existe como agente. O ensaio ffmpeg/YuNet foi descartado em 25/09. O teste de 02/10 no Resolve gratuito deste PC não conectou na API. Plano de 12/10, não construído: o Cineasta mora no Hermes da VM e mexe no Studio que já está nos dois Macs do Victor, por um programinha local e um túnel privado |
| **B5 Texto, thumb, música** | Título, descrição, thumbs, trilha | Não existe como sistema. Dudinha e Caio continuam pessoas. Música famosa no YouTube Shorts segue pergunta: alcance ou receita |
| **B6 Distribuição** | Publicar só depois do OK, com log | Nada passou pelo sistema. Zero publicação automática. O primeiro lote, se vier, sai na mão pelo YouTube Studio |
| **B7 Dashboard** | Pendência por pessoa, calendário, kanban | Não existe. A planilha deles seria essa tela. Última edição do arquivo: 15/09. Link na seção da esteira |
| **B8 Buffer** | 8 a 10 episódios com OK até o lançamento | Não existe dentro do sistema. Eles editam por fora. Na planilha de 15/09 o mais perto de pronto é Micanopy. Em 22/09 o Victor falou Arkansas 01 e 02 finalizados e ele no Arkansas 03. A célula não acompanhou a boca |
| **B9 Site** | Apresentação, depois do sistema | https://atlas-vitor.vercel.app no ar. O scroll Between the Place está pausado. Não bloqueia e não opera o canal |

O calendário do roadmap (B4 em 14/09, B6 em 23/09, go-live em 07/10) não aconteceu. Tratar B4–B8 como histórico de intenção, não como fila.

## Agentes

O plano diretor lista dez papéis: Manager, Orquestrador, Produção, Ingestão, STT, Cineasta, Redator, Designer, Música, Distribuição.

O que roda:

| Coisa | Tipo | Onde | Estado |
|---|---|---|---|
| Bot Telegram | Máquina de estados, sem LLM | Hetzner | No ar e calado. Não é o Manager |
| n8n | Fila desenhada | Hetzner, só localhost | Quase sem uso. Um webhook de job. Não orquestra corte |
| Mandar | Script de upload | Mac da Erica, versão `2026.09.23.2` | Cano do RAW. Não é agente. Não entra na conversa de estrutura de agentes |
| Drive web | Lista o B2 fechado | Hetzner + capa Vercel | Índice. Não é agente |
| Whisper | Script que já rodou | VPS | Pacote do dia 09. Não é um agente em serviço |
| Cineasta ffmpeg | Script local | PC do Daniel | Descartado como produto em 25/09 |

O que não roda: Manager com LLM, orquestrador, cineasta, redator, designer, música, distribuição, qualquer Hermes do ATLAS.

A proposta de 01/10 reduz para quatro papéis e ainda não foi instalada: Berlota (a voz), Cineasta (timeline dentro do projeto Resolve que eles já abrem), Mesa (lê a planilha), Texto (título e legenda). Nesse texto o Hermes ficava no PC do Daniel. O lugar mudou: o Hermes do ATLAS é outro, na VM.

## Plano aceito em 12/10

Está escrito em `PLANO.md` neste repo e em `07_Execucao/PLANO_ATLAS.md` na pasta. Nada disto está construído.

**B0.** Um Hermes novo na VM gerencia os agentes do projeto. Um agente é um profile. O primeiro é a Berlota. O Hermes decide e reparte. Não sobe arquivo, não publica e não mexe no Mandar. O Hermes do PC do Daniel fica de fora. Não se instala Hermes no Mac. Victor e Erica continuam falando pelo Telegram, quieto até **manda**. O dashboard de atividade fica na VM e entra quando houver mais de um trabalho longo.

**B4.** O Cineasta é um profile desse Hermes. A mão é um programinha no Mac do Victor, onde o Studio já está ativado com a chave Blackmagic. O programinha fala com o Resolve só em Local (`127.0.0.1`, com token). A VM manda a ordem por túnel privado. A porta 1144 não abre. Só um dos dois Macs recebe ordem por vez. O Resolve tem que estar aberto, com o Lucid montado e o projeto carregado. O primeiro teste só lê versão, projeto e timeline. O short nasce como timeline `ATLAS-SHORT-` numa cópia do projeto que eles já usam. Não se cria projeto novo por short. Não se publica, não se apaga e não se relinka mídia. O MCP oficial do Studio 21.1 pode ficar por baixo do programinha, se o Mac estiver nessa versão. Ele não substitui o túnel.

## Resolve

O Victor tem a licença Studio em chave Blackmagic, nos dois MacBooks. As duas ativações são as duas máquinas dele. Não há terceira vaga nessa chave.

O PC do Daniel tem o Resolve 21.1.1 gratuito. `scriptapp("Resolve")` não conecta. O teste de 02/10 deixou o projeto `ATLAS-TESTE-MICANOPY` fechado, timeline vazia, e dois cortes 9:16 feitos pelo ffmpeg em `07_Execucao/teste-resolve/export/`.

O Studio 21.1, de 8 de setembro de 2026, tem MCP nativo em File > Setup AI Assistants. É atualização grátis para quem tem a chave da Blackmagic. Configura um assistente no próprio Mac. Não foi ligado nos Macs do Victor. A versão instalada em cada Mac não foi lida.

A ponte do Cineasta está na seção «Plano aceito em 12/10». Não está construída. A porta 1144 continua fechada.

## Esteira que eles já têm

A planilha que o Victor mandou em 14/09:

https://docs.google.com/spreadsheets/d/1GZX2LiRcTHynDrC8R3xfz17avZf9wlSQBSkZX7-z8MM/edit

Nome: `THE_PLACES_IN_BETWEEN_Master_Content___Production_Control_Sheet`. Dono: victorpalermob@gmail.com. Última alteração conhecida: 15/09/2026 02:24 UTC. Não foi lida de novo em 12/10.

Abas: Production Status, Content Calendar, Episode Details, Shorts Tracker, README, Perfomance.

O que as células diziam em 15/09, e que ele mesmo disse em 22/09 que estava atrasado:

| Ep | Título na célula | Mais perto de pronto | Data na célula |
|---|---|---|---|
| 1 | Micanopy, Florida | Edição, mix, cor, legenda e título Completed. Thumb em progresso. 10 de 12 shorts | 07/10 |
| 2 | Ozarks, Arkansas — Part 1 | Edição e mix Completed. Cor em progresso | 14/10 |
| 3 | Ozarks, Arkansas — Part 2 | Edição em progresso | 21/10 |
| 4 | Ozarks, Arkansas — Part 3 | Não começou | 28/10 |
| 5 | South Dakota — 1808 Town | Edição, mix e legenda Completed. Cor em progresso | 04/11 |
| 6 | South Dakota — Deadwood | Edição em progresso | 11/11 |
| 7 | Yellowstone | Não começou | 18/11 |
| 8 | Washington — Pousbo | Não começou. O nome está assim na célula | 25/11 |

Em 22/09 ele falou por cima: Arkansas 01 e 02 finalizados, ele no Arkansas 03, 10 episódios filmados, Chicago como o de 31/12. Chicago não está nas 8 linhas. Não inventar a nona.

Colunas de link do Drive e do YouTube estavam vazias. Não há coluna de quem aprovou.

## Repositórios

| Lugar | O que é |
|---|---|
| `dhub7/atlas-victor` | Este repo. Texto para avaliação. Não tem site, não tem Drive, não está instalado na pasta |
| `dhub7/atlas-inbox-mac` | Código do Mandar e da UI do Drive. GitHub em `c815611`, que é a versão `2026.09.23.2` que o Mac lê do B2. Há um patch local não publicado |
| `Desktop\Projeto Vitor` | Pasta de trabalho. Não é git. Junction `Desktop\Projeto Victor` aponta para ela |
| `07_Execucao/B0_Infra/inbox/` | Árvore velha. Não é o que sobe |
| `07_Execucao/B0_Infra/drive-web` | Capa Vercel. Fora dos dois repos |

O Mac da Erica lê o app do B2, não do GitHub. Push no GitHub não atualiza o Mac. `publicar.ps1` é o que atualiza, e não roda com upload aberto.

## Decisões que continuam

- Nunca publicar sozinho.
- Shorts usam footage diferente do longo. Gancho de 3–5 s. Imagem mais entrevista. Sem cortar frase no meio.
- Nome nativo do clip. Tag de cena em nota, não no nome do arquivo.
- Pasta real: lugar, câmera, bruto ou proxy, data. Victor pediu para manter `SOUTH DAKOTA` e datas `09.07.26`.
- Lucid é trabalho. B2 é cofre. Quem sobe esta fila é a Erica.
- Cérebro em markdown é a voz. A planilha é o quadro de conteúdo, quando estiver atualizada.
- Bot sem LLM na conversa, até o Daniel mandar.

## O que uma avaliação deve separar

1. Desenho de julho (dez agentes, B0–B8, lançamento 07/10). Quase só o B0 saiu do papel. B1–B3 saíram pela metade, por outro caminho.
2. Proposta de 01/10 (quatro papéis, corte no Resolve deles, planilha como esteira, fábrica B4–B8 vira histórico). Escrita. Não instalada. Upload descrito nela está velho.
3. Plano de 12/10, aceito e não construído. B0 ganha um Hermes novo na VM para gerenciar os agentes. B4, o Cineasta, usa o Resolve Studio que já está nos dois Macs, por programinha local e túnel. O Mandar não faz parte dessas duas peças.

## Perguntas abertas

- Qual dos dois Macs ele usa para editar, e qual versão do Studio está em cada um.
- A planilha de 15/09 ainda é a que vale, e o que mudou desde 22/09.
- Música famosa no YouTube Shorts: alcance ou receita.
- Onde Chicago entra na ordem, além de ser o longo de 31/12.
- Nome do episódio que ele disse ter filmado em 21/09.
- Se a fábrica B4–B8 morre de vez ou se alguma peça (texto, thumb, gate) volta com outro nome.

## O que não fazer a partir deste texto

- Não tratar o README de 01/10 como o estado do upload.
- Não ligar dez agentes.
- Não publicar, não clicar Mandar, não abrir a porta 1144.
- Não copiar os 598 do Lucid para o B2.
- Não usar o Hermes do PC do Daniel como frota deste projeto.
- Não criar um projeto Resolve novo para cada short.
