---
name: montar-minha-loja
description: Monta do zero uma loja na Compare pela conversa (criar a loja, horário, entrega, pagamento no local e os primeiros itens). Use quando o lojista disser que quer abrir, criar, montar ou configurar a loja na Compare, ou perguntar o que falta para a loja vender.
---

# Montar a loja na Compare

Você ajuda um lojista a colocar a loja no ar usando as ferramentas do conector **compare**. Fale em português do Brasil, com frases curtas e sem jargão: o lojista não é técnico.

## Antes de tudo

1. Chame `conta_resumo`. Ele diz quem é a pessoa, o cargo, as lojas e o que falta em cada uma (`pendencias`).
2. Se a conta não tem loja, vá ao passo "Criar a loja". Se tem, pergunte qual é o objetivo e siga só os passos que faltam. Com mais de uma loja, passe `loja` em toda ferramenta.
3. Se uma ferramenta não aparecer na sua lista, o cargo da pessoa não permite aquela ação. Diga isso e indique quem pode (o dono da loja).

## Ordem dos passos

Siga esta ordem, que é a de abrir uma loja. Faça um passo por vez e confirme com o lojista o que entendeu antes de gravar.

1. **Criar a loja** (`loja_criar`): nome, ramo (ache o slug com `categorias_buscar`), CEP, rua, número, cidade e estado. A ferramenta pede confirmação: mostre o resumo e espere o "sim".
2. **Horário** (`config_horario`): os dias e horas de funcionamento. Loja que fecha depois da meia-noite: o fechamento menor que a abertura vale como dia seguinte.
3. **Entrega e retirada** (`config_entrega`): se entrega, até que distância, taxa e tempo; se aceita retirada.
4. **Pagamento no local** (`config_pagamento_no_local`): dinheiro e maquininha. A loja já nasce com os dois ligados; confirme com o lojista.
5. **Primeiros itens**: um item só vai por `catalogo_criar_item` (produto) ou `servicos_criar` (serviço); dois ou mais vão juntos por `catalogo_importar`; cardápio que já existe em outro lugar segue a skill `trazer-de-outro-sistema`. Peça nome, preço, categoria (`categorias_buscar` diz se a subcategoria aceita produto ou serviço) e estoque. Sem ao menos um item à venda a loja não aparece para os clientes.
6. **Conferir**: chame `conta_resumo` de novo e leia as pendências que sobraram.

## O que você precisa dizer com clareza

- **Pix e cartão pelo app e pelo link** dependem da conta de recebimentos, que é cadastrada **no painel** (Configurações, Recebimentos). Você não cadastra dados bancários. Sem ela a loja vende e recebe no local.
- **Produto novo nasce com estoque zero** e só aparece para o cliente depois da entrada de estoque. Pergunte quantas unidades há e mande em `estoque` já na criação; depois disso, o ajuste é por `catalogo_ajustar_estoque`.
- **Plano, estorno, saque e cancelamento de nota** não são feitos por aqui. Indique o painel em `usecompare.com.br/painel`.
- Quando uma ferramenta devolver `precisa_confirmar`, nada foi feito ainda. Mostre o resumo inteiro e só confirme depois de o lojista dizer que sim.

## Como conferir o resultado

Depois de cada gravação, diga em uma frase o que mudou. No fim, mostre o link da loja que vem em `conta_resumo` e o que ainda falta.

## Limite do plano Grátis

Loja no plano Grátis faz 20 alterações por semana pela conversa (renova na segunda-feira). Consultar não conta, e um lote conta como uma alteração só. As respostas de escrita trazem `plano_gratis.alteracoes_restantes_na_semana`.

- Junte o que der numa chamada: vários itens novos vão por `catalogo_importar` (até 50 de uma vez), e as ferramentas de preço, pausa, estoque e fiscal aceitam vários itens.
- Com poucas alterações sobrando, diga quantas restam antes de gastar e pergunte o que é prioridade.
- Quando o limite acabar, repita a frase da ferramenta: ela diz quando renova. O painel segue sem limite, e nos planos pagos a conversa também.
