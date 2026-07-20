# Executando Tarefas Automatizadas com AWS Lambda e Amazon S3

Este repositório foi desenvolvido para documentar o processo prático, anotações teóricas e os insights adquiridos durante o laboratório focado na automação de tarefas e arquitetura orientada a eventos utilizando **AWS Lambda** e **Amazon S3**.

## Objetivos do Desafio
* Consolidar os conhecimentos em computação baseada em funções (Serverless).
* Compreender a integração nativa orientada a eventos entre armazenamento (S3) e execução de código (Lambda).
* Documentar processos de arquitetura de nuvem estruturados utilizando o GitHub como portfólio técnico.

## Conceitos Fundamentais Aprendidos

### 1. Amazon S3 (Simple Storage Service)
O Amazon S3 é um serviço de armazenamento de objetos focado em escalabilidade, disponibilidade de dados, segurança e performance. No ecossistema de automação, o S3 atua frequentemente como o **gatilho (trigger)** de um fluxo, disparando notificações sempre que um novo arquivo é criado, modificado ou deletado dentro de um bucket.

### 2. AWS Lambda
O AWS Lambda é um serviço de computação *Serverless* (sem servidor) que permite executar código em resposta a eventos sem a necessidade de provisionar ou gerenciar infraestrutura subjacente. Você paga apenas pelo tempo de computação que consome (tempo de execução da função).

### 3. Arquitetura Orientada a Eventos (Event-Driven)
A integração entre S3 e Lambda exemplifica uma arquitetura moderna orientada a eventos:
* **Gatilho:** Um upload de arquivo (ex: `ObjectCreated`) acontece no bucket do S3.
* **Evento:** O S3 gera um documento JSON contendo metadados sobre o arquivo (nome, tamanho, formato, bucket de origem).
* **Processamento:** O AWS Lambda intercepta esse JSON de forma assíncrona, extrai as informações necessárias e executa uma tarefa automatizada predefinida (como compactação de imagem, extração de dados, validação de arquivos ou carga em um banco de dados).

## Fluxo de Trabalho do Laboratório

1. **Configuração do Armazenamento:** Criação e estruturação do bucket no Amazon S3 para recepção de arquivos de teste.
2. **Desenvolvimento da Função:** Escrita e configuração do código da AWS Lambda Function com as permissões corretas de execução (IAM Role).
3. **Mapeamento do Gatilho:** Vinculação dos eventos de objeto do bucket S3 como a origem geradora de chamadas para a Lambda.
4. **Validação e Testes:** Upload de arquivos reais, monitoramento da execução e análise de logs no **Amazon CloudWatch** para garantir o sucesso do script de automação.

## Insights Obtidos
A união do Amazon S3 com o AWS Lambda remove completamente a necessidade de manter servidores ligados 24 horas por dia apenas aguardando a chegada de arquivos para processamento. Essa abordagem Serverless reduz drasticamente o custo operacional da infraestrutura e garante escalabilidade automática imediata — o sistema funciona perfeitamente processando um único arquivo por dia ou milhares de uploads simultâneos por segundo.