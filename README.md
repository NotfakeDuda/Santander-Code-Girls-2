# AWS Step Functions - Fluxo de Trabalho de Aprovação de Pedido

Este projeto demonstra a criação de uma máquina de estado simples no **AWS Step Functions**, simulando a aprovação de pedidos.

## Descrição do Fluxo de Trabalho

O fluxo de trabalho verifica se um pedido é válido e direciona para aprovação ou rejeição:

1. **PassPedidoInicial**:  
   - Estado inicial que passa a entrada JSON (ex.: `{"pedidoValido": true}` ou `{"pedidoValido": false}`) para a próxima etapa.

2. **ChoiceValidarPedido**:  
   - Verifica o valor da variável `$.pedidoValido` e decide:  
     - `true` → **PedidoAprovado**  
     - `false` → **PedidoRejeitado**  
   - Qualquer valor inesperado também segue para **PedidoRejeitado** (Default).

3. **Estados Finais**:  
   - **PedidoAprovado** → Estado de sucesso.  
   - **PedidoRejeitado** → Estado de falha, indicando que o pedido não passou na validação.

## Como Usar no Console AWS Step Functions

1. Acesse [AWS Step Functions](https://console.aws.amazon.com/states/home).  
2. Clique em **Create state machine** → **Author from scratch**.  
3. Copie o conteúdo de `state_machine_definition.json` no editor de máquina de estado.  
4. Dê um nome à máquina de estado (ex.: `AprovacaoPedido`).  
5. Clique em **Create state machine**.  
6. Clique em **Start execution** e insira uma das entradas JSON:

- Pedido aprovado:
# AWS Step Functions - Fluxo de Trabalho de Aprovação de Pedido

Este projeto demonstra a criação de uma máquina de estado simples no **AWS Step Functions**, simulando a aprovação de pedidos.

## Descrição do Fluxo de Trabalho

O fluxo de trabalho verifica se um pedido é válido e direciona para aprovação ou rejeição:

1. **PassPedidoInicial**:  
   - Estado inicial que passa a entrada JSON (ex.: `{"pedidoValido": true}` ou `{"pedidoValido": false}`) para a próxima etapa.

2. **ChoiceValidarPedido**:  
   - Verifica o valor da variável `$.pedidoValido` e decide:  
     - `true` → **PedidoAprovado**  
     - `false` → **PedidoRejeitado**  
   - Qualquer valor inesperado também segue para **PedidoRejeitado** (Default).

3. **Estados Finais**:  
   - **PedidoAprovado** → Estado de sucesso.  
   - **PedidoRejeitado** → Estado de falha, indicando que o pedido não passou na validação.

## Como Usar no Console AWS Step Functions

1. Acesse [AWS Step Functions](https://console.aws.amazon.com/states/home).  
2. Clique em **Create state machine** → **Author from scratch**.  
3. Copie o conteúdo de `state_machine_definition.json` no editor de máquina de estado.  
4. Dê um nome à máquina de estado (ex.: `AprovacaoPedido`).  
5. Clique em **Create state machine**.  
6. Clique em **Start execution** e insira uma das entradas JSON:

- Pedido aprovado e pedido reprovado:
```json
{
  "pedidoValido": true
}
{
  "pedidoValido": false
}
```
7. Observe o caminho que a execução percorre e o estado final alcançado.



