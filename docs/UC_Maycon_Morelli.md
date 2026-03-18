## UC01 — Cadastrar Aluno

### Ator Principal

Recepcionista

### Objetivo

Cadastrar um novo aluno no sistema.

### Pré-condições

* Recepcionista autenticado.

### Pós-condições

* Aluno registrado no sistema.

### Fluxo Principal

1. O recepcionista acessa a opção de cadastro.
2. O sistema solicita os dados do aluno.
3. O recepcionista preenche as informações.
4. O sistema salva o cadastro.

### Fluxos Alternativos

* **A1 — Dados incompletos:**
  O sistema solicita correção.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

## UC02 — Atualizar Dados do Aluno

### Ator Principal

Recepcionista

### Objetivo

Atualizar informações de um aluno.

### Pré-condições

* Aluno já cadastrado.

### Pós-condições

* Dados atualizados.

### Fluxo Principal

1. O recepcionista busca o aluno.
2. O sistema mostra os dados atuais.
3. O recepcionista altera as informações.
4. O sistema salva as alterações.

### Fluxos Alternativos

* **A1 — Aluno não encontrado:**
  O sistema informa erro.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

## UC03 — Criar Plano

### Ator Principal

Gerente

### Objetivo

Criar um novo plano de academia.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Plano cadastrado.

### Fluxo Principal

1. O gerente acessa a área de planos.
2. O gerente informa dados do plano.
3. O sistema salva o plano.

### Fluxos Alternativos

* **A1 — Dados inválidos:**
  O sistema solicita correção.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

## UC04 — Editar Plano

### Ator Principal

Gerente

### Objetivo

Modificar informações de um plano.

### Pré-condições

* Plano já cadastrado.

### Pós-condições

* Plano atualizado.

### Fluxo Principal

1. O gerente seleciona o plano.
2. O sistema mostra as informações.
3. O gerente altera os dados.
4. O sistema salva as alterações.

### Fluxos Alternativos

* **A1 — Plano inexistente:**
  O sistema informa erro.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

## UC05 — Registrar Pagamento

### Ator Principal

Recepcionista

### Objetivo

Registrar pagamento da mensalidade.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Pagamento registrado.

### Fluxo Principal

1. O recepcionista busca o aluno.
2. O sistema mostra a mensalidade.
3. O recepcionista confirma o pagamento.
4. O sistema registra o pagamento.

### Fluxos Alternativos

* **A1 — Falha no pagamento:**
  O sistema cancela a operação.

### RF Relacionados

* RF03

### RNF Relacionados

* RNF02

### RN Relacionadas

* RN04
* RN07

## UC06 — Verificar Regularidade

### Ator Principal

Sistema

### Objetivo

Verificar se o aluno está com pagamento em dia.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Situação atualizada.

### Fluxo Principal

1. O sistema verifica a data de pagamento.
2. O sistema define a situação do aluno.

### Fluxos Alternativos

* **A1 — Mensalidade vencida:**
  O sistema marca como inadimplente.

### RF Relacionados

* RF04

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN01

## UC07 — Liberar Acesso na Catraca

### Ator Principal

Aluno

### Objetivo

Entrar na academia utilizando RFID.

### Pré-condições

* Aluno com plano ativo.

### Pós-condições

* Entrada liberada ou bloqueada.

### Fluxo Principal

1. O aluno aproxima o cartão.
2. O sistema valida o cadastro.
3. O sistema libera o acesso.

### Fluxos Alternativos

* **A1 — Aluno inadimplente:**
  A catraca permanece bloqueada.

### RF Relacionados

* RF05

### RNF Relacionados

* RNF03
* RNF06

### RN Relacionadas

* RN01

## UC08 — Visualizar Aulas

### Ator Principal

Aluno

### Objetivo

Visualizar aulas disponíveis.

### Pré-condições

* Aluno autenticado.

### Pós-condições

* Lista de aulas exibida.

### Fluxo Principal

1. O aluno acessa o menu de aulas.
2. O sistema mostra horários disponíveis.

### Fluxos Alternativos

* **A1 — Nenhuma aula disponível:**
  O sistema informa ao aluno.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN02

## UC09 — Agendar Aula

### Ator Principal

Aluno

### Objetivo

Reservar vaga em uma aula.

### Pré-condições

* Aula disponível.

### Pós-condições

* Reserva registrada.

### Fluxo Principal

1. O aluno escolhe a aula.
2. O sistema verifica vagas.
3. O sistema confirma a reserva.

### Fluxos Alternativos

* **A1 — Aula lotada:**
  O sistema bloqueia o agendamento.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN02

## UC10 — Cancelar Agendamento

### Ator Principal

Aluno

### Objetivo

Cancelar reserva de aula.

### Pré-condições

* Aula previamente reservada.

### Pós-condições

* Reserva cancelada.

### Fluxo Principal

1. O aluno acessa suas reservas.
2. O aluno seleciona cancelar.
3. O sistema confirma o cancelamento.

### Fluxos Alternativos

* **A1 — Cancelamento fora do prazo:**
  O sistema bloqueia o cancelamento.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN03

## UC11 — Registrar Presença

### Ator Principal

Instrutor

### Objetivo

Registrar presença em aula.

### Pré-condições

* Aula em andamento.

### Pós-condições

* Presença registrada.

### Fluxo Principal

1. O instrutor acessa a aula.
2. O sistema mostra alunos inscritos.
3. O instrutor marca presença.

### Fluxos Alternativos

* **A1 — Aluno ausente:**
  O sistema registra ausência.

### RF Relacionados

* RF07

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

## UC12 — Visualizar Lista de Presença

### Ator Principal

Instrutor

### Objetivo

Visualizar alunos inscritos em aula.

### Pré-condições

* Aula agendada.

### Pós-condições

* Lista exibida.

### Fluxo Principal

1. O instrutor seleciona a aula.
2. O sistema exibe os alunos inscritos.

### Fluxos Alternativos

* **A1 — Nenhum aluno inscrito:**
  O sistema informa ao instrutor.

### RF Relacionados

* RF07

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

## UC13 — Registrar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Registrar dados físicos do aluno.

### Pré-condições

* Aluno ativo.

### Pós-condições

* Avaliação salva.

### Fluxo Principal

1. O instrutor seleciona o aluno.
2. O instrutor registra peso e medidas.
3. O sistema salva os dados.

### Fluxos Alternativos

* **A1 — Aluno irregular:**
  O sistema bloqueia a avaliação.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF02

### RN Relacionadas

* RN05

## UC14 — Consultar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Consultar avaliações anteriores.

### Pré-condições

* Avaliação existente.

### Pós-condições

* Histórico exibido.

### Fluxo Principal

1. O instrutor busca o aluno.
2. O sistema mostra avaliações registradas.

### Fluxos Alternativos

* **A1 — Nenhuma avaliação registrada:**
  O sistema informa.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF02

### RN Relacionadas

* RN06

## UC15 — Gerar Relatório de Alunos

### Ator Principal

Gerente

### Objetivo

Visualizar relatório de alunos ativos.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente acessa relatórios.
2. O gerente seleciona alunos ativos.
3. O sistema gera o relatório.

### Fluxos Alternativos

* **A1 — Falha na geração:**
  O sistema informa erro.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN06

## UC16 — Gerar Relatório de Inadimplência

### Ator Principal

Gerente

### Objetivo

Visualizar alunos com pagamento atrasado.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente acessa relatórios.
2. Seleciona inadimplência.
3. O sistema gera relatório.

### Fluxos Alternativos

* **A1 — Nenhum aluno inadimplente:**
  O sistema informa.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN01

## UC17 — Gerar Relatório de Acessos

### Ator Principal

Gerente

### Objetivo

Visualizar histórico de entradas.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente acessa relatórios.
2. Seleciona histórico de acesso.
3. O sistema gera relatório.

### Fluxos Alternativos

* **A1 — Sem registros:**
  O sistema informa.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN06

## UC18 — Enviar Notificação de Pagamento

### Ator Principal

Sistema

### Objetivo

Avisar sobre vencimento da mensalidade.

### Pré-condições

* Mensalidade próxima do vencimento.

### Pós-condições

* Notificação enviada.

### Fluxo Principal

1. O sistema identifica mensalidade próxima do vencimento.
2. O sistema envia notificação ao aluno.

### Fluxos Alternativos

* **A1 — Falha no envio:**
  O sistema tenta novamente.

### RF Relacionados

* RF10

### RNF Relacionados

* RNF01

### RN Relacionadas

* RN07

## UC19 — Enviar Confirmação de Aula

### Ator Principal

Sistema

### Objetivo

Confirmar agendamento de aula.

### Pré-condições

* Aula agendada.

### Pós-condições

* Confirmação enviada.

### Fluxo Principal

1. O sistema registra o agendamento.
2. O sistema envia confirmação ao aluno.

### Fluxos Alternativos

* **A1 — Falha no envio:**
  O sistema tenta reenviar.

### RF Relacionados

* RF10

### RNF Relacionados

* RNF01

### RN Relacionadas

* RN02

## UC20 — Notificar Nova Avaliação Física

### Ator Principal

Sistema

### Objetivo

Informar disponibilidade de nova avaliação física.

### Pré-condições

* Avaliação anterior registrada.

### Pós-condições

* Notificação enviada ao aluno.

### Fluxo Principal

1. O sistema identifica necessidade de nova avaliação.
2. O sistema envia notificação ao aluno.

### Fluxos Alternativos

* **A1 — Falha no envio:**
  O sistema tenta novamente.

### RF Relacionados

* RF10

### RNF Relacionados

* RNF01

### RN Relacionadas

* RN05
