Este repositório contém o exercício da Aula 05 sobre a criação de workflows no GitHub Actions.

## Descrição

O projeto envolve a criação de um servidor simples em Golang, que responde "Hello, {name}" em uma porta específica. Além disso, há um script de automação (`run.sh`) que faz requisições HTTP para o servidor e imprime respostas para diferentes usuários.

### Arquivos

- `hello-server.go`: Código-fonte do servidor em Go.
- `run.sh`: Script que executa o servidor e faz as requisições HTTP.
- `.github/workflows/go-example.yml`: Workflow do GitHub Actions que compila o código e faz upload dos artefatos para Linux e Windows.

## Como Funciona

1. Quando há um push na branch `main`, o workflow `go-example.yml` é acionado.
2. O código Go é compilado para Linux e Windows.
3. Os artefatos gerados são armazenados como artefatos do workflow.
4. Dois jobs são executados após o build:
   - **Linux**: Baixa e executa o artefato no Linux.
   - **Windows**: Apenas baixa o artefato para Windows.

### Scheduler

O workflow também é executado a cada 15 minutos, de segunda a sábado, mesmo sem um novo push.

## Execução Local

Para rodar o servidor localmente:

```bash
go run hello-server.go
