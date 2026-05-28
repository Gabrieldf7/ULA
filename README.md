# Unidade Lógica e Aritmética (ULA) de 4 bits

Este projeto implementa uma Unidade Lógica e Aritmética (ULA/ALU) de 4 bits desenvolvida em VHDL utilizando o software Intel Quartus Prime. A ULA é capaz de realizar operações lógicas, aritméticas e de comparação com base em um código de operação (Opcode) de 3 bits.

## Estrutura do Projeto

O projeto adota uma arquitetura estrutural (top-down), sendo composto pelos seguintes módulos principais:
- **ula.vhd**: Entidade principal que integra e seleciona o resultado dos submódulos.
- **somador_4bits.vhd**: Implementa a operação de soma e subtração de 4 bits (utilizando complemento de 2).
- **somador_completo.vhd**: Bloco fundamental para construção do somador.
- **comparador_4bits.vhd**: Compara as duas entradas para indicar se são iguais, maior ou menor.
- **multiplicador.vhd**: Realiza a multiplicação entre dois operandos de 2 bits, gerando um resultado de 4 bits.

O projeto também conta com arquivos de *testbench* (`*_tb.vhd`) para validação e simulação de cada componente.

## Tabela de Opcodes

A ULA seleciona a operação a ser executada a partir de um `opcode` de 3 bits.

| Opcode | Operação          | Descrição                                 |
|--------|-------------------|-------------------------------------------|
| `000`  | **NOP**           | Nenhuma operação (Saída = `0000`)         |
| `001`  | **AND**           | Operação lógica `A and B`                 |
| `010`  | **OR**            | Operação lógica `A or B`                  |
| `011`  | **NOT**           | Operação lógica `not B`                   |
| `100`  | **ADD**           | Adição aritmética `A + B`                 |
| `101`  | **SUB**           | Subtração aritmética `A - B`              |
| `110`  | **MUL**           | Multiplicação (entradas limitadas a 2 bits) |
| `111`  | **COMP**          | Comparação (Ativa flags `equ`, `grt`, `lst`) |

## Flags e Saídas

A ULA não só calcula o resultado, como também reporta o status das operações por meio de flags:
- `result` (4 bits): Saída da operação selecionada.
- `zero`: Ativada (`1`) quando o resultado da operação for `0000`.
- `overflow`: Ativada (`1`) quando ocorre um estouro na soma ou subtração em complemento de 2.
- `cout`: Carry Out gerado durante a operação de soma/subtração.
- `equ` (Equal): Ativada se `A = B` durante a operação de comparação.
- `grt` (Greater): Ativada se `A > B` durante a operação de comparação.
- `lst` (Less): Ativada se `A < B` durante a operação de comparação.

## Ferramentas Utilizadas
- **Linguagem**: VHDL
- **Software**: Intel Quartus Prime
- **Simulação**: ModelSim / Questa Intel FPGA Edition

## Como Executar
1. Abra o projeto `Ula.qpf` no Intel Quartus Prime.
2. Compile o projeto para verificar a sintaxe e gerar os componentes.
3. Para simular, utilize os arquivos de *testbench* disponíveis na pasta do projeto e execute-os em seu simulador VHDL de preferência.
