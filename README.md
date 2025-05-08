# Plataforma de Manutenção Preditiva Industrial

Bem-vindo ao repositório da Plataforma de Manutenção Preditiva Industrial! Esta solução tem como objetivo demonstrar uma arquitetura inicial para prevenção de falhas em linhas de produção, aplicando conceitos de IoT e Machine Learning.

---

## 📖 Sumário

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Arquitetura](#-arquitetura)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Estratégia de Coleta de Dados](#-estratégia-de-coleta-de-dados)
- [Como Executar (Modo Simulado)](#-como-executar-modo-simulado)
- [Planejamento e Papéis](#-planejamento-e-papéis)
- [Estrutura do Repositório](#-estrutura-do-repositório)
- [Contribuição](#-contribuição)
- [Licença](#-licença)

---

## 🎯 Sobre o Projeto

Paradas inesperadas em linhas de produção geram custos elevados e atrasos. Esta plataforma visa:

- Monitorar em tempo real parâmetros críticos (vibração, temperatura, umidade).
- Detectar anomalias operacionais via análise de dados e Machine Learning.
- Prever falhas antes que ocorram, ajudando na manutenção preditiva.
- Gerar alertas e relatórios automatizados para tomada de decisão.

Este repositório cobre a **Fase 3 do desafio**, focando em metodologia, arquitetura e tecnologias, sem exigir código funcional completo.

---

## 🚀 Funcionalidades Principais

- **Ingestão de Dados**: API de coleta via FastAPI (MQTT/HTTP).
- **Armazenamento**: Banco PostgreSQL (local ou AWS RDS).
- **Processamento**: Pipeline agendado executando modelos de ML (Scikit-learn/TensorFlow).
- **Visualização**: Dashboard interativo em React.js e Dash (Plotly) ou Grafana.
- **Alertas**: Relatórios em PDF e notificações (e-mail/webhook).

---

## 📐 Arquitetura

```text
[Sensores ESP32] --MQTT--> [API Coleta (FastAPI)] --> [PostgreSQL RDS]
                                        |
                                Agendamento (Lambda/EventBridge)
                                        v
                           [API Análise (FastAPI + ML)]
                                        |
                           Atualiza resultados no RDS
                                        |
            ------------------------------------------------------
            |                                                    |
   [Dashboard React/Dash]                                [Relatórios Automáticos]
```

---

## 🛠 Tecnologias Utilizadas

| Camada              | Ferramenta / Serviço                     |
|---------------------|------------------------------------------|
| Coleta de Dados     | Python, MQTT, ESP32 ou Simulador Python  |
| API Ingestão        | FastAPI                                  |
| Banco de Dados      | PostgreSQL (AWS RDS ou local)            |
| Machine Learning    | Scikit-learn, TensorFlow                 |
| Agendamento         | AWS Lambda + EventBridge ou Cron         |
| Dashboard           | React.js, Dash (Plotly) ou Grafana       |
| Infraestrutura      | AWS EC2, RDS, S3                          |
| Diagramação         | diagrams.net                             |

---

## 📊 Estratégia de Coleta de Dados

### Modo Simulado (recomendado nesta fase):

- Script Python (`simulator.py`) gera sinais de vibração, temperatura e umidade.
- Publicação periódica via HTTP/MQTT na API de coleta.

### Modo Real (Futuro MVP):

- ESP32 com sensores DHT22 e acelerômetro.
- Firmware em MicroPython enviando dados via MQTT.

---

## ▶️ Como Executar (Modo Simulado)

Clone o repositório:

```bash
git clone https://github.com/SEU_USUARIO/repositorio-preditiva.git
cd repositorio-preditiva
```

Crie um ambiente virtual e instale dependências:

```bash
python3 -m venv venv && source venv/bin/activate
pip install -r requirements.txt
```

Execute o simulador de dados:

```bash
cd simulator && python simulator.py
```

Suba a API de coleta:

```bash
cd api-coleta && uvicorn main:app --reload
```

Configure o banco (PostgreSQL) e ajuste `settings.py` com credenciais.

---

## 📅 Planejamento e Papéis

| Responsável        | Atividades Principais                                      |
|--------------------|-------------------------------------------------------------|
| Líder de Projeto   | Coordenação geral, revisão e comunicação com tutores       |
| Engenheiro de Dados| API de ingestão, simulação e modelagem do esquema de banco |
| Cientista de Dados | Desenvolvimento e validação de modelos de detecção         |
| Backend Engineer   | API de análise, agendamento de jobs e integração com ML     |
| Front-end Developer| Implementação do dashboard e gráficos interativos           |
| DevOps / Infra     | Provisionamento AWS, CI/CD e monitoramento                 |

### Cronograma (2 semanas):

- **Semana 1**: Configuração inicial, simulador e API de coleta.
- **Semana 2**: Pipeline de ML, protótipo de dashboard e documentação final.

---

## 📂 Estrutura do Repositório

```text
repo-root/
├── simulator/          # Simulador de dados (simulator.py)
├── api-coleta/         # FastAPI de ingestão (main.py)
├── api-analise/        # FastAPI de processamento e ML (main.py)
├── dashboard/          # Front-end React/Dash
├── infra/              # Scripts de infraestrutura (Terraform/CloudFormation)
├── docs/               # Diagramas e documentação extra
│   └── arquitetura.drawio
├── requirements.txt    # Dependências Python
└── README.md           # Este arquivo
```

---

## 🤝 Contribuição

1. Faça um fork deste repositório.
2. Crie uma branch com sua feature:

```bash
git checkout -b feature/nome-da-feature
```

3. Commit e push da sua branch:

```bash
git commit -m 'Descrição da feature'
git push origin feature/nome-da-feature
```

4. Abra um Pull Request.

---

## 📝 Licença

Este projeto está licenciado sob a MIT License. Consulte o arquivo LICENSE para mais detalhes.
