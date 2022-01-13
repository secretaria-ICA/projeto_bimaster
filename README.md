# projeto_bimaster
# Modelo de otimização da programação para tarefas de manutenção em uma plataforma de petróleo, respeitando restrições de segurança e simultaneidade entre tarefas iNcompatíveis 

#### Aluno: Edson Dias da Costa (https://github.com/edsondcosta).

#### Orientador(/a/es/as): [Nome Sobrenome](https://github.com/link_do_github).
#### Co-orientador(/a/es/as): [Nome Sobrenome](https://github.com/link_do_github). <!-- caso não aplicável, remover esta linha -->

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

- Repositório do Projeto: https://github.com/edsondcosta/projeto_bimaster.git
---

### Resumo

- O PRESENTE PROJETO visa desenvolver um modelo de otimização da programação para tarefas de manutenção planejadas em uma plataforma de petróleo, para sua realização nos turnos de trabalho subsequentes. O modelo tem com objetivo maximizar o emprego da mão de obra disponível a bordo da plataforma, respeitando as restrições de segurança e simultaneidade entre tarefas iNcompatíveis de serem realizadas em proximidade no mesmo intervalo de tempo.

- Plataformas marítimas de produção são instalações de processo compactas, responsáveis pela elevação e processamento primário de hidrocarbonetos a elevadas vazões e pressões. Equipes de operação e manutenção convivem para manter a planta em condições de segurança e eficiência dentro dos limites estabelecidos no projeto. Tais equipes desempenham diversas atividades e operações simultâneas para atingir o objetivo de produzir com segurança. Exemplos: manobras de partida e parada de equipamentos de processo, geração de energia, controle de estabilidade, trabalhos de manutenção e reparo, operações com embarcações, movimentação de cargas, abastecimento de produtos químicos, pousos e decolagens de helicópteros, entre outras. 
- Concomitante com as tarefas operacionais, em cada plataforma diariamente são realizadas diversas atividades para manutenção e reparo, que podem envolver serviços a quente (ex: solda elétrica), abertura de equipamentos que operam com óleo ou gás inflamável, trabalhos elétricos, trabalhos em altura, trabalhos sobre o mar, operações de mergulho, entre outros.

- Trabalhos e Operações Simultâneas: Duas ou mais atividades ou tarefas com potencial interferência entre elas, ocorrendo ao mesmo tempo e no mesmo lugar, resultando em riscos adicionais.

---

### Condições antes da otimização:
- A programação dos trabalhos de manutenção da plataforma é realizada de maneira manual pelos planejadores, utilizando sistemas e planilhas sem recursos de otimização. 
- Por conta da forma manual de realização da programação e das restrições de simultaneidade, a alocação da mão de obra das equipes de manutenção sempre fica abaixo do HH disponível.
- Diariamente é realizada uma reunião de avaliação da simultaneidade com toda a liderança da plataforma. Por conta da forma manual de realização, essa reunião consome grande HH para discussão e reprogramação dos trabalhos identificados como incompatíveis para realização simultânea.
- Falhas na avaliação de simultaneidade podem ocorrer, sendo identificadas somente no momento de execução dos trabalhos. Quando essa condição ocorre, por questões de segurança é exigida a paralização de pelos menos um dos trabalhos incompatíveis, gerando ociosidade para a mão de obra alocada nestes trabalhos e desperdício de HH.

---

### Regras e Restrições

- As etapas programadas dentro de um mesmo serviço são sequenciais, não podemos ter inversão na ordem dos horários;
- Os serviços e etapas programadas de serviços diferentes podem ter sua sequência de execução alterada;
- ...

---

### Pendências
- ...

---

Matrícula: 201.190.263

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
