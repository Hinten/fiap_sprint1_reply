# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# Sprint 1 - Reply 

## Nome do grupo

## 👨‍🎓 Integrantes: 
- <a href="https://www.linkedin.com/in/alice-caroline-marinho">Alice Caroline Marinho de Assis</a>
- <a href="https://www.linkedin.com/in/pedro-lucas-458917207/">Pedro Lucas Tostes Silva</a>
- <a href="https://www.linkedin.com/company/inova-fusca">Nome do integrante 3</a> 
- <a href="https://www.linkedin.com/company/inova-fusca">Nome do integrante 4</a> 
- <a href="https://www.linkedin.com/company/inova-fusca">Nome do integrante 5</a>

## 👩‍🏫 Professores:
### Tutor(a) 
- <a href="https://www.linkedin.com/company/inova-fusca">Lucas Gomes Moreira</a>
### Coordenador(a)
- <a href="https://www.linkedin.com/company/inova-fusca">André Godoi Chiovato</a>


## 📜 Descrição

Este projeto visa o desenvolvimento de uma solução com foco em controle inteligente de processos, monitoramento, dashboards, alertas automáticos e sistemas de predição. Com isso, busca ajudar seus clientes a alcançarem excelência operacional, digitalizando seus ambientes e integrando dispositivos físicos e digitais para gerar dados e insights valiosos em tempo real.

## 🛠 Tecnologias utilizadas
- Python
- NumPy
- Pandas
- Matplotlib
- Scipy
- Seaborn
- C++
- Docker
- Oracle Database / PostgreSQL / Amazon RDS ou Firebase
- MqTT
- TensorFlow / PyTorch

## Considerações

**Como os dados serão coletados a partir de sensores?**

**R:** Os dados serão coletados a partir de sensores conectados a um ESP32 utilizando o protocolo MQTT. O ESP32 atuará como um cliente MQTT, publicando os dados dos sensores em tópicos específicos. O servidor MQTT, que pode ser hospedado em um serviço de nuvem ou em um servidor local, receberá essas mensagens e as encaminhará para uma fila a qual distribuirá para os serviços inscritos.

**Onde os dados serão armazenados?**

**R:** Os dados serão armazenados em um banco de dados em nuvem utilizando Amazon RDS (PostgreSQL) para dados estruturados (como métricas de sensores e logs) e Amazon S3 para dados brutos e arquivos temporários.
Por que essa escolha?
Escalabilidade Automática: O Amazon RDS ajusta capacidade conforme a demanda sem downtime, crucial para linhas de produção com picos de operação.
Alta Disponibilidade: Replicação multi-AZ garante 99,99% de uptime (SLA AWS), evitando paradas não planejadas.
Integração com IA: Compatibilidade nativa com serviços AWS como Lambda e SageMaker, facilitando a implementação de modelos de ML.
Custo-Benefício: Amazon S3 armazena dados brutos a baixo custo (US$ 0,023/GB/mês), enquanto RDS oferece backups automatizados gratuitos.

**Como será feita a integração com modelos de IA?**

**R:** A integração com modelos de IA será realizada através de APIs RESTful. Os dados coletados dos sensores serão enviados para um serviço que executará os modelos de IA, que podem ser implementados em Python utilizando bibliotecas como TensorFlow ou PyTorch. Os resultados das previsões serão retornados para o sistema e poderão ser armazenados no banco de dados ou utilizados para acionar alertas automáticos.

**Onde ocorrerá o processamento?**

**R:** O processamento dos dados coletados dos sensores ocorrerá em um servidor local ou na nuvem, dependendo da arquitetura escolhida. O uso de contêineres Docker permitirá que o sistema seja facilmente escalável e portátil, facilitando a implementação em diferentes ambientes. A escolha entre processamento local ou na nuvem dependerá das necessidades específicas da empresa, da infraestrutura disponível e preocupação com o sigilo dos dados.

## Requisitos Técnicos e Funcionais

1) Linguagens e ferramentas adequadas para análise de dados e Machine Learning

- Python: Linguagem de programação amplamente utilizada para análise de dados e Machine Learning, com bibliotecas como NumPy, Pandas, Matplotlib e Scipy.

2) Como os dados serão coletados, incluindo o tipo de coleta (simulada ou planejada via sensores como ESP32), armazenados e processados?

- Coleta de dados: Os dados serão coletados a partir de sensores conectados a um ESP32 utilizando o protocolo MQTT. O ESP32 atuará como um cliente MQTT, publicando os dados dos sensores em tópicos específicos. O servidor MQTT, que pode ser hospedado em um serviço de nuvem ou em um servidor local, receberá essas mensagens e as encaminhará para uma fila a qual distribuirá para os serviços inscritos. Um desses serviços será o de armazenagem de dados, que cuidará de sua armazenagem em um dos bancos de dados citados anteriormente.

3) Qual é a justificativa para a escolha de um banco de dados local ou na núvem? Qual é a sua escabilidade e viabilidade em relação ao projeto?

- A escolha entre um banco de dados local ou na nuvem deve considerar as necessidades específicas do projeto, a infraestrutura disponível e o nível de exigência quanto disponibilidade dos dados.

- Banco de dados local:
    A implementação local demanda um investimento inicial elevado, com custos associados à aquisição de servidores, infraestrutura de TI e mão de obra especializada para instalação e manutenção. Além disso, a         escalabilidade tende a ser limitada, exigindo novos aportes sempre que for necessário expandir a capacidade. No entanto, pode apresentar melhor desempenho em ambientes com alto volume de acesso interno e menor      dependência de conectividade externa.

- Banco de dados na nuvem:
    Soluções em nuvem oferecem maior flexibilidade e disponibilidade, o modelo de cobrança por demanda reduz o custo inicial e possibilita um controle mais eficiente do orçamento, com escalabilidade praticamente      automática conforme o crescimento do projeto. Além disso, os serviços em nuvem geralmente incluem atualizações e suporte técnico contínuo, o que reduz a necessidade de equipe técnica dedicada.

- Conclusão:
    Para o nosso projeto, os bancos de dados na nuvem apresentam maior viabilidade financeira e operacional, oferecendo uma solução escalável, com alta disponibilidade e menor custo inicial. Já os bancos de dados     locais podem ser considerados em situações específicas que demandem desempenho interno superior, desde que se justifique o investimento necessário.

4) Qual é o potencial de uso de serviços em nuvem (como AWS EC2, RDS, Lambda ou similares) na arquitetura proposta, mesmo que simulados na etapa atual?

A solução utilizará serviços em nuvem da AWS para garantir escalabilidade, baixo custo inicial e integração com IA. As principais escolhas são:
AWS IoT Core: Substitui servidores MQTT locais, gerenciando conexões dos sensores ESP32 com autenticação segura (TLS).
Amazon RDS (PostgreSQL): Armazena dados processados com alta disponibilidade e backups automáticos.
AWS Lambda: Executa modelos leves de Machine Learning (ex: detecção de anomalias) sem custo quando ocioso.
Amazon EC2: Roda modelos complexos (ex: TabTransformer) em instâncias escaláveis.
Por que nuvem?
Custo reduzido: Camada gratuita da AWS permite testes sem investimento inicial.
Pronto para produção: A mesma arquitetura escala para cenários reais sem modificações.
Simulação fácil: Dados simulados (ex: gerados com Pandas) podem ser enviados para a AWS IoT Core como se fossem de sensores reais.
Cenário realista: Para 10 sensores enviando dados a cada 5 segundos, o custo estimado é de US$ 50-100/mês – viável mesmo para pequenas indústrias.

5) Como os dados serão processados e analisados? Quais algoritmos de Machine Learning serão utilizados?

- Processamento de dados:    Os dados coletados dos sensores serão processados em tempo real utilizando Python, com bibliotecas como NumPy, Pandas e SciPy. O processamento incluirá etapas como limpeza, transformação, integração e filtragem:

    Limpeza: Esta etapa envolve a remoção de dados errôneos ou inconsistentes, como valores ausentes, duplicados ou fora de contexto. O objetivo é garantir que os dados sejam precisos e representem a realidade do       que está sendo medido pelos sensores.
  
    Transformação: Nessa fase, os dados são convertidos em formatos ou escalas mais adequados para análise. Isso pode incluir a normalização de valores, a conversão de variáveis categóricas em numéricas ou a            aplicação de funções matemáticas para ajustar os dados.
  
    Integração: Caso os dados venham de diferentes fontes ou sensores, a integração combina essas informações em um único conjunto, garantindo que todas as variáveis relevantes sejam consideradas de forma coesa e       sem sobreposição.
  
    Filtragem: Nessa etapa, são selecionados apenas os dados relevantes para o objetivo da análise. Isso pode envolver a remoção de valores fora de um intervalo específico ou a escolha de dados de interesse com         base em critérios predefinidos.

    Essas etapas garantirão que os dados estejam preparados de forma eficiente para as análises e modelagens posteriores.

- Análise de dados:    A análise dos dados será realizada utilizando algoritmos de Machine Learning, com uma combinação de modelos para tratamento em tempo real (ou em curtos intervalos de tempo) e modelos mais         robustos para volumes maiores de dados.

    Para dados processados em tempo real ou em curtos períodos de tempo (algumas vezes ao dia), será utilizada uma combinação dos modelos Random Forest e Isolation Forest, que rodarão localmente, oferecendo             respostas rápidas e eficazes.

    Já para grandes volumes de dados acumulados ao longo de períodos mais longos (a definir com o cliente), a análise será feita utilizando modelos robustos, como o TabTransformer ou o     XGBoost, executados em        nuvem.
  
    Esses modelos são capazes de lidar com grandes quantidades de dados e oferecem uma análise detalhada e precisa. Com a divisão entre modelos para análise em tempo real e modelos voltados a grandes volumes de         dados, o sistema oferecerá maior flexibilidade e eficiência, entregando respostas rápidas quando necessário e análises aprofundadas para o planejamento estratégico.

- Predição:    Os modelos de Machine Learning serão utilizados para prever eventos futuros com base nos dados dos sensores. As previsões geradas poderão acionar alertas automáticos, alimentar análises e gerar informações simples no dashboard interativo, além de embasar análises mais complexas para decisões específicas, como determinar se vale a pena realizar uma manutenção e qual o melhor momento para isso.

- Visualização de dados:    A visualização será feita com o uso de bibliotecas como Matplotlib e Seaborn. Gráficos e dashboards serão utilizados para apresentar os resultados das análises em tempo real e as previsões geradas pelos modelos. Esses recursos permitirão aos usuários monitorar as informações de forma eficiente, tanto para ações imediatas quanto para o planejamento de longo prazo.

- Alertas automáticos:    Os alertas automáticos serão acionados com base nas previsões dos modelos de Machine Learning. Eles poderão ser enviados por e-mail, SMS ou por meio de notificações em um aplicativo, permitindo uma resposta rápida. Esses alertas se subdividem em dois tipos: alertas de status em tempo real, gerados pelos modelos mais leves, e alertas e relatórios mais completos, baseados em análises de longo prazo realizadas pelos modelos mais robustos.

## Esboço da arquitetura
<p align="center">
<img src="assets/diagrama2.jpg" alt="Arquitetura do projeto" border="0" width=80% height=80%></a>
</p>

## Explicação da estratégia de coleta de dados

Não entendi, confirmar com o professor

## Plano inicial de desenvolvimento

 ✅ Fase 1: Coleta de Dados
- **Membro responsável:** Alice Caroline  
- 📆 *13 de Maio a 9 de Junho*
- Tarefas:
  - Coletar dados via MQTT usando ESP32
  - Armazenar em banco relacional ou NoSQL
  - Processamento inicial com Python (NumPy, Pandas, SciPy)

---

 📊 Fase 2: Análise de Dados
- **Membros responsáveis:** Vitor Albuquerque e Leonardo Sampaio
- 📆 *10 de Junho a 9 de Julho*
- Tarefas:
  - Análise com regressão, árvore de decisão e redes neurais
  - Visualização com Matplotlib e Seaborn
  - Criação de dashboards com insights

---

 🔮 Fase 3: Predição
- **Membro responsável:** Vitor Albuquerque
- 📆 *15 de Julho a 18 de Agosto*
- Tarefas:
  - Modelos preditivos com alertas automáticos
  - Envio de alertas por email, SMS ou app

---

 🔌 Fase 4: Integração com APIs
- **Membro responsável:** Lucas Basseto
- 📆 *18 de Agosto a 15 de Setembro*
- Tarefas:
  - Integração com APIs RESTful usando Flask ou FastAPI
  - Documentação com Swagger ou Postman
  - Testes automatizados com `pytest` ou `unittest`

---

 🐳 Fase 5: Contêineres Docker
- **Membro responsável:** Pedro Lucas
- 📆 *16 de Setembro a 13 de Outubro*
- Tarefas:
  - Dockerfile para cada serviço
  - Orquestração com Docker Compose
  - Testes automatizados dos containers

---

 ✅ Fase 6: Testes Automatizados
- **Membros responsáveis:** Pedro Lucas e Lucas Basseto
- 📆 *14 de Outubro a 03 de Novembro*
- Tarefas:
  - Testes unitários, integração e aceitação
  - CI para rodar testes automaticamente a cada commit

---

 📚 Fase 7: Documentação
- **Membro responsável:** Leonardo Sampaio
- 📆 *04 de Novembro a 17 de Novembro*
- Tarefas:
  - Documentação clara e atualizada
  - Uso de ferramentas automáticas de geração de doc

---

 🔧 Fase 8: Melhorias
- **Membros responsáveis:** Todos do grupo
- 📆 *20 de novembro a 7 de dezembro*
- Tarefas:
  - Testes de carga e estresse
  - Monitoramento e ajustes
  - Melhorias na interface



## 🗃 Histórico de lançamentos

* 0.1.0 - 04/05/2025
    *

## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/agodoi/template">MODELO GIT FIAP</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">Fiap</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>


