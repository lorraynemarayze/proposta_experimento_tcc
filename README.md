# Trabalho Final: Proposta de Experimento para TCC

## 1. Identificação Básica

### 1.1 Título do experimento

Impacto de Falhas de Software na Segurança Operacional Aeronáutica: Uma Análise Empírica

### 1.2 ID / código

1465618/2025.2

### 1.3 Versão e histórico

| Versão | Data       | Descrição                     |
| ------ | ---------- | ----------------------------- |
| v1.0   | 21/11/2025 | Criação inicial do documento e definição do contexto. |


### 1.4 Datas

* Data de criação: 21/11/2025
* Data da última atualização: 21/11/2025

### 1.5 Autores

Lorrayne Marayze Silva de Oliveira - Estudante de Engenharia de Software - lorrayne.marayze@gmail.com 

### 1.6 Responsável principal (PI)

Lorrayne Marayze Silva de Oliveira

### 1.7 Projeto / produto relacionado

Este experimento está relacionado ao pré-desenvolvimento do Trabalho de Conclusão de Curso (TCC) do curso de Engenharia de Software para a disciplina de Medição e Experimentação de Software, com foco na análise empírica do impacto de falhas de software na segurança operacional aeronáutica, utilizando dados dos bancos ASRS e ECCAIRS.

---

## 2. Contexto e Problema

### 2.1 Problema / oportunidade

A crescente automação de sistemas aeronáuticos elevou a dependência de software em operações de voo, navegação, comunicação e gerenciamento de aeronaves. Entretanto, incidentes registrados na aviação mostram que falhas de software, incluindo erros de lógica, inconsistências de dados, comportamentos inesperados de sistemas embarcados e problemas de interface, continuam contribuindo para riscos operacionais.

O problema central é a escassez de análises empíricas sistemáticas que identifiquem, classifiquem e quantifiquem esses tipos de falha a partir de bases reais de incidentes. Sem esse entendimento, fabricantes, operadores e equipes de engenharia de software têm dificuldade em priorizar melhorias, reduzir vulnerabilidades e aperfeiçoar práticas de desenvolvimento seguro. Assim, a oportunidade consiste em investigar empiricamente falhas de software relatadas na aviação, gerando insights que apoiem decisões de engenharia e reforcem a segurança operacional.

### 2.2 Contexto Organizacional e Técnico

### **a) Domínio**

O estudo se situa no domínio da segurança operacional aeronáutica, área que busca compreender, prevenir e mitigar eventos que possam comprometer a integridade de voo. Dentro desse contexto, o software passou a desempenhar um papel central. Sistemas que antes eram essencialmente mecânicos e eletromecânicos gradualmente foram substituídos ou complementados por funções computacionais, muitas delas altamente automatizadas e interdependentes.

Grande parte dos sistemas críticos de bordo — como Flight Management Systems (FMS), autopilot e sistemas de navegação — depende de algoritmos que processam informações provenientes de diferentes sensores, calculam parâmetros de voo e atuam diretamente no controle da aeronave. Esses sistemas não atuam de forma isolada: o autopilot depende do FMS; o FMS depende de dados GNSS; os sistemas de proteção de envelope utilizam leituras de múltiplos instrumentos, como ângulo de ataque, velocidade e altitude.

Essa interconexão cria um ambiente em que falhas aparentemente pequenas no software podem gerar impactos desproporcionais. Por exemplo, uma simples inconsistência de dados pode resultar em cálculos incorretos de performance ou na ativação inadequada de proteções automáticas. Assim, garantir que o software opere de forma previsível, robusta e segura torna-se vital para a integridade do voo.

Para gerenciar essa complexidade crescente, o setor aeronáutico desenvolveu normas rigorosas que orientam todas as fases do ciclo de vida do software. A DO-178C estabelece critérios de desenvolvimento, verificação e certificação baseados no nível de criticidade da função, garantindo que sistemas com potencial de risco catastrófico recebam maior rigor. A ARP-4754A fornece diretrizes para o desenvolvimento integrado de sistemas, destacando a necessidade de alinhamento entre software, hardware e requisitos operacionais. Já a DO-330 complementa esses processos ao definir o padrão para ferramentas utilizadas na verificação de software crítico.

Nesse domínio, portanto, analisamos não apenas os sistemas individualmente, mas a forma como a engenharia de software, a certificação e a operação real se conectam para preservar a segurança operacional.

### **b) Ambiente**

A aviação moderna opera em um ambiente altamente dinâmico, onde o desempenho seguro depende da interação contínua entre humanos, máquinas, sensores e algoritmos. O cockpit contemporâneo é um ecossistema sofisticado, no qual diferentes softwares executam tarefas simultâneas, trocam informações e ajustam parâmetros em tempo real.

Nesse ambiente, o software atua como “cérebro digital” da aeronave, interpretando dados brutos de sensores, filtrando informações, detectando anomalias e apoiando pilotos em decisões críticas. Contudo, essa sofisticação também implica vulnerabilidades: uma falha de software pode se propagar rapidamente e se manifestar em múltiplos sistemas interligados.

Assim, incidentes relacionados a software podem surgir de diversos cenários operacionais, como:

* discrepâncias momentâneas entre sensores que levam o piloto automático a emitir comandos divergentes,

* cálculos incorretos de performance que afetam a decolagem ou subida inicial,

* perda temporária de referências de navegação devido a falhas de processamento GNSS,

* falhas de lógica em algoritmos de proteção que ativam alertas desnecessários ou deixam de disparar alertas essenciais.

Além disso, o ambiente operacional não é uniforme. As bases analisadas incluem relatos de diferentes contextos, como:

* aviação comercial, com alta automatização e rotinas padronizadas;

* aviação geral, onde aeronaves podem operar com menos redundância tecnológica;

* operações internacionais, envolvendo múltiplos espaços aéreos, regras distintas e condições atmosféricas variáveis.

Essas diferenças tornam a análise empírica ainda mais relevante, pois permitem identificar como falhas semelhantes podem ter impactos distintos dependendo do tipo de operação, nível de automação e interação piloto–sistema.

Nesse cenário complexo e interconectado, compreender como falhas de software surgem, se manifestam e afetam a segurança de voo é essencial para orientar melhorias tanto no desenvolvimento quanto na operação dos sistemas aeronáuticos.

### **c) Equipes**

O desenvolvimento, operação e investigação de falhas de software aeronáutico envolvem um ecossistema multidisciplinar. Cada grupo contribui para diferentes etapas do ciclo de vida do software e para a compreensão dos incidentes reportados.

** Engenheiros de software aeronáutico**
São responsáveis pela implementação de funções críticas, seguindo padrões rigorosos de desenvolvimento como DO-178C. Eles precisam garantir rastreabilidade, requisitos verificáveis e processos de teste formais. Seu trabalho influencia diretamente a confiabilidade dos sistemas embarcados.

** Equipes de certificação e conformidade**
Compostas por especialistas internos e externos (Designated Engineering Representatives – DERs), essas equipes avaliam se o software atende às normas e práticas de segurança. No contexto da pesquisa, elas fornecem a ponte entre o desenvolvimento e a operação, muitas vezes participando da análise pós-incidente.

** Pilotos, despachantes operacionais e operadores**
São a linha de frente na observação de falhas. Por lidarem diretamente com os sistemas em condições reais de voo, os relatos voluntários (como os enviados ao ASRS) capturam comportamentos que dificilmente seriam reproduzidos em laboratório ou testes de certificação.

** Analistas de segurança operacional**
Profissionais dedicados à análise de tendências, identificação de riscos e construção de recomendações sistêmicas. Eles utilizam bancos de dados internacionais para detectar padrões de falhas, e seu trabalho é chave para contextualizar incidentes envolvendo software.

** Órgãos reguladores (ANAC, FAA, EASA, ICAO)**
Criam diretrizes, supervisionam investigações e definem requisitos para mitigação de riscos. Também mantêm e alimentam bases de dados que permitem acessar relatos estruturados de anomalias em sistemas aeronáuticos.

Em conjunto, essas equipes formam uma cadeia que vai desde o projeto inicial até o monitoramento em campo, permitindo que a pesquisa tenha uma visão holística das falhas de software reportadas.

### **d) Tecnologias e Processos Relevantes**

A pesquisa se situa no cruzamento entre tecnologia embarcada, engenharia de software crítica e práticas de segurança operacional. Entre os elementos relevantes:

#### Metodologias de desenvolvimento seguro

Abordagens como o **V-Model** e processos **waterfall** rigorosos são amplamente utilizados na aviação devido à previsibilidade e rastreabilidade. Esses métodos estruturam o desenvolvimento em fases sequenciais, com foco forte em verificação e documentação, permitindo identificar falhas sistematicamente.

#### Adoção gradual de práticas modernas (CI/CD, automação de testes)

Embora menos comuns em sistemas críticos embarcados, práticas de DevOps começam a aparecer em softwares aeronáuticos não embarcados — como EFBs, sistemas de manutenção e ferramentas de suporte. Parte da literatura discute como essas práticas poderiam coexistir com requisitos da DO-178C, um aspecto conectado à análise de falhas reais.

#### Tecnologias embarcadas e ferramentas certificáveis

Sistemas como FMS, autopiloto, atuadores eletrônicos e módulos GNSS operam com alto nível de integração. Cada componente troca dados continuamente, o que significa que uma anomalia em software pode provocar efeitos em cascata, algo frequentemente observado nos relatos de incidentes.

#### Bancos internacionais de incidentes

A base da pesquisa empírica são bancos amplamente reconhecidos:

* **ASRS (Aviation Safety Reporting System – NASA/EUA)**
  Reúne relatos voluntários e anônimos, trazendo descrições ricas e narrativas operacionais detalhadas.

* **ECCAIRS / ADREP (ICAO / Europa)**
  Estruturas padronizadas de relatos oficiais, utilizadas por agências de investigação no mundo todo.

Esses bancos são essenciais para observar como o software realmente se comporta fora do ambiente controlado de testes, permitindo identificar falhas não previstas pelo processo de certificação.

### 2.3 Evidências Prévias

Vários estudos prévios indicam que a complexidade do software aeronáutico vem aumentando e, com ela, surgem novos desafios para a segurança operacional. Contudo, esses estudos apresentam lacunas que o tema proposto busca preencher.

#### Trabalhos sobre certificação e padrões (DO-178C, ARP-4754A)

A maior parte da literatura foca nos frameworks de desenvolvimento e certificação. São estudos mais teóricos, que descrevem procedimentos, mas raramente apresentam dados empíricos sobre falhas ocorridas em operação.

#### Pesquisas sobre automação de voo e dependência de software

Há publicações analisando casos de acidentes e incidentes envolvendo automação excessiva ou confusão do piloto diante de comportamentos inesperados do software. Ainda assim, muitas dessas análises são pontuais, focadas em eventos isolados.

#### Estudos sobre fatores humanos e interação homem–máquina

Alguns trabalhos destacam que erros atribuídos ao piloto às vezes têm origens em interfaces mal projetadas, mensagens ambíguas ou automatismos não intuitivos. Esse tipo de evidência reforça a importância de analisar relatos operacionais para identificar padrões de falhas.

#### Falta de pesquisas empíricas amplas

Apesar da existência de bancos como ASRS e ECCAIRS, poucos estudos fazem análises quantitativas e qualitativas combinadas especificamente sobre **falhas de software** — o que constitui uma lacuna claramente explorável no TCC.
A literatura costuma focar mais em falhas mecânicas, eventos meteorológicos ou erros operacionais.

Existe conteúdo teórico robusto sobre normas e processos, mas **há pouca exploração de dados reais de incidentes envolvendo software**. Por isso, uma análise empírica baseada em bancos internacionais representa uma contribuição concreta e bem alinhada ao curso de Engenharia de Software.


### 2.4 Referencial teórico

A dependência crescente de sistemas computacionais na aviação tem motivado uma série de estudos sobre segurança, confiabilidade e impacto de falhas de software em operações críticas. Pesquisas iniciais concentraram-se em compreender falhas estruturais em sistemas embarcados e em estabelecer metodologias de certificação, como a DO-178C. Os trabalhos clássicos (e.g., Storey, 1996; Knight, 2002) discutem como erros de software podem provocar propagação de falhas, perda de controle e comportamentos inesperados em sistemas críticos.

Com a popularização da automação avançada, estudos passaram a investigar falhas em subsistemas específicos, como Flight Management Systems (FMS), autopilot e sistemas de navegação. Pesquisas conduzidas por órgãos como FAA e EASA identificaram incidentes relacionados a inconsistências de dados, erros de lógica e falhas de integração entre sensores e software, reforçando a importância do desenvolvimento baseado em requisitos e verificação formal.

Nos últimos anos, trabalhos empíricos começaram a explorar bancos de dados de incidentes aeronáuticos, como o ASRS (EUA) e o ADREP/ECCAIRS (Europa), permitindo análises em larga escala. Estudos como os de Li et al. (2018) e Shappell & Wiegmann (2017) aplicaram técnicas de mineração de texto e classificação para identificar padrões em fatores humanos e falhas técnicas. Entretanto, apenas parte desses estudos aborda especificamente falhas de software, frequentemente tratadas de modo agregado sob categorias amplas como "malfunction" ou "automation issue".

Avanços metodológicos recentes incluem o uso de processamento de linguagem natural (NLP) para identificar automaticamente incidentes relacionados à automação e compreender erros de interface piloto-máquina. Apesar disso, a literatura ainda carece de uma taxonomia estruturada para falhas de software aeronáutico baseada em dados reais de incidentes — um contraste com outros domínios, como aprendizado de máquina, onde taxonomias específicas já foram desenvolvidas.

Além disso, poucos estudos realizam análises comparativas entre diferentes regiões ou bancos de dados, e quase nenhum investiga como falhas de software se manifestam operacionalmente em contextos distintos (e.g., aviação geral vs comercial, voo IFR vs VFR). A ausência de categorização sistemática dificulta entender a natureza, recorrência e impacto operacional dessas falhas.

Dessa forma, embora exista uma base teórica extensa sobre segurança de software e confiabilidade em sistemas críticos, há uma lacuna significativa em torno de estudos empíricos focados exclusivamente em falhas de software na aviação, especialmente aqueles baseados em bancos de dados reais de incidentes. Esse cenário justifica a necessidade de investigações que combinem análise empírica, classificação estruturada e avaliação do impacto operacional dessas falhas — objetivo central deste trabalho.

---

## 3. Objetivos e Questões (GQM)

### 3.1 Objetivo geral

Definido usando a estrutura GQM.

### 3.2 Objetivos específicos

O1, O2, O3 – metas claras e mensuráveis.

### 3.3 Questões de pesquisa / negócio

Q1, Q2, Q3 – perguntas que o experimento deve responder.

### 3.4 Métricas (GQM)

Métricas, unidades, definição e fonte dos dados.

---

## 4. Escopo e Contexto do Experimento

### 4.1 Escopo funcional / de processo

O que está incluído e excluído.

### 4.2 Contexto do estudo

Organização, projeto, criticidade, experiência dos participantes.

### 4.3 Premissas

Condições consideradas verdadeiras.

### 4.4 Restrições

Tempo, orçamento, ferramentas, acessos etc.

### 4.5 Limitações previstas

Limitações à generalização dos resultados.

---

## 5. Stakeholders e Impacto Esperado

### 5.1 Stakeholders principais

Grupos impactados ou interessados.

### 5.2 Expectativas

O que cada stakeholder espera obter.

### 5.3 Impactos no processo/produto

Consequências esperadas na operação e no produto.

---

## 6. Riscos, Premissas e Critérios de Sucesso

### 6.1 Riscos de alto nível

Riscos técnicos e de negócio.

### 6.2 Critérios de sucesso

Condições de go / no-go.

### 6.3 Critérios de parada antecipada

Situações para adiar ou cancelar antes da execução.

---

## 7. Modelo Conceitual e Hipóteses

### 7.1 Modelo conceitual

Relação entre fatores e respostas.

### 7.2 Hipóteses formais

* H0: Hipótese nula
* H1: Hipótese alternativa

### 7.3 Nível de significância e poder

Ex.: α = 0,05 e justificativa do tamanho da amostra.

---

## 8. Variáveis, Fatores e Objetos de Estudo

### 8.1 Objetos de estudo

Elementos analisados (tarefas, código, issues etc.).

### 8.2 Participantes

Perfil dos sujeitos.

### 8.3 Variáveis independentes

Fatores e seus níveis.

### 8.4 Tratamentos

Condições experimentais.

### 8.5 Variáveis dependentes

Resultados medidos.

### 8.6 Variáveis de controle

Variáveis mantidas constantes ou usadas como bloco.

### 8.7 Variáveis de confusão

Fatores que podem distorcer resultados.

---

## 9. Desenho Experimental

### 9.1 Tipo de desenho

Randomizado, blocos, fatorial etc.

### 9.2 Randomização

O que será randomizado e como.

### 9.3 Balanceamento e contrabalanço

Técnicas para manter grupos comparáveis.

### 9.4 Número de grupos e sessões

Quantidade e justificativa.

---

## 10. População, Sujeitos e Amostragem

### 10.1 População-alvo

Grupo real que se deseja representar.

### 10.2 Critérios de inclusão

Requisitos mínimos para participação.

### 10.3 Critérios de exclusão

Condições impeditivas.

### 10.4 Tamanho da amostra

Total e por grupo, com justificativa.

### 10.5 Método de seleção

Conveniente, sorteio, convite etc.

### 10.6 Treinamento dos sujeitos

Materiais e nivelamento de conhecimento.

---

## 11. Instrumentação e Protocolo Operacional

### 11.1 Instrumentos de coleta

Questionários, logs, planilhas, scripts.

### 11.2 Materiais de suporte

Guias, slides, instruções.

### 11.3 Procedimento experimental

Passo a passo completo do experimento.

### 11.4 Piloto

Escopo, critérios e possíveis ajustes.

---

## 12. Plano de Análise de Dados

### 12.1 Estratégia geral

Como cada questão será respondida pelos dados.

### 12.2 Métodos estatísticos

t-teste, ANOVA, regressão etc.

### 12.3 Tratamento de outliers e dados faltantes

Regras definidas antes da execução.

### 12.4 Análise qualitativa

Codificação, categorias, agrupamento.

---

## 13. Avaliação de Validade

### 13.1 Validade de conclusão

Ameaças e mitigação.

### 13.2 Validade interna

Causas alternativas e controle.

### 13.3 Validade de constructo

Aderência das métricas ao conceito medido.

### 13.4 Validade externa

Generalização dos achados.

### 13.5 Resumo

Ameaças mais críticas e ações de mitigação.

---

## 14. Ética, Privacidade e Conformidade

### 14.1 Questões éticas

Pressão, incentivos, uso de estudantes.

### 14.2 Consentimento informado

Forma de comunicação e registro.

### 14.3 Privacidade e proteção de dados

Anonimização, acesso e retenção.

### 14.4 Aprovações necessárias

Comitê de ética, jurídico, DPO etc.

---

## 15. Recursos, Infraestrutura e Orçamento

### 15.1 Recursos humanos

Pessoas e papéis.

### 15.2 Infraestrutura técnica

Ambientes, servidores, ferramentas.

### 15.3 Materiais e insumos

Licenças, dispositivos, documentos.

### 15.4 Orçamento estimado

Custos principais e fonte.

---

## 16. Cronograma e Riscos Operacionais

### 16.1 Macrocronograma

Datas e marcos principais.

### 16.2 Dependências

Tarefas que dependem de outras.

### 16.3 Riscos operacionais

Contingências e planos de ação.

---

## 17. Governança do Experimento

### 17.1 Papéis e responsabilidades

Quem decide, executa, revisa e é informado.

### 17.2 Ritos de acompanhamento

Checkpoints, reuniões e revisões.

### 17.3 Controle de mudanças

Como mudanças são solicitadas, aprovadas e registradas.

---

## 18. Documentação e Reprodutibilidade

### 18.1 Repositórios e nomeação

Onde ficam documentos, scripts e dados.

### 18.2 Templates

Modelos usados e sua localização.

### 18.3 Empacotamento para replicação

Como deixar organizado para futuras replicações.

---

## 19. Plano de Comunicação

### 19.1 Públicos e mensagens-chave

O que cada grupo precisa saber.

### 19.2 Canais e frequência

E-mail, reuniões, Slack/Teams etc.

### 19.3 Comunicação obrigatória

Eventos que exigem aviso formal.

---

## 20. Critérios de Prontidão (Definition of Ready)

### 20.1 Checklist de prontidão

Itens que devem estar prontos para iniciar.

### 20.2 Aprovações finais

Quem aprova e como o aceite é registrado.
