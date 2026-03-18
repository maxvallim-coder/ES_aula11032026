# Casos de Uso — Sistema FitPass Gym Management

---

# UC01 — Realizar Login

### Ator Principal

Usuário

### Objetivo

Permitir que o usuário acesse o sistema conforme seu perfil.

### Pré-condições

* Usuário deve possuir cadastro ativo no sistema.

### Pós-condições

* Sessão iniciada e permissões aplicadas conforme perfil.

### Fluxo Principal

1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema identifica o perfil do usuário.
4. O sistema redireciona para a tela inicial correspondente ao perfil.

### Fluxos Alternativos

* *A1 — Credenciais inválidas:*
  O sistema exibe mensagem de erro.

* *A2 — Usuário inativo:*
  O sistema bloqueia o acesso.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF02
* RNF04

### RN Relacionadas

* RN06

---

# UC02 — Cadastrar Aluno

### Ator Principal

Recepcionista

### Objetivo

Registrar um novo aluno no sistema.

### Pré-condições

* Recepcionista autenticado no sistema.

### Pós-condições

* Aluno registrado no banco de dados.

### Fluxo Principal

1. O recepcionista acessa a tela de cadastro de alunos.
2. O sistema solicita dados pessoais e de contato.
3. O recepcionista informa os dados.
4. O sistema valida as informações.
5. O sistema registra o aluno.

### Fluxos Alternativos

* *A1 — Dados obrigatórios ausentes:*
  O sistema solicita o preenchimento dos campos.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

# UC03 — Atualizar Dados do Aluno

### Ator Principal

Recepcionista

### Objetivo

Atualizar informações cadastrais do aluno.

### Pré-condições

* Aluno já cadastrado.

### Pós-condições

* Dados atualizados no sistema.

### Fluxo Principal

1. O recepcionista busca o aluno.
2. O sistema exibe os dados atuais.
3. O recepcionista altera as informações necessárias.
4. O sistema salva as alterações.

### Fluxos Alternativos

* *A1 — Aluno não encontrado:*
  O sistema informa que o aluno não foi localizado.

### RF Relacionados

* RF01

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

# UC04 — Criar Plano

### Ator Principal

Gerente

### Objetivo

Cadastrar novos tipos de planos no sistema.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Plano disponível para contratação.

### Fluxo Principal

1. O gerente acessa o módulo de planos.
2. O gerente seleciona a opção criar plano.
3. O sistema solicita informações do plano.
4. O gerente preenche os dados.
5. O sistema salva o plano.

### Fluxos Alternativos

* *A1 — Dados inválidos:*
  O sistema solicita correção.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

# UC05 — Editar Plano

### Ator Principal

Gerente

### Objetivo

Alterar informações de um plano existente.

### Pré-condições

* Plano previamente cadastrado.

### Pós-condições

* Plano atualizado no sistema.

### Fluxo Principal

1. O gerente seleciona um plano.
2. O sistema exibe as informações atuais.
3. O gerente altera os dados.
4. O sistema salva as alterações.

### Fluxos Alternativos

* *A1 — Plano não encontrado:*
  O sistema informa erro.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

# UC06 — Desativar Plano

### Ator Principal

Gerente

### Objetivo

Desativar um plano para impedir novas contratações.

### Pré-condições

* Plano cadastrado.

### Pós-condições

* Plano marcado como inativo.

### Fluxo Principal

1. O gerente acessa a lista de planos.
2. Seleciona o plano desejado.
3. Escolhe a opção desativar.
4. O sistema atualiza o status do plano.

### Fluxos Alternativos

* *A1 — Plano em uso:*
  O sistema mantém o plano apenas para alunos ativos.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

# UC07 — Registrar Pagamento

### Ator Principal

Recepcionista

### Objetivo

Registrar pagamento da mensalidade do aluno.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Pagamento registrado e situação atualizada.

### Fluxo Principal

1. O recepcionista busca o aluno.
2. O sistema exibe mensalidade pendente.
3. O recepcionista registra forma de pagamento.
4. O sistema confirma o pagamento.
5. O sistema atualiza a regularidade do aluno.

### Fluxos Alternativos

* *A1 — Pagamento parcial:*
  O sistema bloqueia o registro.

### RF Relacionados

* RF03

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN04
* RN07

---

# UC08 — Gerar Cobrança Online

### Ator Principal

Recepcionista

### Objetivo

Gerar cobrança digital para pagamento.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Cobrança gerada.

### Fluxo Principal

1. O recepcionista seleciona o aluno.
2. O sistema gera boleto ou link de pagamento.
3. O sistema registra a cobrança.

### Fluxos Alternativos

* *A1 — Falha na geração:*
  O sistema informa erro.

### RF Relacionados

* RF03

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN04

---

# UC09 — Verificar Regularidade do Aluno

### Ator Principal

Sistema

### Objetivo

Verificar automaticamente se o aluno está em dia.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Situação atualizada (regular ou inadimplente).

### Fluxo Principal

1. O sistema verifica a data do último pagamento.
2. O sistema compara com a data atual.
3. O sistema atualiza a situação do aluno.

### Fluxos Alternativos

* *A1 — Pagamento vencido:*
  O sistema marca como inadimplente.

### RF Relacionados

* RF04

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN01

---

# UC10 — Validar Entrada na Catraca

### Ator Principal

Sistema de Catraca

### Objetivo

Permitir ou negar acesso à academia.

### Pré-condições

* Aluno possuir RFID registrado.

### Pós-condições

* Acesso liberado ou bloqueado.

### Fluxo Principal

1. O aluno aproxima o cartão RFID da catraca.
2. A catraca envia solicitação ao sistema.
3. O sistema verifica a regularidade do aluno.
4. O sistema retorna autorização.
5. A catraca libera a entrada.

### Fluxos Alternativos

* *A1 — Aluno inadimplente:*
  O acesso é negado.

### RF Relacionados

* RF05

### RNF Relacionados

* RNF03
* RNF06

### RN Relacionadas

* RN01

---

# UC11 — Visualizar Aulas Disponíveis

### Ator Principal

Aluno

### Objetivo

Permitir visualizar horários de aulas.

### Pré-condições

* Aluno autenticado.

### Pós-condições

* Lista de aulas exibida.

### Fluxo Principal

1. O aluno acessa o módulo de aulas.
2. O sistema lista aulas disponíveis.
3. O sistema exibe horários e vagas.

### Fluxos Alternativos

* *A1 — Nenhuma aula disponível:*
  O sistema informa ao usuário.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN02

---

# UC12 — Reservar Aula

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno reserve vaga em uma aula.

### Pré-condições

* Aula disponível.

### Pós-condições

* Reserva registrada.

### Fluxo Principal

1. O aluno seleciona uma aula.
2. O sistema verifica disponibilidade.
3. O aluno confirma a reserva.
4. O sistema registra o agendamento.

### Fluxos Alternativos

* *A1 — Aula lotada:*
  O sistema bloqueia a reserva.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN02

---

# UC13 — Cancelar Reserva de Aula

### Ator Principal

Aluno

### Objetivo

Permitir cancelamento de agendamento.

### Pré-condições

* Reserva existente.

### Pós-condições

* Reserva cancelada.

### Fluxo Principal

1. O aluno acessa suas reservas.
2. Seleciona a reserva desejada.
3. Solicita cancelamento.
4. O sistema confirma o cancelamento.

### Fluxos Alternativos

* *A1 — Prazo expirado:*
  O sistema bloqueia cancelamento.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN03

---

# UC14 — Registrar Presença em Aula

### Ator Principal

Instrutor

### Objetivo

Registrar presença dos alunos.

### Pré-condições

* Aula iniciada.

### Pós-condições

* Presença registrada.

### Fluxo Principal

1. O instrutor acessa a lista da aula.
2. O sistema exibe alunos inscritos.
3. O instrutor marca presença.
4. O sistema salva os registros.

### Fluxos Alternativos

* *A1 — Aluno não inscrito:*
  O sistema alerta o instrutor.

### RF Relacionados

* RF07

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

# UC15 — Registrar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Registrar dados de avaliação física.

### Pré-condições

* Aluno ativo.

### Pós-condições

* Avaliação armazenada.

### Fluxo Principal

1. O instrutor busca o aluno.
2. O sistema apresenta formulário de avaliação.
3. O instrutor registra medidas físicas.
4. O sistema salva a avaliação.

### Fluxos Alternativos

* *A1 — Aluno inadimplente:*
  Avaliação bloqueada.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN05

---

# UC16 — Anexar Arquivo de Avaliação

### Ator Principal

Instrutor

### Objetivo

Adicionar documentos à avaliação física.

### Pré-condições

* Avaliação existente.

### Pós-condições

* Arquivo anexado.

### Fluxo Principal

1. O instrutor abre a avaliação.
2. Seleciona anexar arquivo.
3. O sistema faz upload do arquivo.
4. O sistema vincula ao registro.

### Fluxos Alternativos

* *A1 — Arquivo inválido:*
  O sistema bloqueia o envio.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF02

### RN Relacionadas

* RN05

---

# UC17 — Emitir Relatório de Inadimplência

### Ator Principal

Gerente

### Objetivo

Gerar relatório de alunos inadimplentes.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente acessa relatórios.
2. Seleciona relatório de inadimplência.
3. O sistema processa os dados.
4. O sistema exibe o relatório.

### Fluxos Alternativos

* *A1 — Sem dados:*
  O sistema informa ausência de registros.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN01

---

# UC18 — Emitir Relatório de Alunos Ativos

### Ator Principal

Gerente

### Objetivo

Consultar quantidade de alunos ativos.

### Pré-condições

* Gerente autenticado.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente seleciona relatório de alunos ativos.
2. O sistema consulta o banco de dados.
3. O sistema exibe os resultados.

### Fluxos Alternativos

* *A1 — Falha na consulta:*
  O sistema informa erro.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN06

---

# UC19 — Emitir Relatório de Ocupação de Aulas

### Ator Principal

Gerente

### Objetivo

Visualizar ocupação das aulas.

### Pré-condições

* Aulas cadastradas.

### Pós-condições

* Relatório exibido.

### Fluxo Principal

1. O gerente seleciona relatório de ocupação.
2. O sistema analisa reservas e presenças.
3. O sistema exibe taxa de ocupação.

### Fluxos Alternativos

* *A1 — Sem aulas registradas:*
  O sistema informa ausência de dados.

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN02

---

# UC20 — Enviar Notificação ao Aluno

### Ator Principal

Sistema

### Objetivo

Enviar notificações automáticas ao aluno.

### Pré-condições

* Evento que gere notificação.

### Pós-condições

* Notificação enviada.

### Fluxo Principal

1. O sistema identifica um evento (vencimento, confirmação ou avaliação).
2. O sistema gera a notificação.
3. O sistema envia ao aluno.

### Fluxos Alternativos

* *A1 — Falha no envio:*
  O sistema registra tentativa para reenvio.

### RF Relacionados

* RF10

### RNF Relacionados

* RNF01
* RNF03

### RN Relacionadas

* RN07

---
