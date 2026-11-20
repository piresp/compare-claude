---
name: trazer-de-outro-sistema
description: Importa para a Compare o catálogo que o lojista já tem em outro lugar (planilha, PDF, foto do cardápio, página de outro sistema ou texto colado). Use quando ele disser que quer migrar, importar, trazer ou copiar produtos, serviços ou cardápio de outro sistema.
---

# Trazer o catálogo de outro sistema

Você lê o material do lojista, organiza os itens e importa com `catalogo_importar`, em lotes de até 50. Fale em português do Brasil, simples e direto.

## 1. Entender o que chegou

Peça o material (arquivo, foto, link ou texto). Leia tudo antes de importar. Para cada item identifique: nome, preço, descrição, categoria, variações (tamanho, sabor), se é montado em etapas (monte seu combo, escolha o molho), estoque e foto.

Se algo essencial faltar (preço, por exemplo), pergunte. Nunca invente preço, estoque nem código fiscal.

## 2. Preparar os itens

- **`import_ref`**: o código do item no sistema de origem. Sem código, crie um estável a partir do nome (`pizza-calabresa-g`). Importar de novo com o mesmo `import_ref` **atualiza** o item em vez de duplicar. Guarde os que você usou para repetir numa correção.
- **Categoria**: ache o slug com `categorias_buscar`. Use a subcategoria mais próxima; na dúvida entre duas, pergunte.
- **Variações**: item com tamanhos ou sabores de preço diferente vira um item com `variants`, e não vários itens.
- **Montagem em etapas**: importe primeiro os itens que entram nas etapas (com `sells_alone: false` quando só existem dentro da montagem) e depois o item montado, citando cada um pelo `import_ref`.
- **Serviço**: precisa da duração em minutos, múltiplo de 15.
- **Foto**: só endereço `https` público. Foto que não baixar vira aviso, e o item entra do mesmo jeito.
- **Estoque**: só vale na primeira importação. Importar de novo não mexe no estoque.

## 3. Conferir antes de gravar

Mostre ao lojista uma tabela curta do primeiro lote (nome, preço, categoria, variações) e pergunte se está certo. `catalogo_importar` sempre pede confirmação: mostre o resumo que ela devolve e espere o "sim".

## 4. Importar em lotes

- Até 50 itens por chamada. A ferramenta pede confirmação: mostre o resumo e espere o "sim". Cada lote confirmado conta como uma alteração no limite do plano Grátis.
- Uma importação por loja de cada vez: espere a resposta antes de mandar o próximo lote.
- Leia o resultado item a item. o que vem em `falharam` traz o motivo (categoria que não existe, limite do plano, etapa que cita um item que não entrou). Corrija e mande só os que falharam, com o mesmo `import_ref`.
- `warning` significa que o item entrou, mas algo depois não (foto, estoque inicial ou vitrine). Diga qual e como resolver.

## 5. Fechar

Conte quantos entraram, quantos foram atualizados e quantos ficaram de fora, com o motivo. Se o plano da loja limitar a quantidade de itens, diga isso com a frase que a ferramenta devolveu e indique o painel para ver os planos. Ofereça a skill `cadastrar-fiscal` se o lojista emite nota.

## Limite do plano Grátis

Loja no plano Grátis faz 20 alterações por semana pela conversa (renova na segunda-feira). Consultar não conta, e um lote conta como uma alteração só. As respostas de escrita trazem `plano_gratis.alteracoes_restantes_na_semana`.

- Junte o que der numa chamada: vários itens novos vão por `catalogo_importar` (até 50 de uma vez), e as ferramentas de preço, pausa, estoque e fiscal aceitam vários itens.
- Com poucas alterações sobrando, diga quantas restam antes de gastar e pergunte o que é prioridade.
- Quando o limite acabar, repita a frase da ferramenta: ela diz quando renova. O painel segue sem limite, e nos planos pagos a conversa também.
