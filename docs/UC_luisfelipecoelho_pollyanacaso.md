# Casos de Uso — Sistema de Gestão de Academia

Documento contendo a especificação dos **Casos de Uso** do sistema de gestão de academia.

---

## UC01 — Cadastrar Aluno

### **Ator Principal**
Recepcionista

### **Objetivo**
Permitir registrar um novo aluno no sistema.

### **Pré-condições**
- O recepcionista deve estar autenticado no sistema.

### **Pós-condições**
- Aluno cadastrado e disponível para contratação de plano.

### **Fluxo Principal**
1. O recepcionista acessa a tela de cadastro de alunos.  
2. O recepcionista preenche dados pessoais, contato, endereço e plano.  
3. O sistema valida os dados inseridos.  
4. O sistema salva o cadastro do aluno.

### **Fluxos Alternativos**

**A1 — Dados obrigatórios não preenchidos**  
- O sistema exibe mensagem solicitando preenchimento dos campos.

**A2 — CPF já cadastrado**  
- O sistema informa que já existe um aluno registrado.

### **RF Relacionados**
- RF01 — Cadastro de Alunos

### **RNF Relacionados**
- RNF02 — Segurança  
- RNF04 — Usabilidade

### **RN Relacionadas**
- RN06 — Acesso restrito por perfil

---

## UC02 — Atualizar Dados do Aluno

### **Ator Principal**
Recepcionista

### **Objetivo**
Permitir a atualização das informações cadastrais do aluno.

### **Pré-condições**
- Aluno deve estar previamente cadastrado.

### **Pós-condições**
- Dados do aluno atualizados no sistema.

### **Fluxo Principal**
1. Recepcionista acessa cadastro do aluno.  
2. Recepcionista altera informações desejadas.  
3. Sistema valida os dados atualizados.  
4. Sistema salva as alterações.

### **Fluxos Alternativos**

**A1 — Dados inválidos**  
- Sistema exibe erro de validação.

### **RF Relacionados**
- RF01 — Cadastro de Alunos

### **RNF Relacionados**
- RNF02 — Segurança  
- RNF04 — Usabilidade

### **RN Relacionadas**
- RN06 — Acesso restrito por perfil

---

## UC03 — Registrar Pagamento

### **Ator Principal**
Recepcionista

### **Objetivo**
Registrar pagamento da mensalidade do aluno.

### **Pré-condições**
- Aluno deve possuir plano ativo.

### **Pós-condições**
- Pagamento registrado e situação do aluno atualizada.

### **Fluxo Principal**
1. Recepcionista acessa tela de pagamentos.  
2. Recepcionista seleciona aluno.  
3. Recepcionista registra pagamento (dinheiro, cartão ou PIX).  
4. Sistema registra pagamento e atualiza situação do aluno.

### **Fluxos Alternativos**

**A1 — Tentativa de pagamento parcial**  
- Sistema bloqueia operação.

### **RF Relacionados**
- RF03 — Controle de Pagamentos

### **RNF Relacionados**
- RNF02 — Segurança  
- RNF03 — Performance

### **RN Relacionadas**
- RN04 — Pagamento parcial não permitido  
- RN07 — Atualização automática da regularidade

---

## UC04 — Verificar Regularidade do Aluno

### **Ator Principal**
Sistema

### **Objetivo**
Verificar automaticamente se o aluno está com pagamento em dia.

### **Pré-condições**
- Aluno cadastrado e plano ativo.

### **Pós-condições**
- Situação do aluno atualizada.

### **Fluxo Principal**
1. Sistema verifica data de vencimento da mensalidade.  
2. Sistema compara com pagamentos registrados.  
3. Sistema define status do aluno (regular ou inadimplente).

### **Fluxos Alternativos**

**A1 — Pagamento vencido**  
- Sistema marca aluno como inadimplente.

### **RF Relacionados**
- RF04 — Regularidade do Aluno

### **RNF Relacionados**
- RNF03 — Performance

### **RN Relacionadas**
- RN01 — Bloqueio por inadimplência

---

## UC05 — Validar Acesso na Catraca

### **Ator Principal**
Sistema de Catraca

### **Objetivo**
Validar entrada do aluno na academia.

### **Pré-condições**
- Aluno deve possuir identificação RFID.

### **Pós-condições**
- Entrada liberada ou bloqueada.

### **Fluxo Principal**
1. Aluno aproxima cartão RFID da catraca.  
2. Sistema recebe identificação do aluno.  
3. Sistema verifica regularidade.  
4. Sistema libera entrada.

### **Fluxos Alternativos**

**A1 — Aluno inadimplente**  
- Sistema bloqueia acesso.

**A2 — RFID não reconhecido**  
- Sistema exibe erro.

### **RF Relacionados**
- RF05 — Controle de Acesso

### **RNF Relacionados**
- RNF03 — Performance  
- RNF06 — Integração

### **RN Relacionadas**
- RN01 — Bloqueio por inadimplência

---

## UC06 — Agendar Aula

### **Ator Principal**
Aluno

### **Objetivo**
Permitir reservar vaga em aula disponível.

### **Pré-condições**
- Aluno deve estar ativo e regular.

### **Pós-condições**
- Reserva registrada no sistema.

### **Fluxo Principal**
1. Aluno acessa lista de aulas disponíveis.  
2. Aluno seleciona aula.  
3. Sistema verifica disponibilidade de vagas.  
4. Sistema confirma agendamento.

### **Fluxos Alternativos**

**A1 — Aula lotada**  
- Sistema bloqueia agendamento.

### **RF Relacionados**
- RF06 — Agendamento de Aulas

### **RNF Relacionados**
- RNF04 — Usabilidade

### **RN Relacionadas**
- RN02 — Limite de vagas

---

## UC07 — Cancelar Agendamento de Aula

### **Ator Principal**
Aluno

### **Objetivo**
Permitir cancelamento de reserva em aula.

### **Pré-condições**
- Aluno deve possuir agendamento ativo.

### **Pós-condições**
- Reserva removida do sistema.

### **Fluxo Principal**
1. Aluno acessa seus agendamentos.  
2. Aluno seleciona aula.  
3. Aluno solicita cancelamento.  
4. Sistema remove reserva.

### **Fluxos Alternativos**

**A1 — Prazo expirado**  
- Sistema bloqueia cancelamento.

### **RF Relacionados**
- RF06 — Agendamento de Aulas

### **RNF Relacionados**
- RNF04 — Usabilidade

### **RN Relacionadas**
- RN03 — Cancelamento até 1 hora antes

---

# UC08 — Registrar Presença em Aula

*Ator Principal*
Instrutor

*Objetivo*
Registrar presença dos alunos participantes da aula.

*Pré-condições*
Aula deve estar agendada.

*Pós-condições*
Presença registrada.

*Fluxo Principal*
Instrutor acessa aula programada.
Instrutor visualiza lista de alunos.
Instrutor marca presença dos alunos.
Sistema salva registro.

*Fluxos Alternativos*

*A1 — Aluno não compareceu:*
Instrutor registra ausência.

*RF Relacionados*
RF07 — Lista de Presença

*RNF Relacionados*
RNF04 — Usabilidade

*RN Relacionadas*
RN06 — Acesso restrito por perfil

---

# UC09 — Registrar Avaliação Física

*Ator Principal*
Instrutor

*Objetivo*
Registrar avaliação física do aluno.

*Pré-condições*
Aluno deve estar ativo e regular.

*Pós-condições*
Avaliação salva no histórico do aluno.

*Fluxo Principal*
Instrutor acessa cadastro do aluno.
Instrutor registra dados da avaliação (peso, IMC, gordura).
Sistema salva avaliação.

*Fluxos Alternativos*

*A1 — Aluno irregular:*
Sistema impede registro da avaliação.

*RF Relacionados*
RF08 — Avaliação Física

*RNF Relacionados*
RNF02 — Segurança

*RN Relacionadas*
RN05 — Avaliação física apenas para alunos ativos

---

# UC10 — Emitir Relatório Gerencial

*Ator Principal*
Gerente

*Objetivo*
Gerar relatórios de gestão da academia.

*Pré-condições*
Gerente autenticado no sistema.

*Pós-condições*
Relatório exibido ou exportado.

*Fluxo Principal*
Gerente acessa módulo de relatórios.
Gerente escolhe tipo de relatório.
Sistema processa dados.
Sistema exibe relatório.

*Fluxos Alternativos*

*A1 — Falha na geração:*
Sistema exibe erro.

*RF Relacionados*
RF09 — Relatórios Gerenciais

*RNF Relacionados*
RNF03 — Performance

*RN Relacionadas*
RN06 — Acesso restrito por perfil

---

# UC11 — Criar Plano de Academia

*Ator Principal*
Gerente

*Objetivo*
Permitir a criação de novos planos de academia.

*Pré-condições*
Gerente autenticado no sistema.

*Pós-condições*
Plano cadastrado e disponível para contratação.

*Fluxo Principal*
Gerente acessa o módulo de planos.
Gerente seleciona a opção de criar plano.
Gerente informa nome, valor, duração e características.
Sistema valida os dados.
Sistema salva o novo plano.

*Fluxos Alternativos*

*A1 — Dados incompletos:*
Sistema solicita preenchimento dos campos obrigatórios.

*RF Relacionados*
RF02 — Gerenciamento de Planos

*RNF Relacionados*
RNF04 — Usabilidade

*RN Relacionadas*
RN06 — Acesso restrito por perfil

---

# UC12 — Editar Plano

*Ator Principal*
Gerente

*Objetivo*
Permitir a alteração das informações de um plano existente.

*Pré-condições*
Plano deve estar cadastrado no sistema.

*Pós-condições*
Informações do plano atualizadas.

*Fluxo Principal*
Gerente acessa lista de planos.
Gerente seleciona um plano.
Gerente altera informações desejadas.
Sistema valida dados.
Sistema salva alterações.

*Fluxos Alternativos*

*A1 — Dados inválidos:*
Sistema exibe erro e solicita correção.

*RF Relacionados*
RF02 — Gerenciamento de Planos

*RNF Relacionados*
RNF04 — Usabilidade

*RN Relacionadas*
RN06 — Acesso restrito por perfil

---

# UC13 — Ativar Plano

*Ator Principal*
Gerente

*Objetivo*
Permitir ativar um plano para que possa ser contratado.

*Pré-condições*
Plano deve estar previamente cadastrado.

*Pós-condições*
Plano disponível para uso.

*Fluxo Principal*
Gerente acessa lista de planos.
Gerente seleciona plano inativo.
Gerente solicita ativação.
Sistema altera status para ativo.

*Fluxos Alternativos*

*A1 — Plano já ativo:*
Sistema informa que o plano já está disponível.

*RF Relacionados*
RF02 — Gerenciamento de Planos

*RNF Relacionados*
RNF04 — Usabilidade

*RN Relacionadas*
RN06 — Acesso restrito por perfil

---

# UC14 — Desativar Plano

*Ator Principal*
Gerente

*Objetivo*
Permitir desativar um plano existente.

*Pré-condições*
Plano cadastrado no sistema.

*Pós-condições*
Plano indisponível para novas contratações.

*Fluxo Principal*
Gerente acessa lista de planos.
Gerente seleciona plano ativo.
Gerente solicita desativação.
Sistema altera status do plano para inativo.

*Fluxos Alternativos*

*A1 — Plano já inativo:*
Sistema informa que o plano já está desativado.

*RF Relacionados*
RF02 — Gerenciamento de Planos

*RNF Relacionados*
RNF04 — Usabilidade

*RN Relacionadas*
RN06 — Acesso restrito por perfil

---

# UC15 — Consultar Horários de Aula

*Ator Principal*
Aluno

*Objetivo*
Permitir visualizar aulas disponíveis e horários.

*Pré-condições*
Aluno deve estar autenticado.

*Pós-condições*
Lista de aulas exibida.

*Fluxo Principal*
Aluno acessa módulo de aulas.
Sistema consulta aulas cadastradas.
Sistema exibe horários e vagas disponíveis.

*Fluxos Alternativos*

*A1 — Nenhuma aula disponível:*
Sistema informa que não há aulas cadastradas.

*RF Relacionados*
RF06 — Agendamento de Aulas

*RNF Relacionados*
RNF04 — Usabilidade

*RN Relacionadas*
RN02 — Limite de vagas

---

# UC16 — Enviar Notificação de Vencimento

*Ator Principal*
Sistema

*Objetivo*
Notificar o aluno sobre vencimento da mensalidade.

*Pré-condições*
Aluno possui mensalidade próxima do vencimento.

*Pós-condições*
Aluno recebe notificação.

*Fluxo Principal*
Sistema verifica datas de vencimento.
Sistema identifica mensalidades próximas do prazo.
Sistema envia notificação ao aluno.

*Fluxos Alternativos*

*A1 — Falha no envio:*
Sistema registra tentativa e agenda novo envio.

*RF Relacionados*
RF10 — Notificações

*RNF Relacionados*
RNF01 — Disponibilidade

*RN Relacionadas*
RN01 — Bloqueio por inadimplência

---

# UC17 — Enviar Confirmação de Agendamento

*Ator Principal*
Sistema

*Objetivo*
Confirmar para o aluno que o agendamento foi realizado.

*Pré-condições*
Agendamento de aula realizado.

*Pós-condições*
Aluno recebe confirmação.

*Fluxo Principal*
Sistema registra agendamento.
Sistema gera mensagem de confirmação.
Sistema envia notificação ao aluno.

*Fluxos Alternativos*

*A1 — Falha na notificação:*
Sistema registra erro.

*RF Relacionados*
RF10 — Notificações

*RNF Relacionados*
RNF01 — Disponibilidade

*RN Relacionadas*
RN02 — Limite de vagas

---

# UC18 — Enviar Notificação de Nova Avaliação

*Ator Principal*
Sistema

*Objetivo*
Informar ao aluno que uma nova avaliação física está disponível.

*Pré-condições*
Avaliação física registrada no sistema.

*Pós-condições*
Aluno recebe notificação.

*Fluxo Principal*
Sistema detecta nova avaliação registrada.
Sistema gera mensagem.
Sistema envia notificação ao aluno.

*Fluxos Alternativos*

*A1 — Falha no envio:*
Sistema registra tentativa de envio.

*RF Relacionados*
RF10 — Notificações

*RNF Relacionados*
RNF01 — Disponibilidade

*RN Relacionadas*
RN05 — Avaliação física

---

# UC19 — Consultar Histórico de Acessos

*Ator Principal*
Gerente

*Objetivo*
Visualizar histórico de entradas dos alunos na academia.

*Pré-condições*
Registros de acesso devem existir.

*Pós-condições*
Histórico exibido.

*Fluxo Principal*
Gerente acessa módulo de relatórios.
Gerente seleciona relatório de acessos.
Sistema consulta banco de dados.
Sistema exibe histórico.

*Fluxos Alternativos*

*A1 — Nenhum registro encontrado:*
Sistema informa ausência de dados.

*RF Relacionados*
RF09 — Relatórios Gerenciais

*RNF Relacionados*
RNF03 — Performance

*RN Relacionadas*
RN06 — Acesso restrito por perfil

---

# UC20 — Consultar Ocupação das Aulas

*Ator Principal*
Gerente

*Objetivo*
Visualizar taxa de ocupação das aulas da academia.

*Pré-condições*
Aulas cadastradas no sistema.

*Pós-condições*
Relatório de ocupação exibido.

*Fluxo Principal*
Gerente acessa relatórios.
Gerente seleciona relatório de ocupação.
Sistema calcula vagas preenchidas por aula.
Sistema exibe resultados.

*Fluxos Alternativos*

*A1 — Falha no processamento:*
Sistema exibe erro.

*RF Relacionados*
RF09 — Relatórios Gerenciais

*RNF Relacionados*
RNF03 — Performance

*RN Relacionadas*
RN02 — Limite de vagas
