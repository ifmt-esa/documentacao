# SonarQube

O SonarQube é uma ferramenta de revisão automática de código autogerenciada que sistematicamente ajuda a fornecer código limpo. Com ele é possível integrar ao seu fluxo de trabalho existente e detectar problemas em seu código para ajudar a realizar inspeções contínuas em seus projetos. A ferramenta analisa  mais de [30 linguagens de programação diferentes](https://rules.sonarsource.com/)  e se integra ao seu [pipeline de CI](https://docs.sonarqube.org/latest/analyzing-source-code/ci-integration/overview/) e  à [plataforma DevOps](https://docs.sonarqube.org/latest/devops-platform-integration/github-integration/) para garantir que seu código atenda aos padrões de alta qualidade.

## Quality Gates

Um Quality Gate é um conjunto de condições booleanas baseadas em medidas. Ele ajuda você a saber imediatamente se seus projetos estão prontos para produção. Idealmente, todos os projetos usarão o mesmo Quality Gate. O status do Quality Gate de cada projeto é exibido com destaque em sua página inicial.

O Quality Gate está em conformidade com a metodologia [Clean as You Code](https://docs.sonarqube.org/9.9/user-guide/clean-as-you-code/) , para que você se beneficie da abordagem mais eficiente para fornecer código limpo.

Ele garante que:

* Nenhum bug novo é introduzido
* Nenhuma nova vulnerabilidade é introduzida
* Todos os novos pontos de acesso de segurança são revisados
* Novo código é devidamente coberto por testes
* Sem linhas duplicadas

### Condições Principais

As condições presentes no Quality Gates são utilizadas para verificar se um projeto de software atende aos requisitos aceitáveis em termos de qualidade de código. No SonarQube, é possível configurar as seguintes condições em um Quality Gate:

* **Coverage (Cobertura):** Informam qual a porcentagem de seu código é coberta pelo conjunto de testes automatizados.

* **Duplicated Lines (Linhas Duplicadas) (%):** Mede a porcentagem de código duplicado no projeto, o que pode indicar falta de modularização ou outras questões de design.

* **Maintainability Rating (Classificação de manutenibilidade):** é uma medida de avaliação da capacidade do código de ser mantido e evoluído ao longo do tempo, com base em boas práticas de programação.
  
  O Maintainability Rating é calculado com base em uma combinação de outras métricas de código, como complexidade, duplicação, tamanho do código, coesão e acoplamento. Essas métricas são ponderadas e comparadas com uma escala de notas que varia de A a E, sendo A a nota mais alta e E a mais baixa.

  * A escala de classificação de Manutenibilidade pode ser declarada alternativamente, dizendo que, se o custo de correção pendente for:

    * <=5% do tempo que já passou no aplicativo, a classificação é A
    * entre 6 a 10% a classificação é um B
    * entre 11 a 20% a classificação é um C
    * entre 21 a 50% a classificação é um D
    * qualquer coisa acima de 50% é um E

* **Reliability Rating (Classificação de confiabilidade):** Avalia a confiabilidade do software em relação à ocorrência de falhas em tempo de execução. Ela usa uma escala de notas que varia de A a E, sendo A a nota mais alta e E a mais baixa.

  * A = 0 Bugs
  * B = pelo menos 1 Bug Menor
  * C = pelo menos 1 Bug Grave
  * D = pelo menos 1 Bug Crítico
  * E = pelo menos 1 Bug Bloqueador

* **Security Hotspots Reviewed (Pontos de acesso de segurança):** Um security hotspot destaca uma parte do código sensível à segurança que o desenvolvedor precisa revisar. Esses hotspots são identificados por meio da análise do código-fonte em busca de padrões específicos que podem indicar a presença de vulnerabilidades, como por exemplo, a utilização de funções inseguras de manipulação de strings.
  
* **Security Rating (Classificação de segurança):** Avalia o nível de segurança do código-fonte em relação a possíveis vulnerabilidades e ameaças de segurança.

  O Security Rating é baseado em várias métricas de segurança de código, como a presença de vulnerabilidades conhecidas, a cobertura de testes de segurança, a utilização de bibliotecas seguras e a existência de práticas de codificação segura. Essas métricas são combinadas e ponderadas, e a pontuação final varia de A a E, sendo A a nota mais alta e E a mais baixa.

  * A = 0 Vulnerabilidades
  * B = pelo menos 1 Vulnerabilidade Menor
  * C = pelo menos 1 Vulnerabilidade Maior
  * D = pelo menos 1 Vulnerabilidade Crítica
  * E = pelo menos 1 Vulnerabilidade de Bloqueador

Para mais detalhes acesse: <https://docs.sonarqube.org/latest/user-guide/metric-definitions/>

### Condições Extras

Aqui estão algumas outras condições que é possível configurar no SonarQube. Não é recomendado adicionar mais condições além das padrões, pois pode levar a gargalos no ritmo de desenvolvimento com benefício mínimo. Também corre o risco de um Quality Gate ser ignorado pois falhas frequentes podem causar um debate sobre quais condições priorizar.

Essas outras condições estão descrita abaixo:

* **Condition Coverage (Cobertura de condição):** Indica a porcentagem de fluxos de controle condicionais em um código-fonte que foram testados durante a execução de testes automatizados.

  Os fluxos de controle condicionais são estruturas de código que dependem de condições ou expressões booleanas, como if-else, switch-case, while e for. A cobertura de condição mede a proporção de fluxos condicionais que foram testados durante a execução dos testes automatizados em relação ao total de fluxos condicionais no código-fonte.

  Por exemplo, se um código tem 100 fluxos de controle condicionais e apenas 80 foram testados durante a execução de testes automatizados, a cobertura de condição seria de 80%.

* **Condition to Cover (Condição para cobrir):** Indica a quantidade de expressões booleanas condicionais em um código-fonte que foram identificadas como "cobríveis" pelos testes automatizados. Em outras palavras, "Condition to Cover" mede a quantidade de condições que deveriam ter sido cobertas por testes automatizados, mas não foram. Essa métrica é útil para identificar áreas do código que não foram adequadamente testadas e, portanto, apresentam maior risco de falhas ou bugs.

  Por exemplo, se um código tem 100 expressões booleanas condicionais e apenas 80 foram identificadas como "cobríveis" pelos testes automatizados, a métrica de "Condition to Cover" seria de 20 expressões booleanas condicionais que não foram testadas.

* **Line Coverage (Cobertura de linha):** Mostra a porcentagem de linhas de código-fonte que foram executadas durante a execução de testes automatizados. Em outras palavras, "Line Coverage" mede o nível de cobertura de testes para as linhas de código-fonte. A métrica indica quantas linhas de código foram realmente executadas durante a execução dos testes automatizados em relação ao total de linhas de código-fonte.

  Por exemplo, se um código tem 100 linhas e apenas 80 foram executadas durante a execução dos testes automatizados, a cobertura de linha seria de 80%.

* **Lines to Cover (Linhas a Cobrir):** Aponta o número total de linhas de código-fonte que devem ser cobertas pelos testes automatizados.

  Em outras palavras, "Lines to Cover" mede a quantidade de linhas de código-fonte que devem ser testadas durante a execução dos testes automatizados. Essa métrica é útil para avaliar a cobertura de testes para o código-fonte e identificar áreas do código que ainda não foram adequadamente testadas.

  Por exemplo, se um código tem 100 linhas de código-fonte e apenas 80 linhas foram identificadas como "cobríveis" pelos testes automatizados, a métrica de "Lines to Cover" seria de 20 linhas.

* **Uncovered Conditions (Condições não cobertas):** Revela o número de caminhos de execução que não foram cobertos pelos testes automatizados em uma determinada seção do código.

  Essa métrica é importante para avaliar a efetividade dos testes automatizados em detectar possíveis problemas ou erros no código, especialmente em seções que contêm condições e fluxos de controle.

  Por exemplo, suponha que um determinado trecho de código tenha duas condições (if-else) e que apenas a condição do "if" foi coberta pelos testes automatizados, enquanto a condição do "else" não foi testada. Nesse caso, a métrica "Uncovered Conditions" seria de 1, indicando que há um caminho de execução não testado.

* **Uncovered Lines (Linhas descobertas):** Atesta o número de linhas de código que não foram executadas pelos testes automatizados. Essas linhas podem representar fluxos de execução de código não testados ou potenciais problemas de qualidade que ainda não foram identificados pelos testes automatizados.

  Por exemplo, se uma seção do código-fonte contém 100 linhas de código e os testes automatizados cobrem apenas 80 delas, a métrica "Uncovered Lines" seria de 20 linhas. Isso significa que há ainda 20 linhas que não foram testadas pelos testes automatizados e que podem representar possíveis problemas de qualidade de código.

* **Duplicated Blocks (Blocos Duplicados):** Sinaliza a quantidade de código duplicado em um projeto. Quando uma seção de código é duplicada em várias partes do projeto, ela é considerada um "Duplicated Block".

* **Duplicated Lines (Linhas Duplicadas):** Determina a quantidade de linhas de código duplicadas em um projeto. Quando uma linha de código é copiada e colada em várias partes do projeto, ela é considerada uma "Duplicated Line".

* **Blocker Issues (Problemas com bloqueadores):** Reservada para problemas graves e críticos que devem ser corrigidos imediatamente para garantir a qualidade e a segurança do código.

  Os "Blocker Issues" são os problemas mais graves identificados pelo SonarQube e podem incluir vulnerabilidades de segurança, falhas críticas de qualidade de código e violações de melhores práticas de desenvolvimento. Esses problemas precisam ser corrigidos antes que o código seja enviado para produção, pois podem causar sérios problemas e comprometer a integridade do sistema.

* **Critical Issues (Questões críticas):** Essa categoria inclui problemas críticos que precisam ser corrigidos para garantir a qualidade do código e reduzir o risco de problemas de segurança e falhas críticas.

  Os "Critical Issues" são problemas importantes que precisam ser resolvidos o mais rápido possível, embora não sejam tão graves quanto os "Blocker Issues". Esses problemas podem incluir vulnerabilidades de segurança, falhas de qualidade de código que podem afetar a funcionalidade do sistema e violações de boas práticas de desenvolvimento.

* **Info Issues (Problemas de informação):** Essa categoria inclui problemas de menor importância que geralmente não afetam a segurança ou a funcionalidade do sistema, mas que ainda assim podem ser melhorados para aprimorar a qualidade do código.

  Os "Info Issues" geralmente incluem sugestões para melhorar o código, como usar melhores práticas de codificação, refatorar o código para melhorar a legibilidade ou reduzir a complexidade, ou remover código morto ou inútil. Esses problemas não afetam a segurança ou a funcionalidade do sistema, mas podem afetar a manutenibilidade ou a escalabilidade do código.

* **Issues (Problemas):** Refere-se a problemas de qualidade de código encontrados em um projeto de software. Esses problemas podem ser de várias categorias, como bugs, vulnerabilidades de segurança, dívida técnica, violações de padrões de codificação e outros.

  O SonarQube realiza uma análise estática do código fonte do projeto para identificar esses problemas de qualidade de código e classifica cada problema de acordo com sua gravidade. Cada problema é exibido no painel do SonarQube como um "issue", com uma descrição do problema, sua categoria, gravidade, localização no código-fonte e outras informações relevantes.

  Os issues no SonarQube são organizados em categorias, como Bugs, Vulnerabilities, Code Smells, Security Hotspots, entre outras. Cada categoria tem sua própria definição de problemas, critérios de classificação e regras de análise.

  Os issues podem ser classificados em diferentes níveis de gravidade, como Blocker, Critical, Major, Minor e Info. As categorias e níveis de gravidade ajudam a priorizar os problemas de qualidade de código para que os desenvolvedores possam focar nos problemas mais importantes primeiro.

* **Major Issues (Problemas maiores):** São problemas considerados de nível médio de gravidade e podem afetar a manutenção, legibilidade e desempenho do código.

  Alguns exemplos de "Major Issues" incluem:

  * Falta de comentários ou documentação adequada no código-fonte.
  * Uso excessivo de declarações de exceção ou exceções muito genéricas.
  * Falta de tratamento de erros ou validação de entrada de dados.
  * Uso de variáveis globais ou estáticas desnecessárias.
  * Uso inadequado de estruturas de controle de fluxo, como loops ou condicionais.

* **Minor Issues (Problemas menores):** São problemas considerados de baixo impacto e não afetam a funcionalidade ou a segurança do sistema.

  Alguns exemplos de "Minor Issues" incluem:

  * Uso inadequado de espaços em branco ou tabulações no código-fonte.
  * Nomes de variáveis mal formatados ou pouco descritivos.
  * Uso de construções de código desnecessárias ou redundantes.
  * Uso de declarações ou funções obsoletas ou desencorajadas.
  
  Embora esses problemas possam não ter um impacto significativo na qualidade do código, eles podem dificultar a leitura e compreensão do código, aumentando a complexidade e reduzindo a legibilidade.

* **Added Technical Debt (Dívida técnica adicionada):** Indica a quantidade de dívida técnica adicionada em um projeto de software. A dívida técnica é o custo futuro estimado de corrigir problemas de qualidade de código, como bugs, problemas de segurança, problemas de desempenho, etc.

  Cada vez que um desenvolvedor faz uma alteração no código que adiciona uma nova dívida técnica, a métrica "Added Technical Debt" é atualizada para refletir o valor dessa nova dívida técnica.

  Por exemplo, se um desenvolvedor adiciona uma nova funcionalidade ao código, mas a implementa de uma maneira que introduz um novo problema de segurança, isso adiciona uma dívida técnica ao projeto. O valor dessa nova dívida técnica é então adicionado à métrica "Added Technical Debt".

* **Code Smells:** Conjunto de problemas de qualidade de código que podem levar a problemas mais sérios no futuro. São indicadores de possíveis violações de boas práticas de programação, como redundância, falta de clareza e manutenibilidade, acoplamento excessivo, entre outros.

* **Technical Debt Ratio (TDR) (Índice de dívida técnica):** Avalia a qualidade do código de um projeto em relação ao seu nível de dívida técnica. A dívida técnica é uma metáfora para descrever o custo a longo prazo de manter um código de baixa qualidade.

  O TDR é calculado como a proporção entre o tempo necessário para corrigir todas as violações de qualidade de código detectadas pelo SonarQube e o tempo que seria necessário para implementar as funcionalidades adicionais necessárias sem corrigir essas violações.

  Em outras palavras, o TDR é a relação entre o tempo necessário para corrigir o código existente e o tempo necessário para desenvolver novas funcionalidades sem a necessidade de corrigir o código.

  Quanto mais alto o TDR, mais tempo seria necessário para corrigir as violações de qualidade de código, o que significa que há mais dívida técnica no projeto. Uma alta dívida técnica pode levar a problemas de manutenção, aumento dos custos e risco de bugs no futuro.

* **Bugs:** Permitem definir um limite para a quantidade de bugs que um projeto pode ter para ser considerado aceitável em termos de qualidade de código. Essas condições podem ser configuradas de acordo com a necessidade de cada projeto e podem ser definidas para diferentes níveis de gravidade, desde bugs críticos até bugs menores.

* **Reliability Remediation Effort (Esforço de remediação de confiabilidade):** Mede a quantidade de esforço necessário para corrigir os problemas de confiabilidade (ou seja, os bugs) identificados no código-fonte do projeto. Essa métrica é uma forma de avaliar o impacto dos bugs no projeto e determinar o esforço necessário para corrigi-los.

  O "Reliability Remediation Effort" é calculado a partir do número total de problemas de confiabilidade identificados no projeto e da estimativa de tempo necessário para corrigir cada um deles. Essa estimativa de tempo é baseada em uma fórmula que considera fatores como a complexidade do problema, a frequência de ocorrência e a experiência da equipe de desenvolvimento.

* **Vulnerabilities (Vulnerabilidades):** Indica a quantidade de problemas de segurança encontrados no código-fonte. Esses problemas podem ser vulnerabilidades conhecidas, como falhas de segurança, vulnerabilidades de criptografia, vulnerabilidades de autenticação, entre outras.

  O SonarQube fornece uma lista detalhada das vulnerabilidades encontradas, incluindo informações sobre o tipo de vulnerabilidade, o trecho de código onde ela ocorre, a gravidade da vulnerabilidade e as possíveis soluções para corrigir o problema.

  Ao configurar um Quality Gate, é possível definir um limite máximo de vulnerabilidades aceitáveis no código-fonte. Isso ajuda a garantir que o código seja seguro e livre de problemas de segurança conhecidos. Se o número de vulnerabilidades encontradas exceder esse limite, o Quality Gate irá falhar e a equipe de desenvolvimento deverá corrigir os problemas antes de continuar com o desenvolvimento.

* **Security Remediation Effort (Esforço de correção de segurança):** Avalia a qualidade e segurança do código de um projeto de software. Essa condição indica a quantidade de esforço estimado para corrigir as vulnerabilidades de segurança encontradas no código.

  O SonarQube calcula o 'Security Remediation Effort' com base no número e na gravidade das vulnerabilidades identificadas pelo software de análise estática. Esse valor é apresentado em minutos, representando o tempo que seria necessário para corrigir todas as vulnerabilidades encontradas.

* **Security Review Rating (Avaliação de revisão de segurança):** Mede a qualidade da análise de segurança realizada no código fonte do projeto. Essa análise é realizada com base em regras de segurança estabelecidas pela plataforma, que buscam identificar vulnerabilidades e riscos de segurança no código.

  O 'Security Review Rating' é calculado a partir da quantidade de vulnerabilidades identificadas pela análise de segurança do SonarQube e da gravidade de cada uma dessas vulnerabilidades. Quanto maior for a quantidade e gravidade das vulnerabilidades encontradas, menor será a pontuação do 'Security Review Rating', indicando que o projeto possui um maior risco de segurança.

* **Lines (Linhas):** Analisar diversas métricas relacionadas a essas linhas de código, com cobertura de código, dívida técnica, qualidade de código, entre outras. No Quality Gate, é possível definir condições em relação a essas métricas, incluindo o número mínimo ou máximo de linhas de código que um projeto deve ter para ser considerado aceitável em termos de qualidade.
