# 🌿 Monitoramento de Biomas — UERGS Litoral Norte

> Protótipo acadêmico client-side para registro e visualização de observações de monitoramento ambiental, com foco em Imbé/RS.

![Status](https://img.shields.io/badge/Status-Academic%20Prototype-blue)
![Platform](https://img.shields.io/badge/Platform-Web-lightgrey)
![Architecture](https://img.shields.io/badge/Architecture-Client--side-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)

## 🎯 Objetivo

O projeto explora uma interface web simples para apoiar o registro de observações e a organização de pontos de coleta, conectando os registros a dados geográficos em **GeoJSON** e visualizando-os com **Leaflet**.

A proposta é experimental e acadêmica: o foco está na organização dos dados e na integração entre formulário, tabela e informação geoespacial.

## 🚀 Funcionalidades

- Cadastro local de pesquisador, ponto, espécie/bioma e quantidade.
- Validação básica dos campos do formulário.
- Tabela dinâmica de registros.
- Contador de registros.
- Remoção de registros da sessão atual.
- Visualização das camadas `zonas_ecologicas.geojson` e `observacoes_pontos.geojson`.
- Mapa client-side com Leaflet.
- Ajuste automático do mapa quando existem feições GeoJSON.
- Mensagem explícita quando os GeoJSON estão vazios ou não podem ser carregados.

## 🔐 Segurança

A criação das linhas da tabela não utiliza interpolação de entrada do usuário em `innerHTML`. Os valores fornecidos pelo usuário são inseridos com `textContent` e APIs DOM, reduzindo o risco de XSS baseado em HTML injetado.

O formulário também aplica limites básicos de tamanho e validação de quantidade no cliente.

> **Importante:** validação client-side não é uma barreira de segurança para sistemas reais. Este projeto não possui backend, autenticação, autorização, persistência ou validação server-side.

O tratamento de erro do carregamento GeoJSON evita expor diretamente ao usuário detalhes internos da exceção, mantendo o diagnóstico técnico no console do navegador.

## 🗺️ Dados geográficos

Os arquivos GeoJSON fazem parte do repositório e são carregados com `fetch()`.

No estado atual, os arquivos podem estar sem feições. Isso é tratado como ausência de dados, e não como erro silencioso.

Para dados reais de campo, mantenha propriedades e coordenadas válidas no padrão GeoJSON e avalie previamente requisitos de privacidade, governança e sensibilidade das informações geográficas.

## ▶️ Execução local

Como o navegador pode bloquear `fetch()` de arquivos locais por CORS, execute um servidor HTTP simples na pasta do projeto:

```bash
python -m http.server 8000
```

Depois acesse `http://localhost:8000`.

## 🧱 Arquitetura

A aplicação é composta por uma página HTML com CSS e JavaScript embarcados, além dos arquivos GeoJSON do projeto.

**Dependência externa principal:** Leaflet 1.9.4 e os tiles do OpenStreetMap para a visualização cartográfica.

Não existe backend ou banco de dados neste repositório.

## 🎓 Contexto acadêmico

Projeto desenvolvido no contexto de atividades acadêmicas de Ciências Biológicas, com foco em organização de dados de monitoramento ambiental e integração com ferramentas de SIG.

## 📌 Estado atual

**Protótipo acadêmico funcional.**

O projeto já demonstra o fluxo básico de entrada local, renderização segura dos registros e visualização de dados GeoJSON. Ainda não deve ser tratado como sistema de coleta ou gestão de dados de produção.

### Evoluções necessárias para produção

- backend e banco de dados;
- autenticação e autorização;
- validação server-side;
- persistência e controle de concorrência;
- testes automatizados;
- tratamento geoespacial mais completo;
- trilha de auditoria;
- controles de privacidade e governança de dados;
- política de retenção e recuperação de dados;
- revisão das dependências externas e integridade dos recursos carregados.

## 📄 Licença

Este projeto é distribuído sob a **MIT License**. Consulte o arquivo [`LICENSE`](LICENSE) para os termos completos.
