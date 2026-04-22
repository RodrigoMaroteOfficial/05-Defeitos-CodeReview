📦 Relatório Final

Atividade: Bug Report Profissional + Code Review Guiado
Curso: Qualidade de Software
Professor: Prof. Claudio Nunes

👥 Identificação da dupla
Nome completo	RA	GitHub
Gustavo Dias	226851	--------
Rodrigo Marote	200242	@RodrigoMaroteOfficial
Leonardo Guimarães 200624 --------

Ambiente de testes: Chrome no Windows 11, rodando localmente

📋 Sumário
Parte A — Bug Reports
Parte B — Code Review
Reflexão final
Declarações
Parte A — Bug Reports
🐛 Bug 1 — Contador de tarefas pendentes errado

Severidade: Alta
Prioridade: Alta

Descrição:
O número de tarefas pendentes fica maior do que o correto quando tem tarefa com prioridade 5.

Passos para Reprodução:

Criar uma tarefa com prioridade 5
Não marcar como concluída
Ver o contador de pendentes

Resultado Esperado:
Mostrar 1 tarefa pendente

Resultado Atual:
Mostra 2 tarefas pendentes

Evidências:
O número exibido não bate com a quantidade real

Causa (código):

pendentes = pendentes + urgentes;
🐛 Bug 2 — Permite criar tarefa sem título

Severidade: Média
Prioridade: Alta

Descrição:
O sistema deixa criar tarefa sem título, ficando um item vazio na lista.

Passos para Reprodução:

Deixar o campo título vazio
Clicar em adicionar tarefa

Resultado Esperado:
Não permitir criar tarefa

Resultado Atual:
Cria tarefa em branco

Evidências:
Aparece uma tarefa sem nome

Causa (código):

const titulo = inputTitulo.value.trim();
🐛 Bug 3 — Ordenação por prazo errada

Severidade: Média
Prioridade: Média

Descrição:
As tarefas não ficam ordenadas corretamente pela data.

Passos para Reprodução:

Criar tarefas com datas diferentes
Ver a ordem da lista

Resultado Esperado:
Ordem correta por data

Resultado Atual:
Ordem meio errada

Evidências:
Datas fora de ordem

Causa (código):

localeCompare
Parte B — Code Review
Resumo
#	Linha	Dimensão	Rótulo	Severidade
1	~140	Lógica	Contagem errada	Alta
2	~40	Validação	Falta validação	Alta
3	~115	Lógica	Ordenação incorreta	Média
4	~30	Robustez	Pode dar NaN	Média
5	~95	Manutenibilidade	Evento inline	Média
6	~70	UX	Sem confirmação	Baixa
Findings detalhadas

1. Contagem errada (Alta)
Tá somando tarefas urgentes duas vezes, o que deixa o número de pendentes maior que o real.

2. Falta validação (Alta)
O sistema deixa criar tarefa sem título, o que não deveria acontecer.

3. Ordenação incorreta (Média)
A ordenação usa string em vez de data, então pode ficar errado.

4. Possível NaN (Média)
O parseInt pode gerar NaN se o valor vier errado.

5. Evento inline (Média)
Uso de onclick/onchange direto no HTML não é uma boa prática.

6. Sem confirmação (Baixa)
O botão de limpar tudo apaga tudo direto sem perguntar.

💭 Reflexão final

Qual dimensão do checklist foi mais difícil aplicar? Por quê?

A parte de lógica foi a mais difícil, porque precisa entender o que o código faz de verdade. Não é só ler, tem que pensar no comportamento. O bug da contagem foi o mais complicado de perceber.

O que vocês fariam diferente se revisassem o código novamente?

Testar mais a aplicação antes de analisar o código. Isso ajuda a encontrar os erros mais rápido. Também prestar mais atenção nos detalhes da lógica.

📣 Declarações
Uso de IA como parceiro de trabalho
 Não usamos IA nesta atividade.
X Usamos IA para esclarecer conceitos teóricos.
 Usamos IA para revisar a redação dos bug reports.
 Usamos IA para discutir se um achado era ou não um defeito.
X Uso específico: ajuda para identificar bugs e organizar o relatório
Declaração de autoria

Declaramos que este relatório é de autoria do trio, que exploramos
pessoalmente a aplicação da Parte A e lemos o código da Parte B. As
findings aqui registradas representam nosso próprio julgamento
técnico.
