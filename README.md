# Otimizacao_da_Programacao_de-Servicos_de_Manutencao_em_uma_Plataforma_de_Petroleo_Incorporando_Criterios_de_Seguranca_e_Simultaneidade_entre-Tarefas_Incompativeis

#### Aluno: [Edson Dias da Costa](https://github.com/edsondcosta)

#### Orientador: [Felipe Borges](https://github.com/FelipeBorgesC)
#### Co-orientador: [Anderson Nascimento](https://github.com/insightds)

---

Trabalho apresentado ao curso de Pós-graduação [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão do curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

- Repositório do Projeto: https://github.com/edsondcosta/projeto_bimaster

---

## Resumo

- O presente projeto apresenta uma Prova de Conceito para otimização da programação de serviços de manutenção planejados em uma plataforma de petróleo, para sua realização nos turnos de trabalho subsequentes. O modelo tem como objetivo maximizar o emprego da mão de obra disponível a bordo da plataforma, incorporando critérios de segurança e simultaneidade entre tarefas incompatíveis de serem realizadas em proximidade no mesmo intervalo de tempo.

- Plataformas marítimas de produção são instalações de processo compactas, responsáveis pela elevação e processamento primário de hidrocarbonetos a elevadas vazões e pressões. Equipes de operação e manutenção convivem para manter a planta em condições de segurança e eficiência dentro dos limites estabelecidos no projeto. Tais equipes desempenham diversas atividades e operações simultâneas para atingir o objetivo de produzir com segurança. Exemplos: manobras de partida e parada de equipamentos de processo, geração de energia, controle de estabilidade, trabalhos de manutenção e reparo, operações com embarcações, movimentação de cargas, abastecimento de produtos químicos, pousos e decolagens de helicópteros, entre outras. 
- Concomitante com as tarefas operacionais, em cada plataforma diariamente são realizadas diversas atividades para manutenção e reparo, que podem envolver serviços a quente (ex: solda elétrica), abertura de equipamentos que operam com óleo ou gás inflamável, trabalhos elétricos, trabalhos em altura, trabalhos sobre o mar, operações de mergulho, entre outros.

- Trabalhos e Operações Simultâneas: Duas ou mais atividades ou tarefas com potencial interferência entre elas, ocorrendo ao mesmo tempo e no mesmo lugar, resultando em riscos adicionais.

- O modelo de otimização proposto parte de um Banco de Dados criado pelo autor, com tabelas de serviços, equipamentos e características de serviços, simulando a extração das informações a partir de sistemas transacionais de uma plataforma de petróleo. 
- A partir dessas informações o presente projeto irá estabelecer critérios de distância segura entre as tarefas com características de simultaneidade e eliminar sobreposição de horários das tarefas que não atendem aos critérios, seguindo um passo a passo (algoritmo) que será apresentado a seguir.

---

## O problema a ser otimizado
- Grande número de tarefas de manutenção planejadas diariamente, que podem possuir características que impedem sua realização em proximidade no mesmo intervalo de tempo. Como realizar a programação dessa demanda, de forma a maximizar o emprego da mão de obra disponível, respeitando os critérios de segurança e simultaneidade ?

### Condições antes da otimização
- A programação dos trabalhos de manutenção da plataforma é realizada de maneira manual pelos planejadores, utilizando sistemas e planilhas sem recursos de otimização;
- Por conta da forma manual de realização da programação e das restrições de simultaneidade, a alocação da mão de obra das equipes de manutenção sempre fica abaixo do HH disponível;
- Diariamente é realizada uma reunião de avaliação da simultaneidade com toda a liderança da plataforma. Por conta da forma manual de realização, essa reunião consome grande HH para discussão e reprogramação dos trabalhos identificados como incompatíveis para realização simultânea;
- Falhas na avaliação de simultaneidade podem ocorrer, sendo identificadas somente no momento de execução dos trabalhos. Quando essa condição ocorre, por questões de segurança é exigida a paralização de pelos menos um dos trabalhos incompatíveis, gerando ociosidade para a mão de obra alocada nestes trabalhos e desperdício de HH.

---

## A solução proposta 
- Estabelecer critérios de distância segura entre as tarefas com características de simultaneidade e eliminar sobreposição de horários das tarefas que não atendem aos critérios.

### Passo a passo da solução (algoritmo)
- Base de dados: Banco de dados transacional do sistema de manutenção de uma plataforma, contendo tabelas de serviços, equipamentos e características de trabalho (ver pasta [base_dados](https://github.com/edsondcosta/projeto_bimaster/tree/main/base_dados)).
	- Nota: O banco de dados foi elaborado pelo autor, sem utilizar dados reais ou sigilosos, de forma a tornar pública a divulgação do trabalho disponibilizado neste repositório.

1. Convencionar matriz de simultaneidade com distancias seguras para cada par de características de tarefas incompatíveis de serem realizadas em proximidade no mesmo intervalo de tempo;
2. Identificar as coordenadas x, y, z de cada equipamento da plataforma onde são realizadas as tarefas de manutenção;
3. Calcular a distância entre cada par equipamentos, com base em suas coordenadas utilizando a fórmula da distância entre dois pontos;
4. Separar a relação de tarefas de manutenção planejadas para um dia, com seus horários de realização previstos;
5. Identificar a distância entre cada par de tarefas, com base nas distâncias entre os equipamentos onde serão executadas (passo 3);
6. Identificar as características de cada tarefa de manutenção; 
	- Nota: Tarefas que não possuam características com impacto na simultaneidade, não irão entrar na análise nem no otimizador, pois podem ser programadas para qualquer horário.
7. Buscar na matriz de simultaneidade as distancias seguras convencionadas para cada par de características das tarefas planejadas para o dia selecionado;
8. Comparar a distância real entre as tarefas (passo 5) e a distância de segurança de suas características (passo 7);
9. Identificar a sobreposição de horários das tarefas programadas para o dia, com base em seus horários de início e fim previstos, utilizando fórmula de sobreposição de horários;
10. Identificar as tarefas com distância real menor que a distância segura de suas características (passo 8);
11. Identificar as tarefas que possuam simultaneamente as duas condições: a) sobreposição de horários (passo 9); b) distância real menor que a distância segura (passo 10); 
12. Utilizar otimizador para escolher novos horários de início, eliminando a sobreposição de horários dos pares de tarefas com distancia real menor que a distancia segura estabelecida para as suas características.

---

## Regras e restrições

### Restrições de precedência
- Dentro de um mesmo serviço, as etapas devem respeitar a sequência definida na planilha. Exemplo: a etapa com ID 1202202 somente deve    iniciar após o fim da etapa com ID 1202201, e assim sucessivamente. Essa restrição será estabelecida no otimizador: dentro das etapas de um mesmo serviço, serão inseridas restrições para que uma etapa inicie somente após o fim da etapa precedente.
- As etapas de um serviço não possuem restrição de precedência com etapas de outros serviços, mas devem atender as restrições de simultaneidade se os serviços forem incompatíveis conforme Matriz de Simultaneidade.

### Etapas com mais de uma característica de simultaneidade
-  Quando isso ocorre, uma mesma etapa pode impactar de formas distintas etapas de outros serviços sendo executados no mesmo intervalo de tempo. Essa possibilidade será modelada dentro das matrizes, gerando uma linha para cada característica com repetição das respectivas etapas associadas, de forma que sejam identificadas todas as combinações que se encaixem no critério estabelecido.

---
### A prova de conceito apresentada nesse projeto desenvolveu o trabalho da disciplina de Otimização de Planejamento, incorporando novas variáveis possíveis de ocorrer, visando a aplicação real:
- criadas tabelas relacionais de serviços, equipamentos e características de trabalho, simulando a extração de um bando de dados transacional de uma plataforma de petróleo;
- cada tarefa de manutenção a ser realizada pode ter mais de uma característica, o que aumenta as possibilidades de restrições de simultaneidade;
- para cada característica, pode haver mais de uma tarefa a ser realizada, o que também aumenta as possibilidades de restrições de simultaneidade;
- matriz de simultaneidade com mais características combinadas, com outras possiblidades de restrições de simultaneidade;
- utilizado modelo 3D de uma planta de processo: Fórmula da distância entre dois pontos com três dimensões;
- inseridas restrições de precedência entre os trabalhos planejados;

---
### Arquivos com a modelagem da solução
- Com base no passo a passo da solução (algoritmo) desenvolvido conforme itens anteriores, na pasta [modelo_prova_conceito](https://github.com/edsondcosta/projeto_bimaster/tree/main/modelo_prova_conceito) estão os arquivos com o Modelo de Otimização aplicado para três dias. 
- Cada dia (dia 1, dia 2, dia 3) possui combinação de serviços, etapas, características e regras de precedência distintas. 
- Para cada combinação pudemos observar resultados distintos quando rodamos o otimizador por Algoritmos Genéticos do Excel (Solver - Evolutionary). Os resultados estão descritos a seguir.

---
## Resultados Obtidos

### O modelo permite a eliminação das restrições de simultaneidade pela eliminação da sobreposição de horários. 
- No dia 1, como havia muitas restrições de precedência e tarefas repetidas devido possuírem mais de uma característica, o otimizador obteve 2% de melhoria na utilização da mão de obra alocada, aumentando a utilização de 263 para 272 horas, das 371 horas possíveis que foram alocadas para o dia. 
- No dia 2, como havia poucas restrições de precedência e nenhuma tarefa repetida por possuir mais de uma característica, o otimizador permitiu a utilização de 100% da mão de obra alocada, aumentando das 40 horas iniciais  (31%) para as 130 horas possíveis que foram alocadas para o dia. 
- No dia 3, como também havia poucas restrições de precedência e nenhuma tarefa repetida por possuir mais de uma característica, o otimizador também permitiu a utilização de 100% da mão de obra alocada, aumentando das 90 horas iniciais  (87%) para as 104 horas possíveis que foram alocadas para o dia. 
- A partir das coordenadas de cada trabalho e de suas características, o modelo permite identificar facilmente os pares de trabalhos que não atendem ao critério de distância segura entre eles.
- As reuniões diárias de avaliação da simultaneidade podem tornar-se mais reduzidas, liberando o HH da equipe envolvida em sua realização, considerando que a matriz identifica os pares de trabalhos que não atendem o critério de distância segura entre eles. 
- A otimização dos horários de início de cada trabalho permite maior utilização da mão de obra disponível, uma vez que remove a sobreposição de horários entre os pares de trabalhos incompatíveis para realização simultânea. 

---
## Conclusão
- A modelagem do problema e a aplicação do otimizador apresentaram resultados satisfatórios, embora muitas restrições (dia 1) possuam impacto negativo na eficiência do otimizador.
- Como possíveis desenvolvimentos para melhoria da Prova de Conceito, podemos ainda sugerir para trabalhos futuros: 
1) inserir avaliação da incerteza para a duração esperada de cada trabalho; 
2) Desenvolver o Modelo de Otimização em Python; 
3) Desenvolver Projeto em BI com dashboards sobre as interferências de simultaneidade que mais ocorrem, tipos de tarefas, equipamentos e áreas de trabalho na plataforma para identificar fragilidades etc.;
- O projeto está sendo discutido com uma empresa que faz a gestão de dados empresariais, visando a integração da solução com os módulos de Planejamento de Manutenção e Permissão de Trabalho utilizados em uma empresa de Óleo e Gás Offshore. As avaliações das reuniões de trabalho estão sendo promissoras para sua aplicação prática.

---

Matrícula: 201.190.263

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
