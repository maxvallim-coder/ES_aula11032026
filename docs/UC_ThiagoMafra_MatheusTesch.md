# Casos de Uso – Sistema FitPass Gym Management

## UC01 — Realizar Login
*Ator Principal*
Usuário

*Objetivo*
Permitir que o usuário acesse o sistema.

*Pré-condições*
Usuário deve possuir cadastro ativo.

*Pós-condições*
Sessão iniciada com sucesso.

*Fluxo Principal*
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.

*Fluxos Alternativos*
A1 — Senha incorreta:
O sistema exibe mensagem de erro.

A2 — Conta bloqueada:
O sistema impede o login.

*RF Relacionados*
RF01

*RNF Relacionados*
RNF02

*RN Relacionadas*
RN06


## UC02 — Cadastrar Aluno
*Ator Principal*
Recepcionista

*Objetivo*
Cadastrar novos alunos no sistema.

*Pré-condições*
Recepcionista autenticado.

*Pós-condições*
Aluno registrado no sistema.

*Fluxo Principal*
1. Recepcionista acessa cadastro.
2. Insere dados pessoais e contato.
3. Seleciona plano.
4. Sistema valida e registra o aluno.

*Fluxos Alternativos*
A1 — Dados incompletos:
Sistema solicita correção.

*RF Relacionados*
RF01

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN06


## UC03 — Atualizar Dados do Aluno
*Ator Principal*
Recepcionista

*Objetivo*
Atualizar dados cadastrais de alunos.

*Pré-condições*
Aluno cadastrado.

*Pós-condições*
Dados atualizados.

*Fluxo Principal*
1. Recepcionista busca aluno.
2. Atualiza dados.
3. Sistema salva alterações.

*Fluxos Alternativos*
A1 — Aluno não encontrado.

*RF Relacionados*
RF01

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN06


## UC04 — Gerenciar Planos
*Ator Principal*
Gerente

*Objetivo*
Criar ou editar planos da academia.

*Pré-condições*
Gerente autenticado.

*Pós-condições*
Plano atualizado.

*Fluxo Principal*
1. Gerente acessa menu de planos.
2. Cria ou edita plano.
3. Sistema salva alterações.

*RF Relacionados*
RF02

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN06


## UC05 — Registrar Pagamento
*Ator Principal*
Recepcionista

*Objetivo*
Registrar pagamento de mensalidade.

*Pré-condições*
Aluno cadastrado.

*Pós-condições*
Pagamento registrado.

*Fluxo Principal*
1. Recepcionista seleciona aluno.
2. Insere forma de pagamento.
3. Sistema confirma pagamento.

*Fluxos Alternativos*
A1 — Pagamento inválido.

*RF Relacionados*
RF03

*RNF Relacionados*
RNF02

*RN Relacionadas*
RN04, RN07


## UC06 — Verificar Regularidade do Aluno
*Ator Principal*
Sistema

*Objetivo*
Verificar se a mensalidade está em dia.

*Pré-condições*
Aluno cadastrado.

*Pós-condições*
Status atualizado.

*Fluxo Principal*
1. Sistema verifica vencimento.
2. Sistema define status do aluno.

*RF Relacionados*
RF04

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN01


## UC07 — Validar Acesso na Catraca
*Ator Principal*
Sistema de Catraca

*Objetivo*
Liberar ou bloquear acesso do aluno.

*Pré-condições*
Aluno possui RFID.

*Pós-condições*
Entrada registrada.

*Fluxo Principal*
1. RFID é lido.
2. Sistema verifica status.
3. Catraca libera ou bloqueia.

*Fluxos Alternativos*
A1 — Aluno inadimplente.

*RF Relacionados*
RF05

*RNF Relacionados*
RNF03, RNF06

*RN Relacionadas*
RN01


## UC08 — Agendar Aula
*Ator Principal*
Aluno

*Objetivo*
Reservar vaga em aula.

*Pré-condições*
Aluno ativo.

*Pós-condições*
Aula reservada.

*Fluxo Principal*
1. Aluno visualiza agenda.
2. Seleciona aula.
3. Sistema registra reserva.

*Fluxos Alternativos*
A1 — Aula lotada.

*RF Relacionados*
RF06

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN02


## UC09 — Cancelar Agendamento
*Ator Principal*
Aluno

*Objetivo*
Cancelar reserva de aula.

*Pré-condições*
Reserva existente.

*Pós-condições*
Reserva removida.

*Fluxo Principal*
1. Aluno acessa agenda.
2. Seleciona reserva.
3. Cancela agendamento.

*Fluxos Alternativos*
A1 — Prazo expirado.

*RF Relacionados*
RF06

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN03


## UC10 — Registrar Presença
*Ator Principal*
Instrutor

*Objetivo*
Registrar presença dos alunos.

*Pré-condições*
Aula em andamento.

*Pós-condições*
Presença registrada.

*Fluxo Principal*
1. Instrutor acessa lista.
2. Marca presença.
3. Sistema salva registro.

*RF Relacionados*
RF07

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN06


## UC11 — Registrar Avaliação Física
*Ator Principal*
Instrutor

*Objetivo*
Registrar avaliação física.

*Pré-condições*
Aluno ativo.

*Pós-condições*
Avaliação registrada.

*Fluxo Principal*
1. Instrutor seleciona aluno.
2. Insere dados da avaliação.
3. Sistema salva.

*Fluxos Alternativos*
A1 — Aluno irregular.

*RF Relacionados*
RF08

*RNF Relacionados*
RNF02

*RN Relacionadas*
RN05


## UC12 — Consultar Histórico de Avaliações
*Ator Principal*
Instrutor

*Objetivo*
Visualizar avaliações anteriores.

*Pré-condições*
Avaliações registradas.

*Pós-condições*
Histórico exibido.

*Fluxo Principal*
1. Instrutor busca aluno.
2. Sistema exibe histórico.

*RF Relacionados*
RF08

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN05


## UC13 — Gerar Relatório de Inadimplência
*Ator Principal*
Gerente

*Objetivo*
Identificar alunos inadimplentes.

*Pré-condições*
Gerente autenticado.

*Pós-condições*
Relatório exibido.

*Fluxo Principal*
1. Gerente seleciona relatório.
2. Sistema gera relatório.

*RF Relacionados*
RF09

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN01


## UC14 — Gerar Relatório de Alunos Ativos
*Ator Principal*
Gerente

*Objetivo*
Visualizar alunos ativos.

*RF Relacionados*
RF09

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN06


## UC15 — Gerar Relatório de Acessos
*Ator Principal*
Gerente

*Objetivo*
Consultar histórico de entradas.

*RF Relacionados*
RF09

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN06


## UC16 — Gerar Relatório de Ocupação das Aulas
*Ator Principal*
Gerente

*Objetivo*
Avaliar ocupação das turmas.

*RF Relacionados*
RF09

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN02


## UC17 — Enviar Notificação de Vencimento
*Ator Principal*
Sistema

*Objetivo*
Avisar alunos sobre vencimento da mensalidade.

*RF Relacionados*
RF10

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN07


## UC18 — Enviar Confirmação de Agendamento
*Ator Principal*
Sistema

*Objetivo*
Confirmar reserva de aula.

*RF Relacionados*
RF10

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN02


## UC19 — Notificar Liberação de Avaliação Física
*Ator Principal*
Sistema

*Objetivo*
Informar que nova avaliação pode ser feita.

*RF Relacionados*
RF10

*RNF Relacionados*
RNF03

*RN Relacionadas*
RN05


## UC20 — Consultar Agenda de Aulas
*Ator Principal*
Aluno

*Objetivo*
Visualizar horários disponíveis.

*Pré-condições*
Aluno autenticado.

*Pós-condições*
Agenda exibida.

*Fluxo Principal*
1. Aluno acessa agenda.
2. Sistema exibe horários disponíveis.

*RF Relacionados*
RF06

*RNF Relacionados*
RNF04

*RN Relacionadas*
RN02
