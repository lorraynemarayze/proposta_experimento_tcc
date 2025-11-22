# Plano de Experimento – Scoping e Planejamento

## 1. Identificação Básica

### 1.1 Título do experimento

Impacto de Falhas de Software na Segurança Operacional Aeronáutica: Um Experimento Empírico Baseado em Relatos de Incidentes

### 1.2 ID / código

1465618/2025.2

### 1.3 Versão e histórico

| Versão | Data       | Descrição                     |
| ------ | ---------- | ----------------------------- |
| v1.0   | 21/11/2025 | Criação inicial do documento e definição do contexto. |
| v2.0   | 22/11/2025 | Definição do escopo e objetivo. |
| v2.1   | 22/11/2025 | Definição dos stakeholders e riscos. |
| v2.2   | 22/11/2025 | Definição do desenho experimental, hipóteses, variáveis, etc. |
| v2.3   | 22/11/2025 | Definição da população, amostra, instrumentos e plano de análise. |

### 1.4 Datas

* Data de criação: 21/11/2025
* Data da última atualização: 22/11/2025

### 1.5 Autores

Lorrayne Marayze Silva de Oliveira - Estudante de Engenharia de Software - lorrayne.marayze@gmail.com 

### 1.6 Responsável principal (PI)

Prof. Danilo de Quadros Maia Filho

Papel: Orientador Acadêmico e Supervisor Metodológico

Instituição: Pontifícia Universidade Católica de Minas Gerais

### 1.7 Projeto / produto relacionado

Este documento descreve um experimento controlado de Engenharia de Software, desenvolvido no contexto da disciplina Medição e Experimentação de Software. O objetivo do experimento é investigar empiricamente como falhas de software contribuem para incidentes aeronáuticos, utilizando dados reais provenientes dos bancos internacionais ASRS e ECCAIRS.

A proposta define o desenho experimental, as variáveis analisadas e os procedimentos necessários para coletar, classificar e medir ocorrências relacionadas a anomalias de software em operações de voo.

---

## 2. Contexto e Problema

### 2.1 Problema / oportunidade

A crescente automação de sistemas aeronáuticos elevou a dependência de software em operações de voo, navegação, comunicação e gerenciamento de aeronaves. Entretanto, incidentes registrados na aviação mostram que falhas de software, incluindo erros de lógica, inconsistências de dados, comportamentos inesperados de sistemas embarcados e problemas de interface, continuam contribuindo para riscos operacionais.

O problema central é a escassez de análises empíricas sistemáticas que identifiquem, classifiquem e quantifiquem esses tipos de falha a partir de bases reais de incidentes. Sem esse entendimento, fabricantes, operadores e equipes de engenharia de software têm dificuldade em priorizar melhorias, reduzir vulnerabilidades e aperfeiçoar práticas de desenvolvimento seguro. Assim, a oportunidade consiste em investigar empiricamente falhas de software relatadas na aviação, gerando insights que apoiem decisões de engenharia e reforcem a segurança operacional.

### 2.2 Contexto Organizacional e Técnico

### **a) Domínio**

O estudo se situa no **domínio da segurança operacional** aeronáutica, área que busca compreender, prevenir e mitigar eventos que possam comprometer a integridade de voo. Dentro desse contexto, o software passou a desempenhar um papel central, sistemas que antes eram essencialmente mecânicos e eletromecânicos gradualmente foram substituídos ou complementados por funções computacionais, muitas delas altamente automatizadas e interdependentes. Grande parte dos sistemas críticos de bordo, como o _Flight Management Systems_ (FMS), autopilot e sistemas de navegação, dependem de algoritmos que processam informações provenientes de diferentes sensores, calculam parâmetros de voo e atuam diretamente no controle da aeronave. Esses sistemas não atuam de forma isolada: o autopilot depende do FMS; o FMS depende de dados _Global Navigation Satellite System_ (GNSS); os sistemas de proteção de envelope utilizam leituras de múltiplos instrumentos, como ângulo de ataque, velocidade e altitude.

Essa interconexão cria um ambiente em que falhas aparentemente pequenas no software podem gerar impactos desproporcionais. Por exemplo, uma simples inconsistência de dados pode resultar em cálculos incorretos de performance ou na ativação inadequada de proteções automáticas. Assim, garantir que o software opere de forma previsível, robusta e segura torna-se vital para a integridade do voo.

Para gerenciar essa complexidade crescente, foi desenvolvido normas que orientam todas as fases do ciclo de vida do software:
* **DO-178C** estabelece critérios de desenvolvimento, verificação e certificação baseados no nível de criticidade da função, garantindo que sistemas com potencial de risco catastrófico recebam maior rigor.
* **ARP-4754A** fornece diretrizes para o desenvolvimento integrado de sistemas, destacando a necessidade de alinhamento entre software, hardware e requisitos operacionais.
* **DO-330** complementa esses processos ao definir o padrão para ferramentas utilizadas na verificação de software crítico.

Nesse domínio, portanto, será analisado não apenas os sistemas individualmente, mas a forma como a engenharia de software, a certificação e a operação real se conectam para preservar a segurança operacional.

### **b) Ambiente**

A aviação moderna opera em um ambiente altamente dinâmico, onde o desempenho seguro depende da interação contínua entre humanos, máquinas, sensores e algoritmos. O _cockpit_ (cabine do piloto) contemporâneo é um ecossistema sofisticado, no qual diferentes softwares executam tarefas simultâneas, trocam informações e ajustam parâmetros em tempo real.

Nesse ambiente, o software atua como “cérebro digital” da aeronave, interpretando dados brutos de sensores, filtrando informações, detectando anomalias e apoiando pilotos em decisões críticas. Contudo, essa sofisticação também implica vulnerabilidades: uma falha de software pode se propagar rapidamente e se manifestar em múltiplos sistemas interligados. Assim, incidentes relacionados a software podem surgir de diversos cenários operacionais, como:

* discrepâncias momentâneas entre sensores que levam o piloto automático a emitir comandos divergentes,

* cálculos incorretos de performance que afetam a decolagem ou subida inicial,

* perda temporária de referências de navegação devido a falhas de processamento GNSS,

* falhas de lógica em algoritmos de proteção que ativam alertas desnecessários ou deixam de disparar alertas essenciais.

Além disso, o ambiente operacional não é uniforme. Por isso, as bases de dados que serão analisadas incluem relatos em diferentes contextos, como:

* aviação comercial, com alta automatização e rotinas padronizadas;

* aviação geral, onde aeronaves podem operar com menos redundância tecnológica;

* operações internacionais, envolvendo múltiplos espaços aéreos, regras distintas e condições atmosféricas variáveis.

Essas diferenças tornam a análise empírica ainda mais relevante, pois permitem identificar como falhas semelhantes podem ter impactos distintos dependendo do tipo de operação, nível de automação e interação piloto–sistema.

Nesse cenário complexo e interconectado, compreender como falhas de software surgem, se manifestam e afetam a segurança de voo é essencial para orientar melhorias tanto no desenvolvimento quanto na operação dos sistemas aeronáuticos.

### **c) Equipes**

O desenvolvimento, operação e investigação de falhas de software aeronáutico envolvem um ecossistema multidisciplinar, onde cada grupo contribui para diferentes etapas do ciclo de vida do software e para a compreensão dos incidentes reportados:

** Engenheiros de software**
São responsáveis pela implementação de funções críticas, seguindo padrões rigorosos de desenvolvimento como DO-178C. Eles precisam garantir rastreabilidade, requisitos verificáveis e processos de teste formais. Seu trabalho influencia diretamente a confiabilidade dos sistemas embarcados.

** Equipes de certificação e conformidade**
Compostas por especialistas internos e externos (Designated Engineering Representatives – DERs), essas equipes avaliam se o software atende às normas e práticas de segurança. 

** Pilotos, despachantes operacionais e operadores**
São a linha de frente na observação de falhas. Por lidarem diretamente com os sistemas em condições reais de voo, os relatos voluntários (como os enviados ao ASRS) capturam comportamentos que dificilmente seriam reproduzidos em laboratório ou testes de certificação.

** Analistas de segurança operacional**
Profissionais dedicados à análise de tendências, identificação de riscos e construção de recomendações sistêmicas. Eles utilizam bancos de dados internacionais para detectar padrões de falhas, e seu trabalho é importante para ajudar a para contextualizar incidentes envolvendo software.

** Órgãos reguladores (ANAC, FAA, EASA, ICAO)**
Criam diretrizes, supervisionam investigações e definem requisitos para mitigação de riscos. Também mantêm e alimentam bases de dados que permitem acessar relatos estruturados de anomalias em sistemas aeronáuticos.

Em conjunto, essas equipes formam uma cadeia que vai desde o projeto inicial até o monitoramento em campo, permitindo que a pesquisa tenha uma visão holística das falhas de software reportadas.

### **d) Tecnologias e Processos Relevantes**

A pesquisa se situa no cruzamento entre tecnologia embarcada, engenharia de software crítica e práticas de segurança operacional. Entre os elementos relevantes:

#### Metodologias de desenvolvimento seguro

Abordagens como o **V-Model** e o processo **waterfall** são rigorosos e amplamente utilizados na aviação devido à previsibilidade e rastreabilidade. Esses métodos estruturam o desenvolvimento em fases sequenciais, com foco forte em verificação e documentação, permitindo identificar falhas sistematicamente.

#### Adoção gradual de práticas modernas (CI/CD, automação de testes)

Embora menos comuns em sistemas críticos embarcados, práticas de DevOps começam a aparecer em softwares aeronáuticos não embarcados, como EFBs (Electronic flight bag, dispositivo eletrônico de gerenciamento de informações), sistemas de manutenção e ferramentas de suporte. Parte da literatura discute como essas práticas poderiam coexistir com requisitos da DO-178C, um aspecto conectado à análise de falhas reais.

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

A maior parte da literatura foca nos frameworks de desenvolvimento e certificação. São estudos mais teóricos, que descrevem procedimentos, mas raramente apresentam dados empíricos sobre falhas ocorridas em operação. A principal documentação que rege o desenvolvimento (e.g., RTCA/DO-178C, SAE ARP-4754A) estabelece o rigor, mas a garantia de segurança é baseada primariamente na conformidade do processo. Autores como Rushby (2009) discutem a insuficiência da conformidade processual para garantir a segurança no sentido mais amplo. Mesmo na Engenharia de Software Empírica mais recente, o foco é em processos de desenvolvimento (e.g., integração de metodologias ágeis em ambientes críticos, Tordrup Heeager & Nielsen, 2020), e não na análise de falhas operacionais do produto final.

#### Pesquisas sobre automação de voo e dependência de software

Há publicações analisando casos de acidentes e incidentes envolvendo automação excessiva ou confusão do piloto diante de comportamentos inesperados do software. O trabalho seminal de Sarter & Woods (1997) e as análises de Degani (2004) destacam a opacidade e a complexidade da automação de cabine. Além disso, a literatura recente aponta para a importância de investigar falhas em aviônicos digitais e a relação com vulnerabilidades sistêmicas (Kaspersky, 2025). Ainda assim, muitas dessas análises são pontuais, focadas em eventos isolados ou na interação humana, sem classificar as falhas de software de forma sistemática a partir de grandes bases de dados.

#### Estudos sobre fatores humanos e interação homem–máquina

Alguns trabalhos destacam que erros atribuídos ao piloto às vezes têm origens em interfaces mal projetadas, mensagens ambíguas ou automatismos não intuitivos. Modelos amplamente utilizados, como o HFACS, frequentemente atribuem a origem de falhas de design de software à categoria de 'condições latentes' (Latent Failures) ou 'erros de decisão' do piloto, conforme demonstrado em análises de ASRS (e.g., Shappell & Wiegmann, 2004). Esse tipo de evidência reforça a importância de analisar relatos operacionais, mas demonstra que a taxonomia de falhas usada por esses estudos é focada em fatores humanos, e não na raiz da falha de software.

#### Lacuna

Apesar da existência de bancos ricos como ASRS (Aviation Safety Reporting System) e ECCAIRS, poucos estudos realizam experimentações ou análises empíricas sistemáticas, quantitativas e qualitativas combinadas, especificamente sobre falhas de software, o que constitui uma lacuna a ser explorada.

* Foco Principal da Literatura Empírica: A vasta maioria das análises empíricas que exploram ASRS/ECCAIRS tem foco em categorias tradicionais: erros operacionais de pilotos e controladores (Herr, 2025; Marx & Graeber, 1994), falhas de manutenção (Boeing, 2014) e eventos ambientais ou mecânicos.
* A Superficialidade da Categoria 'Software': Embora o ASRS capture relatórios que mencionam problemas de software, a literatura costuma focar em falhas onde o software é apenas um fator contribuinte na cadeia de eventos, e não o objeto central da classificação empírica. A simples menção de um problema de software em um relato de incidente não constitui uma análise empírica de sua causa-raiz em termos de Engenharia de Software.

Existe conteúdo teórico robusto sobre normas e processos, mas há pouca exploração experimental de dados reais de incidentes especificamente para criar uma taxonomia empírica de falhas de software e quantificar seu impacto. Por isso, a experimentação proposta, baseada em bancos internacionais e usando técnicas de Engenharia de Software Empírica para classificar as causas-raiz de falha do código/lógica a partir dos relatos, representa uma contribuição bem alinhada à Engenharia de Software e Segurança Operacional.

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

![GQM](https://github.com/lorraynemarayze/proposta_experimento_tcc/blob/main/GQM.png)

### 3.2 Objetivos específicos

![Objetivos específicos](https://github.com/lorraynemarayze/proposta_experimento_tcc/blob/main/objetivos_especificos.png)
![Identificação de métricas](https://github.com/lorraynemarayze/proposta_experimento_tcc/blob/main/identifica%C3%A7%C3%A3o_metricas.png)

### 3.3 Questões de pesquisa / negócio

Essas são perguntas centrais que o experimento como um todo deve responder:

* **Q1:** Qual é a distribuição da frequência, tipo e causa-raiz das falhas que contribuem para incidentes aeronáuticos relatados nas bases ASRS e ECCAIRS?
* **Q2:** Quais são os sistemas embarcados, fases de voo e tipos de falha de software que apresentam a maior correlação com o Nível de Criticidade Operacional e exigem mais intervenções manuais da tripulação?
* **Q3:** Como os achados empíricos sobre os padrões de falha de software podem ser traduzidos em recomendações específicas para a melhoria dos processos de desenvolvimento, verificação e validação (como o DO-178C), visando a redução de vulnerabilidades sistêmicas?

### 3.4 Métricas (GQM)

| ID  | Métrica | Unidade | Descrição | Fonte de Dados |
|------|---------|----------|------------|----------------|
| **M1**  | Frequência absoluta de falhas de software | Contagem | Número total de incidentes classificados como relacionados a software. | ASRS / ECCAIRS |
| **M2**  | Proporção percentual de cada categoria de falha | % | Distribuição proporcional das falhas por categoria (lógica, dados, interface, integração). | ASRS / ECCAIRS + Codificação |
| **M3**  | Incidentes por subsistema aeronáutico | Contagem | Número de incidentes relacionados a FMS, Autopilot, GNSS etc. | ASRS / ECCAIRS |
| **M4**  | Percentual de falhas por subsistema | % | Proporção percentual das falhas por subsistema aeronáutico. | ASRS / ECCAIRS |
| **M5**  | Classificação do tipo de falha | Código | Classificação nominal do tipo de falha (lógica, interface, dados, integração). | Codificação manual |
| **M6**  | Percentual relativo de cada tipo de falha | % | Proporção percentual de cada tipo de falha em relação ao total. | ASRS / ECCAIRS + Codificação |
| **M7**  | Percentual de incidentes com impacto operacional | % | Incidentes com consequências visíveis (desvio, perda de automação etc.). | ASRS / ECCAIRS |
| **M8**  | Distribuição das consequências operacionais por tipo de falha | % | Proporção de consequências associadas a cada categoria de falha. | ASRS / ECCAIRS |
| **M9**  | Severidade média dos incidentes por tipo de falha | Índice | Grau médio de severidade conforme escalas ADREP/ASRS. | ASRS / ECCAIRS |
| **M10** | Incidentes por fase do voo | Contagem | Quantidade de incidentes por fase (decolagem, cruzeiro, pouso etc.). | ASRS / ECCAIRS |
| **M11** | Tempo de degradação operacional | Minutos | Duração da anomalia até o retorno à normalidade. | ASRS / ECCAIRS (quando disponível) |
| **M12** | Probabilidade condicional Falha × Consequência | Probabilidade | P(consequência X / falha Y). | ASRS / ECCAIRS |
| **M13** | Frequência de cada causa-raiz | Contagem | Quantidade de incidentes atribuídos a erro de lógica, requisito etc. | Codificação manual |
| **M14** | Percentual relativo de cada causa-raiz | % | Proporção de cada causa-raiz identificada. | Codificação manual |
| **M15** | Incidentes com contribuição humano–máquina | Contagem | Número de incidentes onde houve interação falha + fator humano. | ASRS / ECCAIRS + Codificação |
| **M16** | Incidentes com mensagens/alertas ambíguos | % | Proporção de falhas de interface com informação inadequada ao piloto. | ASRS / ECCAIRS + Codificação |
| **M17** | Consistência da classificação (Cohen’s Kappa) | 0–1 | Grau de concordância entre avaliadores na taxonomia. | Avaliação manual |
| **M18** | Recorrência dos padrões de falha | Contagem / % | Frequência de padrões críticos após clustering ou codificação axial. | Codificação manual / Análise |
| **M19** | Prioridade de melhoria (Impacto × Frequência) | Índice | Escore de priorização de vulnerabilidades. | Derivado das métricas anteriores |


---

## 4. Escopo e Contexto do Experimento

Analisar os relatos de incidentes aeronáuticos envolvendo falhas de software com o propósito de caracterizar, classificar e quantificar padrões de falhas e seus efeitos operacionais com respeito à frequência, tipologia, causas-raiz, severidade e impacto operacional sobre a tripulação e os sistemas embarcados do ponto de vista de pesquisadores e engenheiros de software no contexto de relatos provenientes das bases ASRS e ECCAIRS, referentes à aviação comercial e geral.

### 4.1 Escopo funcional / de processo

**Incluído (In Scope)**

O experimento abrange:

* Análise de relatos textuais de incidentes envolvendo falhas atribuídas a software embarcado.
* Classificação das falhas segundo taxonomias definidas (lógica, dados, interface, integração etc.).
* Identificação de causas-raiz, tipos de falha, subsistemas afetados, fase do voo e consequências operacionais.
* Aplicação de métricas GQM definidas previamente.
* Codificação manual para análise qualitativa para detecção de padrões.
* Avaliação de severidade e impacto operacional com base em ADREP/ASRS.
* Análise estatística básica (correlações, frequências, probabilidades condicionais).
* Extração de padrões e priorização de recomendações de engenharia.

**Excluído (Out of Scope)**

O experimento não inclui:

* Análise de incidentes sem componente de software.
* Testes laboratoriais, simulações em bancos de ensaio ou instrumentação real.
* Avaliação em nível de código-fonte ou auditoria de requisitos.
* Dados confidenciais ou proprietários de fabricantes.
* Inferências sobre desempenho de aeronaves específicas ou modelos comerciais.

### 4.2 Contexto do estudo

O experimento será conduzido no contexto de um estudo acadêmico experimental desenvolvido como parte da disciplina Medição e Experimentação, do curso de graduação da PUC Minas. Trata-se de uma atividade de pesquisa aplicada que antecede o Trabalho de Conclusão de Curso (TCC).

**Organização do estudo**

* O experimento não está associado a empresas, órgãos reguladores ou instituições aeronáuticas.
* Trata-se de um projeto acadêmico independente, cujo objetivo é aprender, aplicar e avaliar métodos de medição e experimentação em Engenharia de Software usando dados reais.

**Natureza do Projeto**

* O estudo segue o modelo GQM (Goal–Question–Metric).
* A abordagem é empírica e exploratória, permitindo identificar padrões de falhas relatadas em bases públicas.
* A experimentação será feita com análise combinada qualitativa e quantitativa.
* O estudo utiliza como artefatos bases textuais disponíveis publicamente (ASRS e ECCAIRS), aplicadas como dataset.

**Experiência dos participantes**

* A análise será realizada por um pesquisador iniciante, sem formação prévia em segurança aeronáutica.
* O conhecimento em Engenharia de Software irá guiar as análises. 
* Conhecimentos serão adquiridos durante o processo, baseando-se em taxonomias e referências documentadas.

**Criticidade**

* Embora o domínio aeronáutico seja de alta criticidade, o estudo não tem impacto operacional real, pois lida apenas com dados públicos e agregados.
* A análise busca compreender padrões de falhas relatadas, sem emitir conclusões técnicas sobre sistemas específicos ou fabricantes.

**Ambiente da pesquisa**

* Análise conduzida em ambiente acadêmico, com ferramentas convencionais de apoio à codificação.
* Não há infraestrutura especial nem acesso privilegiado a dados sensíveis.

### 4.3 Premissas

Para o experimento, assume-se que:

* Os relatos fornecidos pelas bases ASRS e ECCAIRS são fidedignos, ainda que baseados em auto-relato.
* É possível identificar e classificar falhas de software a partir dos textos.
* O período de coleta escolhido contém volume suficiente de incidentes relevantes.
* A taxonomia de falhas definida é adequada para o domínio.
* As métricas GQM podem ser avaliadas com os dados disponíveis.
* A análise qualitativa, mesmo considerando a variação de interpretação, permite detectar padrões significativos.

### 4.4 Restrições

O estudo está sujeito às seguintes limitações operacionais:

* Tempo limitado para codificação manual dos relatos.
* Acesso restrito a dados apenas das bases públicas.
* Orçamento inexistente, impedindo compra de ferramentas avançadas.
* Escopo textual, sem possibilidade de validar tecnicamente falhas reais nos sistemas.
* Dependência do conteúdo disponível, algumas variáveis podem não estar presentes em todos os relatos.

### 4.5 Limitações previstas

**Limitações metodológicas**

* Dados são baseados em auto-relato e podem ser incompletos ou subjetivos.
* Relatos podem conter ambiguidades que dificultam inferência sobre a falha real.
* A codificação manual introduz variabilidade humana (reduzida com Cohen’s Kappa).

**Limitações da generalização**

* Não é possível generalizar conclusões para todos os fabricantes, todas as aeronaves ou todas as operações.
* Falhas relatadas não representam necessariamente a incidência real, apenas a incidência percebida e reportada.
* Não há acesso aos detalhes técnicos dos sistemas embarcados, limitando inferências profundas.

---

## 5. Stakeholders e Impacto Esperado

### 5.1 Stakeholders principais

Os principais grupos interessados ou impactados pelo experimento são:

* **Estudante/pesquisador(a):**
Responsável pela condução do experimento, análise e documentação dos resultados.

* **Professor da disciplina “Medição e Experimentação” (PUC Minas):**
Interessados na correta aplicação dos métodos de medição, experimentação e análise empírica.

* **Instituição de ensino (PUC Minas):**
Beneficiária da produção acadêmica, e consolidação do processo de aprendizagem.

* **Comunidade acadêmica em Engenharia de Software:**
Interessada em estudos sobre falhas de software em sistemas críticos e aplicação de GQM.

* **Profissionais de software com interesse em sistemas críticos:**
Podem se beneficiar das recomendações geradas para processos de desenvolvimento, verificação e validação.

### 5.2 Expectativas

**Pesquisador(a)**
* Aprender e aplicar a abordagem GQM na prática.
* Desenvolver habilidades em codificação qualitativa e análise de métricas.
* Produzir um experimento reprodutível e bem documentado.

**Professor)**
* Verificar o domínio dos conceitos de experimentação.
* Avaliar a qualidade da definição de objetivos, métricas e análise.
* Garantir alinhamento com o conteúdo da disciplina.

**Instituição de ensino**
* Obter evidências de aprendizagem aplicada.
* Estimular a produção de experimentos empíricos.

**Comunidade acadêmica**
* Acesso a resultados que ilustram padrões de falhas de software em sistemas críticos.
* Possibilidade de replicar ou expandir o estudo.

**Profissionais da área**
* Obter insights sobre vulnerabilidades, causas recorrentes e oportunidades de melhoria.
* Aplicação de recomendações no contexto de engenharia de software crítico.

### 5.3 Impactos no processo/produto

**Impactos no processo**
* Consolidação de um processo de análise empírica baseado em GQM.
* Melhoria na capacidade de definir métricas alinhadas a objetivos concretos.
* Expansão do conhecimento sobre codificação de dados não estruturados.
* Desenvolvimento de competências metodológicas para experimentos futuros.

**Impactos no produto**
* Relatório estruturado com resultados claros e replicáveis.
* Taxonomia aplicada às falhas de software aeronáuticas.
* Conjunto de métricas que pode ser reutilizado em estudos posteriores.
* Identificação de padrões e possíveis recomendações preliminares.

---

## 6. Riscos, Premissas e Critérios de Sucesso

### 6.1 Riscos de alto nível

**Riscos técnicos**
* Volume insuficiente de dados úteis nas bases selecionadas.
* Dificuldade de interpretação dos relatos devido à linguagem técnica.
* Baixa consistência na codificação de falhas.
* Possível ambiguidade ou falta de detalhe nos dados públicos.

**Riscos de projeto/negócio**
* Tempo limitado para realizar codificação manual e análise.
* Escopo excessivo para o período da experimentação.
* Dependência de ferramentas gratuitas que podem limitar análises avançadas.

### 6.2 Critérios de sucesso

O experimento será considerado bem-sucedido se:
* Os objetivos definidos no GQM forem atendidos.
* Todas as perguntas forem respondidas com base em métricas definidas.
* A codificação for realizada com consistência suficiente para análise.
* O relatório final apresentar clareza, reprodutibilidade e coerência metodológica.
* As principais categorias de falha forem identificadas e quantificadas.
* As conclusões forem justificadas com evidências extraídas dos dados.

Esses critérios funcionarão como condições go/no-go para validação do experimento.

### 6.3 Critérios de parada antecipada

A execução poderá ser suspensa ou revista caso:
* O volume de relatos disponíveis seja insuficiente para análise estatística mínima.
* A codificação manual se mostre inviável dentro do período da experimentação.
* Haja inconsistência grave na taxonomia que inviabilize a classificação.
* O pesquisador não consiga interpretar adequadamente os relatos (necessitando redefinir abordagem).
* Ferramentas essenciais deixarem de funcionar ou não forem compatíveis com os dados.

---

## 7. Modelo Conceitual e Hipóteses

### 7.1 Modelo conceitual

| Categoria | Variável / Fator | Relação esperada |
|----------|------------------|------------------|
| Fatores principais | Tipo de falha (lógica, interface, dados, integração) | Pode afetar severidade, impacto e tipo de consequência operacional |
| | Subsistema afetado (FMS, Autopilot, GNSS etc.) | Pode influenciar tipo de impacto e criticidade |
| | Fase do voo | Pode alterar severidade e probabilidade de consequências |
| | Causa-raiz | Relacionada à recorrência e padrões mais críticos |
| Respostas | Severidade do incidente | Determinada pelo tipo e contexto da falha |
| | Tipo de consequência operacional | Associado ao tipo de falha e subsistema |
| | Impacto na operação da tripulação | Relacionado à fase de voo e natureza da falha |

Certos fatores aumentam a probabilidade de as falhas se manifestarem de maneira mais severa ou mais disruptiva para a operação.

### 7.2 Hipóteses formais

**Hipótese 1 – Tipo de falha → Severidade**
* **H0₁:** Não há associação entre o tipo de falha de software e a severidade do incidente.
* **H1₁:** Há associação entre o tipo de falha de software e a severidade do incidente.

Direção esperada: falhas de lógica e integração tendem a produzir maior severidade.

**Hipótese 2 – Subsistema → Consequência operacional**
* **H0₂:** O subsistema afetado não influencia o tipo de consequência operacional.
* **H1₂:** O subsistema afetado influencia o tipo de consequência operacional.
* 
Direção esperada: falhas em FMS e Autopilot tendem a gerar consequências mais disruptivas.

**Hipótese 3 – Fase do voo → Impacto operacional**
* **H0₃:** A fase do voo não está associada ao impacto operacional causado pela falha.
* **H1₃:** A fase do voo está associada ao impacto operacional.
  
Direção esperada: falhas em aproximação e decolagem tendem a produzir impactos maiores.

### 7.3 Nível de significância e poder

* **Nível de significância (α): 0,05 -**
Escolhido por ser o padrão em estudos empíricos exploratórios.

* **Poder estatístico desejado: ≥ 0,80 -**
O estudo buscará maximizar o número de relatos para atingir poder estatístico adequado.

* **Considerações sobre tamanho da amostra:**
O tamanho amostral é determinado pelo total de relatos disponíveis contendo falhas de software nas bases ASRS/ECCAIRS.
Por ser um estudo observacional, será utilizada toda a amostra disponível, reduzindo erro amostral.

---

## 8. Variáveis, Fatores e Objetos de Estudo

### 8.1 Objetos de estudo

| Objeto | Descrição |
|--------|-----------|
| Relatos de incidentes | Textos de ASRS/ECCAIRS contendo falhas de software |
| Categorias/taxonomias | Classificação de tipos de falha, causas e consequências |
| Variáveis codificadas | Atributos extraídos manualmente dos relatos |


### 8.2 Participantes

| Participante | Caracterização |
|--------------|----------------|
| Pesquisador principal | Estudante de Engenharia de Software da PUC Minas, não especialista em aviação |
| Avaliador secundário | Usado apenas para validação da codificação (Cohen’s Kappa) |

### 8.3 Variáveis independentes

| Variável (fator) | Tipo | Níveis / Valores |
|------------------|------|------------------|
| Tipo de falha | Nominal | lógica, interface, dados, integração |
| Subsistema afetado | Nominal | FMS, Autopilot, GNSS, Displays, Sensores |
| Fase do voo | Ordinal | Solo, Decolagem, Subida, Cruzeiro, Aproximação, Pouso |
| Causa-raiz | Nominal | lógica, requisito, integração, dado inconsistente |

### 8.4 Tratamentos

| Tratamento | Descrição |
|------------|-----------|
| T1 | Falhas de lógica em subsistemas críticos |
| T2 | Falhas de interface em fases críticas do voo |
| T3 | Erros de dados com impacto operacional percebido |
| T4 | Falhas de integração com perda de automação |

### 8.5 Variáveis dependentes

| Variável dependente | Tipo | Descrição |
|---------------------|------|-----------|
| Severidade | Ordinal | Grau de severidade do incidente |
| Tipo de consequência | Nominal | Ex.: desvio, perda de função, alerta falso |
| Impacto operacional | Ordinal | Aumento de carga de trabalho, confusão, etc. |
| Probabilidade condicional | Numérica | P(consequência | tipo de falha) |
| Recorrência | Numérica | Frequência de padrões de falha |

### 8.6 Variáveis de controle

| Variável | Por que controlar |
|----------|-------------------|
| Período da coleta | Evita efeitos temporais |
| Tipo de aeronave (grupo) | Diferenças entre modelos |
| Região / base de dados | Diferenças ASRS × ECCAIRS |

### 8.7 Variáveis de confusão

| Variável | Risco para o experimento |
|----------|---------------------------|
| Clareza do relato | Pode dificultar a identificação da falha |
| Experiência do piloto | Influencia a forma como descreve a ocorrência |
| Linguagem técnica variada | Pode gerar inconsistências na codificação |
| Diferenças entre bases | Estruturas distintas de dados |

---

## 9. Desenho Experimental

### 9.1 Tipo de desenho

Desenho observacional e correlacional, com análise fatorial das combinações observadas. Adequado porque não há manipulação deliberada de variáveis e os dados são históricos.

### 9.2 Randomização

Ainda que não exista randomização:
* A ordem dos relatos para codificação será embaralhada aleatoriamente para minimizar viés de ordem.
* A análise estatística usará toda a amostra, não exigindo alocação entre grupos.

### 9.3 Balanceamento e contrabalanço

* Grupos naturais (tipos de falha, fases etc.) podem ser desbalanceados, pois dependem da frequência real nas bases.
* O desbalanceamento será quantificado e reportado como limitação.
* Como não há tarefas sequenciais atribuídas a participantes humanos, contrabalanço não se aplica.

### 9.4 Número de grupos e sessões

| Elemento | Valor |
|----------|--------|
| Grupos | 4 grupos principais classificados por tipo de falha |
| Sessões | 1 sessão completa de codificação e análise |
| Justificativa | Natureza observacional: grupos surgem dos dados, não de manipulação |

---

## 10. População, Sujeitos e Amostragem

Este experimento não envolve participantes humanos, portanto a interpretação adequada é que os “sujeitos” são os relatos analisados, e o único operador é o pesquisador.

### 10.1 População-alvo

A população-alvo corresponde ao conjunto global de:
* Relatos de incidentes aeronáuticos que envolvem falhas de software, provenientes de sistemas de reporte voluntário (ASRS) e de bases oficiais de estado (ECCAIRS), relacionados à aviação comercial e geral.

### 10.2 Critérios de inclusão

Um relato será incluído se atender aos seguintes critérios:
* Contém referência textual explícita ou implícita a falha de software, automação, FMS, Autopilot, sensores digitais, alertas automatizados ou sistemas embarcados.
* Está completo o suficiente para permitir extração de informações mínimas (fase do voo, tipo de evento).
* Pertence a uma das bases consideradas: ASRS ou ECCAIRS.
* Está dentro do intervalo de tempo definido para a coleta.

### 10.3 Critérios de exclusão

Relatos serão excluídos se:
* Forem duplicados entre as bases.
* Não houver qualquer evidência de componente de software no evento.
* Possuírem dados insuficientes para codificação (ex.: relatos completamente vazios).
* Se referirem exclusivamente a falhas mecânicas, meteorológicas ou humanas sem envolvimento do software.

### 10.4 Tamanho da amostra

Como se trata de um estudo observacional:
* Amostra esperada total: todos os relatos relevantes encontrados.
* Amostra por grupo (tipo de falha): dependerá da distribuição real (não manipulável).

Toda a população disponível será utilizada, maximizando poder estatístico e robustez, já que não há custo marginal por sujeito adicional.

### 10.5 Método de seleção

Amostragem por conveniência estruturada, isto é, todos os relatos que atendem aos critérios serão coletados diretamente das bases públicas ASRS e ECCAIRS.

### 10.6 Treinamento dos sujeitos

Não aplicável, porque não há participantes humanos.

No entanto, para o operador do experimento:
* Será utilizado um protocolo de codificação previamente definido.
* O pesquisador estudará a taxonomia de falhas e exemplos antes de iniciar a codificação real.
* Será realizado um teste piloto de codificação com 5–10 relatos.

---

## 11. Instrumentação e Protocolo Operacional

### 11.1 Instrumentos de coleta

| Instrumento | Função |
|-------------|--------|
| Planilha de codificação (Excel/Google Sheets) | Registrar variáveis, códigos, métricas e atributos extraídos |
| Script Python | Auxiliar contagem, limpeza e análise quantitativa |
| Documentos PDF/HTML dos relatos | Fonte primária dos incidentes |
| Tabela de métricas GQM | Referência para coleta padronizada |
| Taxonomia de falhas | Guia para classificação sistemática |

### 11.2 Materiais de suporte

* Manual de codificação (codebook) com definições das categorias.
* Guia rápido do protocolo (passo a passo).
* Modelo da planilha pré-preenchida.
* Exemplos de codificação corretos.

### 11.3 Procedimento experimental

![Fluxograma](https://github.com/lorraynemarayze/proposta_experimento_tcc/blob/main/Fluxograma.png)

### 11.4 Piloto

Um piloto será realizado com 10 relatos selecionados aleatoriamente.

**Objetivos:**
* testar clareza da taxonomia,
* ajustar categorias,
* identificar dificuldades,
* validar consistência da planilha.

**Critérios de ajuste:**
* redefinição de categorias ambíguas;
* ajustes no codebook;
* padronização de termos;
* revisão de métricas difíceis de coletar.

---

## 12. Plano de Análise de Dados

### 12.1 Estratégia geral

Seguiremos com uma abordagem mista (qualitativa e quantitativa) e exploratória. O foco é primeiro quantificar a extensão do problema (Q1), depois avaliar a associação dos fatores (Q2), e, por fim, extrair insights práticos (Q3).

**Q1: Distribuição (Frequência, Tipo e Causa-raiz)**
* **Questão:** Qual é a distribuição da frequência, tipo e causa-raiz das falhas que contribuem para incidentes aeronáuticos relatados nas bases ASRS e ECCAIRS?
* **Estratégia:** Esta questão será respondida primariamente por meio da estatística descritiva após a conclusão da codificação manual.

| Passo | Métricas Chave | Método de Análise |
| :--- | :--- | :--- |
| Quantificação Bruta | M1, M10 | Contagem de incidentes (`M1`) para determinar o tamanho da amostra de falhas de software. A distribuição por fase de voo (`M10`) será mapeada. |
| Classificação | M2, M4, M6, M14 | Cálculo de Frequências Absolutas e Percentuais (`M2`, `M6`, `M14`) para cada nível das variáveis nominais (Tipo de Falha, Subsistema, Causa-raiz). Serão criados *gráficos de barras* e *tabelas de contingência* para visualização. |
| Validação | M17 | O Coeficiente Kappa de Cohen será calculado sobre uma sub-amostra para validar a consistência da codificação manual. |

**Q2: Associação (Fatores, Criticidade e Intervenção)**
* **Questão:** Quais são os sistemas embarcados, fases de voo e tipos de falha de software que apresentam a maior correlação com o Nível de Criticidade Operacional e exigem mais intervenções manuais da tripulação?
* **Estratégia:** Esta questão exige o uso da estatística inferencial (Testes de Associação) para validar as hipóteses formuladas e probabilidade condicional.

| Passo | Métricas Chave | Hipótese Relacionada | Método de Análise |
| :--- | :--- | :--- | :--- |
| Associação Fator × Resposta | M9, M8 | H1₁, H1₂, H1₃ | Uso de testes não-paramétricos (dada a natureza ordinal/nominal de Severidade, Impacto e Fase do Voo), como o Teste Qui-Quadrado ($\chi^2$) e/ou Teste de Kruskal-Wallis, para verificar se existe associação estatisticamente significativa entre as variáveis independentes (Tipo de Falha, Subsistema, Fase do Voo) e as variáveis dependentes (Severidade, Consequência, Impacto). |
| **Probabilidade e Risco** | M12 | - | Cálculo de Probabilidades Condicionais ($P(\text{consequência X} \mid \text{falha Y})$) para identificar quais tipos de falha levam, mais frequentemente, às consequências mais críticas (e.g., desvio de rota, perda de controle automático). |
| Interação Humana | M15, M16 | - | Análise de frequência e proporção de incidentes (`M15`, `M16`) que envolvem falhas na interface homem-máquina, confirmando a relevância do fator humano como mitigador ou agravante da falha de software. |

**Q3: Padrões e Recomendações**
* **Questão:** Como os achados empíricos sobre os padrões de falha de software podem ser traduzidos em recomendações específicas para a melhoria dos processos de desenvolvimento, verificação e validação (como o DO-178C)?
* **Estratégia:** Esta é a etapa de **Síntese e Indução**, combinando os resultados quantitativos (Q1 e Q2) com a análise qualitativa das narrativas.

| Passo | Métricas Chave | Método de Análise |
| :--- | :--- | :--- |
| Análise de Padrões | M18 | Aplicação de técnicas de Codificação Axial e Agrupamento (Clustering) nas narrativas textuais (qualitativo) para identificar *padrões recorrentes de falha* que transcendem a taxonomia inicial (e.g., "Falha de Lógica + Aproximação + Dados Inconsistentes"). |
| Priorização de Vulnerabilidades | M19 | Derivar o Índice de Prioridade de Melhoria (`M19`) multiplicando a Frequência da Causa-raiz pela Severidade Média (`M9`). Isso destacará onde o risco é maior (falhas raras, mas catastróficas, ou falhas frequentes, mas leves). |
| Recomendação | - | Discussão/Análise Indutiva: Tradução dos padrões priorizados e das causas-raiz identificadas em *recomendações específicas de Engenharia de Software*, sugerindo ajustes na ênfase dos processos de desenvolvimento (e.g., reforçar testes de integração, simulação de dados atípicos, refinamento de requisitos de interface). |

### 12.2 Métodos estatísticos

| Técnica | Justificativa |
|---------|----------------|
| Qui-Quadrado de Independência | Testar associação entre tipo de falha e severidade |
| Teste G ou Fisher (quando frequências forem baixas) | Alternativa ao Qui-quadrado |
| Cramér’s V | Medir força da associação |
| Análise de correlação ordinal (Spearman) | Para severidade e impacto operacional |
| Clustering (K-modes ou hierárquico) | Identificação de padrões de falha |
| Estatísticas descritivas completas | Tabelas, proporções, frequências |

### 12.3 Tratamento de outliers e dados faltantes

**Regras:**
* Se o relato não contiver informação mínima para codificação → excluir da análise.
* Valores faltantes parciais → registrar como “não informado” (categoria própria).
* Outliers textuais (relatos extremamente longos ou curtos) → mantidos, pois fazem parte da natureza dos dados.
* Não remover valores com base em resultado desejado (evitar vieses).

### 12.4 Análise qualitativa

Os dados qualitativos (textos dos relatos) serão analisados usando:
* Codificação aberta → identificar fragmentos relevantes.
* Codificação axial → agrupar códigos em categorias de falhas e causas-raiz.
* Codificação seletiva → identificar temas centrais e padrões recorrentes.

**Ferramentas possíveis:**
* Planilha manual,
* Python Script,

**Resultados qualitativos alimentam:**
* identificação de padrões,
* refinamento das métricas,
* explicação dos resultados quantitativos.

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

## 21. Referências
