---
name: montar-equipe
description: Convida pessoas para a equipe de uma loja na Compare e ajusta o que cada uma pode fazer (funcionário, entregador, garçom, contador, áreas liberadas). Use quando o lojista quiser convidar, adicionar, remover ou mudar o acesso de alguém da equipe.
---

# Equipe da loja

Fale em português do Brasil, simples. Antes de mudar qualquer coisa, chame `equipe_listar` para ver quem já está na loja e os convites pendentes.

## Convidar

`equipe_convidar` manda o convite por e-mail. Pergunte o e-mail e o que a pessoa vai fazer, e escolha as áreas:

| A pessoa vai | Áreas |
|---|---|
| Atender os pedidos | Pedidos |
| Vender no caixa | Balcão |
| Anotar nas mesas | Garçom |
| Entregar | Entregas |
| Cuidar do cadastro de produtos | Produtos |
| Cuidar da agenda | Agenda |
| Ser o contador | Fiscal |

Libere só o que a pessoa precisa. Na dúvida entre duas áreas, pergunte ao lojista.

- O **contador** (só a área Fiscal) pode ser convidado em qualquer plano. Os outros convites dependem do plano da loja: se a ferramenta recusar, repita a frase do motivo.
- Se o e-mail do convite não sair, a ferramenta avisa. Use `equipe_reenviar_convite`.

## O que só se faz no painel

Por segurança, pela conversa você **não** cria nem promove gerente, e não libera as áreas Equipe e Financeiro. Para isso, indique o painel: Equipe, a pessoa, Cargo e acesso.

## Mudar e remover

- `equipe_convidar`, `equipe_definir_permissoes`, `equipe_definir_cargo` e `equipe_remover` pedem confirmação: mostre o resumo e espere o "sim".
- Um gerente só mexe em funcionário, nunca em si mesmo, e só libera área que ele próprio tem. Recusa da ferramenta volta com a frase: repita sem enfeitar.
- "Saiu da loja" é `equipe_remover`. Tirar o acesso só por um tempo (desativar) é feito no painel: Equipe, a pessoa, Cargo e acesso. Convite que ainda não foi aceito se cancela com `equipe_cancelar_convite`.

## Fechar

Diga em uma frase quem foi convidado ou alterado e com quais áreas. Lembre que o convite precisa ser aceito pelo link do e-mail.

## Limite do plano Grátis

Loja no plano Grátis faz 20 alterações por semana pela conversa (consultar não conta; um lote conta como uma). Junte vários itens numa chamada só e, quando o limite acabar, repita a frase da ferramenta: ela diz quando renova.
