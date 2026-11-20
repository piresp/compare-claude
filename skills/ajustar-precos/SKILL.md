---
name: ajustar-precos
description: Muda preços, promoções e disponibilidade do catálogo de uma loja na Compare, um item ou vários de uma vez. Use quando o lojista pedir para subir, baixar, reajustar ou corrigir preço, criar ou tirar promoção, pausar ou reativar itens.
---

# Ajustar preços e promoções

Fale em português do Brasil, simples. Dinheiro sempre em reais, com duas casas.

## Passo a passo

1. **Ache os itens** com `catalogo_listar` (busca por nome, filtro por situação). Com muitos itens, percorra as páginas antes de concluir: cada página traz 25.
2. **Mostre antes de mudar**: uma tabela com nome, preço atual e preço novo. Em reajuste por percentual, mostre o valor final já arredondado para duas casas.
3. **Grave** com `catalogo_definir_preco` (valor ou percentual, um item ou vários). Mudança em vários itens pede confirmação: mostre o resumo que a ferramenta devolve e espere o "sim".
4. **Confirme o resultado** em uma frase: quantos mudaram e, se algum falhou, qual e por quê.

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
