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
