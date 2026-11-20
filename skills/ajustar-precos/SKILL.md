---
name: ajustar-precos
description: Muda preços, custos, promoções, vitrines e disponibilidade do catálogo de uma loja na Compare, um item ou vários de uma vez. Use quando o lojista pedir para subir, baixar, reajustar ou corrigir preço, pôr preço pela margem, dizer quanto sobra, guardar custo ou taxa, organizar ou ordenar vitrines, criar ou tirar promoção, pausar ou reativar itens.
---

# Ajustar preços e promoções

Fale em português do Brasil, simples. Dinheiro sempre em reais, com duas casas.

## Passo a passo

1. **Ache os itens** com `catalogo_listar` (busca por nome, filtro por situação). Com muitos itens, percorra as páginas antes de concluir: cada página traz 25.
2. **Mostre antes de mudar**: uma tabela com nome, preço atual e preço novo. Em reajuste por percentual, mostre o valor final já arredondado para duas casas.
3. **Grave** com `catalogo_definir_preco` (valor ou percentual, um item ou vários). Mudança em vários itens pede confirmação: mostre o resumo que a ferramenta devolve e espere o "sim".
4. **Confirme o resultado** em uma frase: quantos mudaram e, se algum falhou, qual e por quê.

## Custo, imposto e preço pela margem

- **Custo** (`catalogo_definir_custo`): quanto o item custa para a loja. O cliente nunca vê. Aceita a planilha inteira (até 50 itens); produto com variações guarda o custo de cada variação.
- **Imposto e taxas** (`config_custos_da_venda`): o imposto sobre a venda (MEI é 0%, o DAS é fixo; no Simples, a alíquota que o contador passa) e a taxa da maquininha no crédito, no débito e no Pix. Pergunte ao lojista. Nunca chute taxa nem alíquota.
- **Quanto sobra**: `catalogo_listar` e `catalogo_ver_item` trazem `custo`, `sobra_no_credito` e `sobra_no_pix`. Margem é o que sobra do PREÇO, não "em cima do custo": 60% em cima do custo deixa bem menos de 60% de sobra.
- **Preço pela margem**: `catalogo_definir_preco` com `margem: { percentual }` usa o custo guardado, o imposto e a taxa do crédito (o pior caso); com `forma_de_pagamento` usa outra taxa, e com `custos_da_venda_pct` usa os percentuais que o lojista disser. Item sem custo é recusado: peça o custo e grave antes.

## Quanto sobrou

`loja_lucro` dá, para o período, quanto sobrou dos produtos vendidos (receita − custo − imposto − taxas, o mesmo número do Início) e o que sobrou de cada produto. `sem_custo` lista os produtos vendidos sem custo cadastrado: ofereça gravar o custo deles antes de tirar conclusões.

## Vitrines

As vitrines são as seções da página da loja e do app. `vitrines_listar` mostra a ordem que o cliente vê; `vitrines_criar` cria; `vitrines_ordenar` muda a ordem delas; `vitrines_organizar` põe e tira produtos; `vitrines_ordenar_itens` muda a ordem dentro de uma vitrine. Para "reorganizar a vitrine para vender mais", leia antes o que vende e o que sai junto (`pedidos_listar` no histórico), proponha o arranjo e só mude depois do "sim".

## Regras do produto

- **Promoção** (`catalogo_definir_promocao`): o preço promocional tem de ser menor que o preço normal. Produto com variações de preço diferente não aceita promoção no item: ajuste o preço de cada variação.
- **Item montado em etapas**: o preço é o preço base mais o que o cliente escolher. Mexer no preço base muda todas as combinações.
- **Pausar** (`catalogo_pausar`) tira o item da loja sem apagar. Prefira pausar a excluir quando o lojista disser "tirar por enquanto".
- **Excluir** (`catalogo_excluir`) não tem volta e pede confirmação.
- O que a ferramenta recusar volta com a frase do motivo. Repita a frase ao lojista sem enfeitar.

## O que não fazer

Não mude preço de item que o lojista não citou. Em pedido vago ("sobe tudo 10%"), confirme o alcance antes: todos os itens, uma categoria, só os ativos?

## Limite do plano Grátis

Loja no plano Grátis faz 20 alterações por semana pela conversa (renova na segunda-feira). Consultar não conta, e um lote conta como uma alteração só. As respostas de escrita trazem `plano_gratis.alteracoes_restantes_na_semana`.

- Junte o que der numa chamada: vários itens novos vão por `catalogo_importar` (até 50 de uma vez), e as ferramentas de preço, pausa, estoque e fiscal aceitam vários itens.
- Com poucas alterações sobrando, diga quantas restam antes de gastar e pergunte o que é prioridade.
- Quando o limite acabar, repita a frase da ferramenta: ela diz quando renova. O painel segue sem limite, e nos planos pagos a conversa também.
