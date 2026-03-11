## UC01 — Realizar Login (UC EXEMPLO - FAZER DESSA FORMA PARA TODOS OS CASOS DE USO, NESSE MESMO DOCUMENTO)

### Ator Principal
Usuário

### Objetivo
Permitir que o usuário acesse o sistema.

### Pré-condições
- Usuário deve possuir cadastro ativo.

### Pós-condições
- Sessão iniciada com sucesso.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos
- **A1 — Senha incorreta:**  
  O sistema exibe mensagem de erro.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- RF01, RF02, RF09

### RNF Relacionados
- RNF01 (Segurança), RNF03 (Tempo de Resposta)

### RN Relacionadas
- RN06

--- 
## UC02 - Cadastrar Novo Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo cliente na base de dados da academia.

### Pré-condições
- Recepcionista autenticado no sistema.

### Pós-condições
_ Aluno registrado com dados pessoais, endereço e plano inicial vinculado.

### Fluxo Principal
1. A recepcionista acessa o módulo de matrículas.
2. O sistema solicita dados: Nome, CPF, Endereço, Contato e Plano.
3. A recepcionista preenche as informações.
4. O sistema valida os campos obrigatórios e salva o registro.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:**
   O sistema alerta que o aluno já existe e impede a duplicidade.

### RF Relacionados
RF01

### RNF Relacionados
RNF04 (Integridade de Dados)

### RN Relacionadas
RN06

---
## UC03 — Criar Novo Plano de Academia

### Ator Principal
Gerente

### Objetivo
Definir novas modalidades de planos (Mensal, Anual, etc.).

### Pré-condições
- Gerente autenticado no sistema.

### Pós-condições
- Novo tipo de plano disponível para venda nas matrículas.

### Fluxo Principal
1. O gerente acessa "Configurações de Planos".
2. O gerente define o nome, valor, duração e modalidades incluídas.
3. O sistema armazena a nova configuração.

### Fluxos Alternativos
- **A1 — Valor inválido:**
   O sistema solicita correção de valores negativos ou zerados.

### RF Relacionados
RF02

### RNF Relacionados
RNF05 (Escalabilidade)

### RN Relacionadas
RN06

---
## UC04 — Editar Plano Existente

### Ator Principal
Gerente

### Objetivo
Alterar valores ou condições de um plano já cadastrado.

### Pré-condições
- Plano deve estar cadastrado no sistema.

### Pós-condições
- Dados do plano atualizados para novas vendas.

### Fluxo Principal
!. O gerente busca o plano desejado.
2. O sistema exibe os dados atuais.
3. O gerente altera as informações necessárias.
4. O sistema valida e salva as alterações.

### Fluxos Alternativos
- **A1 — Plano com alunos ativos:**
   O sistema avisa que a mudança afetará apenas novas adesões.

### RF Relacionados
RF02

### RNF Relacionados
RNF02 (Disponibilidade)

### RN Relacionadas
RN06

---
## UC05 — Registrar Pagamento Presencial

### Ator Principal
Recepcionista

### Objetivo
Registrar a quitação de mensalidade realizada na recepção.

### Pré-condições
- Aluno selecionado e com débito pendente.

### Pós-condições
- Pagamento registrado e situação do aluno atualizada (RN07).
  
### Fluxo Principal
1. O recepcionista seleciona o aluno e a parcela.
2. O sistema solicita a forma de pagamento (Dinheiro, Cartão ou PIX).
3. O recepcionista confirma o recebimento do valor integral (RN04).
4. O sistema gera o comprovante e atualiza o status financeiro imediatamente.

### Fluxos Alternativos
- **A1 — Pagamento parcial:**
   O sistema bloqueia a operação informando a RN04.

### RF Relacionados
RF03, RF04

### RNF Relacionados
RNF03 (Tempo de Resposta)

### RN Relacionadas
RN04, RN06, RN07

---
## UC06 — Gerar Boleto para Pagamento Online

### Ator Principal
Recepcionista

### Objetivo
Emitir documento de cobrança para pagamento remoto.

### Pré-condições
- Integração financeira ativa.

### Pós-condições
- Boleto gerado e disponibilizado para o aluno.

### Fluxo Principal
1. O recepcionista solicita a emissão de cobrança para o aluno.
2. O sistema comunica-se com a API bancária.
3. O sistema gera o link do boleto e o salva no perfil do aluno.

### Fluxos Alternativos
- **A1 — Falha na API:**
- O sistema avisa sobre a indisponibilidade e sugere tentar mais tarde.

## RF Relacionados
RF03

## RNF Relacionados
RNF06 (Interoperabilidade)

## RN Relacionadas
RN06

---
## UC07 — Verificar Regularidade do Aluno (Automático)

### Ator Principal
Sistema

### Objetivo
Monitorar diariamente o status financeiro de todos os alunos.

### Pré-condições
- Rotina agendada ou gatilho de acesso.

### Pós-condições
- Status do aluno atualizado para "Inadimplente" ou "Regular".

### Fluxo Principal
1. O sistema verifica a data de vencimento das parcelas.
2. O sistema identifica alunos com pagamentos atrasados.
3. Se o atraso for superior a 5 dias, o sistema marca o aluno para bloqueio de acesso.

### Fluxos Alternativos
- **A1 — Pagamento identificado:**
- O sistema restaura a regularidade (RN07).

### RF Relacionados
RF04

### RNF Relacionados
RNF01 (Confiabilidade)

### RN Relacionadas
RN01, RN07

---
## UC08 — Validar Acesso na Catraca

### Ator Principal
Sistema de Catraca (API)

### Objetivo
Liberar ou bloquear a entrada física do aluno via RFID.

### Pré-condições
- Aluno posiciona a tag RFID no leitor.

### Pós-condições
- Acesso permitido ou mensagem de bloqueio exibida.

### Fluxo Principal
1. O aluno aproxima o RFID.
2. O sistema de catraca envia o ID para o servidor FitPass.
3. O sistema verifica a regularidade (RF04).
4. Se o aluno estiver regular ou com atraso ≤ 5 dias, o sistema envia sinal de liberação.


### Fluxos Alternativos
- **A1 — Inadimplência > 5 dias:**
- O sistema nega o acesso (RN01) e instrui ir à recepção.

### RF Relacionados
RF04, RF05

### RNF Relacionados
RNF07 (Desempenho: < 1s)

### RN Relacionadas
RN01

---
## UC09 — Consultar Grade de Aulas

### Ator Principal
Aluno

### Objetivo
Visualizar horários e modalidades disponíveis.

### Pré-condições
- Aluno logado no aplicativo ou portal.

### Pós-condições
- Informações de horários exibidas ao usuário.

### Fluxo Principal
- O aluno acessa o módulo de "Agendamentos".
- O sistema exibe a lista de aulas, horários, instrutores e vagas disponíveis.

### Fluxos Alternativos
- **A1 — Nenhuma aula cadastrada:**
   O sistema informa que não há horários para a data.

### RF Relacionados
RF06

### RNF Relacionados
RNF08 (Usabilidade)

### RN Relacionadas
Nenhuma

---
### UC10 — Agendar Aula Coletiva

### Ator Principal
Aluno

### Objetivo
Reservar uma vaga em uma aula específica.

### Pré-condições
- Aluno deve estar regular e a aula deve ter vagas disponíveis.
  
### Pós-condições
- Reserva confirmada e vaga subtraída do total.

### Fluxo Principal
1. O aluno seleciona a aula desejada.
2. O sistema verifica o limite de vagas (RN02).
3. O sistema confirma a reserva e envia notificação (RF10).

### Fluxos Alternativos
- **A1 — Aula lotada:**
   O sistema informa que não há mais vagas e bloqueia a reserva.

### RF Relacionados
RF06, RF10

### RNF Relacionados
RNF04 (Consistência)

### RN Relacionadas
RN02

---
## UC11 — Gerar Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Listar todos os alunos com matrículas vigentes para análise de retenção e faturamento.

### Pré-condições
- Gerente autenticado com permissões administrativas.

### Pós-condições
- Relatório gerado com sucesso contendo a lista de membros ativos.

### Fluxo Principal
1. O gerente acessa o menu "Relatórios Gerenciais".
2. O gerente seleciona a opção "Relatório de Alunos Ativos".
3. O sistema consulta a base de dados filtrando por alunos com planos ativos e situação financeira regular.
4. O sistema exibe a lista com Nome, Plano, Data de Expiração e Último Acesso.

### Fluxos Alternativos
- **A1 — Nenhum registro encontrado:**
   O sistema informa que não há alunos ativos na base de dados no momento.

### RF Relacionados
RF09

### RNF Relacionados
RNF10 (Geração de relatórios)

### RN Relacionadas
RN06   

