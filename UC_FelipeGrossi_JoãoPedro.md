# Documentação de Casos de Uso – FitPass Gym Management

---

## UC01 — Realizar Login

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

### Objetivo
Permitir que o usuário acesse o sistema de acordo com seu perfil.

### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.

### Pós-condições
- Sessão iniciada com sucesso e redirecionamento conforme perfil.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema identifica o perfil de acesso (RN06).
4. O sistema autentica o usuário e redireciona para a tela inicial correspondente.

### Fluxos Alternativos
- **A1 — Senha incorreta:**  
  O sistema exibe mensagem de erro e solicita novas credenciais.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF02 (Segurança / Criptografia)
- RNF03 (Performance)

### RN Relacionadas
- RN06 (Acesso restrito por perfil)

---

## UC02 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno para permitir o uso da academia.

### Pré-condições
- Recepcionista autenticado no sistema.

### Pós-condições
- Registro do aluno salvo no banco de dados.

### Fluxo Principal
1. O recepcionista solicita a criação de novo cadastro.
2. O recepcionista insere dados pessoais, contato e endereço.
3. O recepcionista vincula um plano inicial ao aluno (RF02).
4. O sistema valida os dados e confirma o salvamento.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:**  
  O sistema alerta que o aluno já possui registro e impede a duplicidade.

### RF Relacionados
- RF01

### RNF Relacionados
- RNF04 (Usabilidade)

### RN Relacionadas
- RN06 (Perfil de Recepcionista)

---

## UC03 — Gerenciar Planos

### Ator Principal
Gerente

### Objetivo
Criar, editar ou desativar os planos de serviço da academia.

### Pré-condições
- Gerente autenticado no sistema.

### Pós-condições
- Plano disponível ou atualizado no catálogo de vendas.

### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. O gerente define nome, valor, duração e regras do plano.
3. O sistema registra a configuração.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF04 (Usabilidade)

### RN Relacionadas
- RN06 (Perfil de Gerente)

---

## UC04 — Registrar Pagamento Presencial

### Ator Principal
Recepcionista

### Objetivo
Realizar a baixa financeira de mensalidades na recepção física.

### Pré-condições
- Aluno identificado.
- Fatura em aberto disponível.

### Pós-condições
- Status da mensalidade alterado para "Pago".
- Regularidade do aluno atualizada.

### Fluxo Principal
1. O recepcionista seleciona a conta a pagar do aluno.
2. O sistema exige o valor integral do pagamento (RN04).
3. O recepcionista informa o método (Dinheiro, Cartão ou PIX).
4. O sistema processa o pagamento e atualiza a situação do aluno imediatamente (RN07).

### RF Relacionados
- RF03
- RF04

### RNF Relacionados
- RNF03 (Performance)

### RN Relacionadas
- RN04 (Pagamento integral)
- RN07 (Atualização automática)

---

## UC05 — Validar Acesso (Catraca)

### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Controlar a entrada física dos alunos na unidade.

### Pré-condições
- Aluno aproxima o dispositivo RFID da catraca.

### Pós-condições
- Acesso liberado ou bloqueado com registro de log.

### Fluxo Principal
1. A catraca envia o código RFID para o sistema via API.
2. O sistema verifica a regularidade financeira do aluno (RF04).
3. O sistema autoriza o desbloqueio da catraca.

### Fluxos Alternativos
- **A1 — Inadimplência:**  
  Se o atraso for superior a 5 dias, o sistema nega o acesso (RN01) e exibe mensagem na catraca.

### RF Relacionados
- RF04
- RF05

### RNF Relacionados
- RNF03 (Resposta rápida)
- RNF06 (Integração JSON)

### RN Relacionadas
- RN01 (Bloqueio por inadimplência)

---

## UC06 — Agendar Aula Coletiva

### Ator Principal
Aluno

### Objetivo
Garantir uma vaga em aulas com limite de participantes.

### Pré-condições
- Aluno com mensalidade regular.
- Vagas disponíveis.

### Pós-condições
- Reserva confirmada.

### Fluxo Principal
1. O aluno seleciona a aula e o horário desejado.
2. O sistema verifica o limite de vagas (RN02).
3. O sistema confirma o agendamento.
4. O sistema envia notificação de confirmação (RF10).

### RF Relacionados
- RF06
- RF10

### RNF Relacionados
- RNF04 (Interface responsiva)

### RN Relacionadas
- RN02 (Limite de vagas)

---

## UC07 — Cancelar Agendamento

### Ator Principal
Aluno

### Objetivo
Desistir de um agendamento prévio liberando a vaga.

### Pré-condições
- Possuir agendamento ativo.

### Fluxo Principal
1. O aluno visualiza seus agendamentos.
2. O aluno solicita o cancelamento.
3. O sistema valida antecedência mínima de 1 hora (RN03).
4. O sistema confirma o cancelamento.

### RF Relacionados
- RF06

### RN Relacionadas
- RN03 (Prazo de cancelamento)

---

## UC08 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Confirmar presença dos alunos na aula.

### Pré-condições
- Aula em andamento ou finalizada.

### Fluxo Principal
1. O instrutor acessa a lista de alunos.
2. O instrutor marca presença.
3. O sistema salva as informações.

### RF Relacionados
- RF07

### RN Relacionadas
- RN06 (Perfil Instrutor)

---

## UC09 — Realizar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar evolução física do aluno.

### Pré-condições
- Aluno ativo e regular (RN05).

### Pós-condições
- Avaliação salva no perfil do aluno.

### Fluxo Principal
1. O instrutor registra medidas corporais.
2. O instrutor anexa exames ou fotos (RF08).
3. O sistema salva a avaliação e notifica o aluno.

### RF Relacionados
- RF08
- RF10

### RN Relacionadas
- RN05

---

## UC10 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Identificar alunos com mensalidades em atraso.

### Fluxo Principal
1. O gerente solicita o relatório.
2. O sistema filtra alunos com dívidas.
3. O sistema gera lista exportável.

### RF Relacionados
- RF09

---

## UC11 — Gerar Boleto Online

### Ator Principal
Aluno

### Objetivo
Emitir boleto para pagamento de mensalidade.

### Fluxo Principal
1. O aluno acessa área financeira.
2. O aluno seleciona fatura.
3. O sistema gera boleto ou linha digitável.

### RF Relacionados
- RF03

---

## UC12 — Configurar Notificações Automáticas

### Ator Principal
Sistema

### Objetivo
Notificar alunos automaticamente.

### Fluxo Principal
1. O sistema verifica vencimentos diariamente.
2. O sistema envia notificações automáticas.

### RF Relacionados
- RF10

---

## UC13 — Consultar Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Monitorar entradas e saídas de alunos.

### Fluxo Principal
1. O gerente seleciona período.
2. O sistema exibe registros da catraca.

### RF Relacionados
- RF09

---

## UC14 — Inativar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Suspender acesso de um aluno.

### Fluxo Principal
1. O recepcionista localiza o aluno.
2. O recepcionista seleciona "inativar".
3. O sistema registra a alteração.

### RF Relacionados
- RF01

---

## UC15 — Consultar Ocupação das Aulas

### Ator Principal
Gerente

### Objetivo
Avaliar popularidade das aulas.

### Fluxo Principal
1. O gerente acessa relatórios.
2. O sistema mostra taxa de ocupação.

### RF Relacionados
- RF09

---

## UC16 — Anexar Documentos de Saúde

### Ator Principal
Instrutor

### Objetivo
Armazenar documentos médicos dos alunos.

### Fluxo Principal
1. O instrutor acessa perfil do aluno.
2. O instrutor envia arquivos.
3. O sistema armazena documentos.

### RF Relacionados
- RF08

---

## UC17 — Visualizar Grade de Horários

### Ator Principal
Aluno

### Objetivo
Consultar horários de aulas disponíveis.

### Fluxo Principal
1. O aluno acessa agenda.
2. O sistema exibe grade semanal.

### RF Relacionados
- RF06

---

## UC18 — Consultar Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Obter estatísticas de alunos matriculados.

### Fluxo Principal
1. O gerente solicita listagem.
2. O sistema gera relatório.

### RF Relacionados
- RF09

---

## UC19 — Atualizar Dados Cadastrais

### Ator Principal
Recepcionista

### Objetivo
Atualizar dados de contato ou endereço.

### Fluxo Principal
1. O recepcionista localiza o aluno.
2. O recepcionista altera dados.
3. O sistema salva alterações.

### RF Relacionados
- RF01

---

## UC20 — Redefinir Senha de Acesso

### Ator Principal
Usuário

### Objetivo
Permitir recuperação segura da senha.

### Fluxo Principal
1. O usuário solicita redefinição.
2. O sistema envia link por e-mail.
3. O usuário define nova senha.
4. O sistema atualiza as credenciais.

\### RNF Relacionados
- RNF02 (Segurança)
