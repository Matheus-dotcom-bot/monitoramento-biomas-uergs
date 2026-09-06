# 🌿 Monitoramento de Biomas — UERGS Litoral Norte

Sistema experimental para registro, organização e visualização de dados biológicos coletados em campo, com foco em Imbé/RS.

## 🎯 Objetivo

O projeto explora uma interface web simples para apoiar o registro de observações e a organização de pontos de coleta, conectando os registros a dados geográficos em GeoJSON.

## 🚀 Funcionalidades

- Cadastro local de pesquisador, ponto, espécie/bioma e quantidade.
- Tabela dinâmica de registros.
- Contador de registros.
- Visualização das camadas zonas_ecologicas.geojson e observacoes_pontos.geojson.
- Mapa client-side com Leaflet.
- Mensagem explícita quando o GeoJSON está vazio ou não pode ser carregado.

## 🔐 Segurança

A criação das linhas da tabela não utiliza mais interpolação de entrada do usuário em innerHTML.

Os valores fornecidos pelo usuário são inseridos usando textContent e APIs DOM, reduzindo o risco de XSS baseado em HTML injetado.

> Este projeto é uma aplicação client-side experimental. Não deve ser considerado um sistema de produção ou banco de dados seguro sem backend, autenticação, autorização, validação server-side e persistência adequada.

## 🗺️ Dados geográficos

Os GeoJSON atuais fazem parte do repositório e são carregados com fetch().

No estado atual, arquivos GeoJSON podem estar sem feições. Isso é tratado como ausência de dados, não como erro silencioso.

Para trabalhar com dados reais de campo, mantenha propriedades e coordenadas válidas no padrão GeoJSON.

## ▶️ Execução

Como o navegador pode bloquear fetch() de arquivos locais por CORS, execute um servidor HTTP simples na pasta do projeto:

    python -m http.server 8000

Depois acesse http://localhost:8000.

## 🎓 Contexto acadêmico

Projeto desenvolvido no contexto de atividades acadêmicas de Ciências Biológicas, com foco em organização de dados de monitoramento ambiental e integração com ferramentas de SIG.

## 📌 Estado

**Protótipo acadêmico funcional**, com integração client-side de GeoJSON e Leaflet.

Ainda faltam, para uma versão de produção:

- backend e banco de dados;
- autenticação/autorização;
- validação server-side;
- persistência;
- testes automatizados;
- tratamento de dados geoespaciais mais completo;
- controles de privacidade e governança de dados.