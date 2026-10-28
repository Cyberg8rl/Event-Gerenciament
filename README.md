# Sistema de Gerenciamento de Eventos Universitários

Aplicação de linha de comando em Python para cadastrar eventos, consultar a lista de eventos e gerenciar inscrições de participantes respeitando a capacidade máxima de cada evento.

## Funcionalidades implementadas

- Cadastrar eventos com nome, data, descrição e limite de vagas.
- Listar os eventos cadastrados e calcular as vagas restantes.
- Inscrever participantes em um evento existente.
- Impedir inscrições quando o evento atinge sua capacidade.
- Consultar os inscritos de um evento.
- Tratar entradas inválidas para opções de menu, IDs e número de vagas.

## Tecnologias

- Python 3
- Estruturas de dados nativas: listas e dicionários
- Entrada e saída pelo terminal

## Como executar

1. Instale Python 3.
2. Clone ou baixe o repositório.
3. No terminal, entre na pasta do projeto.
4. Execute:

```bash
python main.py
```

## Como os dados são armazenados

A versão atual mantém eventos e inscrições em memória usando listas e dicionários. Os dados são perdidos quando o programa é encerrado; não há persistência em arquivo ou banco de dados.

## Finalidade

Projeto acadêmico para praticar lógica de programação, funções, estruturas condicionais, laços, validação de entradas e regras de negócio. Não é um sistema de produção.
