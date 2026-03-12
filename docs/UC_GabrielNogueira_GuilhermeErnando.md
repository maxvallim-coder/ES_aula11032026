## UC01 — Realizar Login

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
- RF01 (Dados Pessoais/Perfil)

### RNF Relacionados
- RNF02 (Segurança/Criptografia)

### RN Relacionadas
- RN06 (Acesso restrito por perfil)

--

# UC02 — Realizar Matrícula de Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema.

### Pré-condições
- O recepcionista deve estar autenticado.

### Pós-condições
- Registro de aluno criado no banco de dados.

### Fluxo Principal
1. O recepcionista insere dados pessoais, contato, endereço e plano (RF01).

2. O sistema valida se os campos obrigatórios estão preenchidos.

3. O sistema confirma a matrícula.

### Fluxos Alternativos

- **A1 — Plano Desativado:**
  O sistema informa que o plano escolhido não está mais disponível para novas vendas.

### RF Relacionados
- RF01, RF02

### RNF Relacionados
- RNF04 (Usabilidade)

### RN Relacionadas
- RN06 (Perfil Recepcionista)

--

# UC03 — Registrar Pagamento de Mensalidade

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento integral da mensalidade do aluno.

### Pré-condições
- Existência de débito ou renovação de plano.

### Pós-condições
- Status de regularidade atualizado.

### Fluxo Principal
1. O recepcionista seleciona o aluno.

2. O sistema exibe o valor integral (RN04).

3. O recepcionista confirma o recebimento via dinheiro, cartão ou PIX (RF03).

### Fluxos Alternativos

- **A1 - Tentativa de pagamento parcial:**
  O sistema bloqueia a operação conforme RN04.

### RF Relacionados
- RF03, RF04

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN04, RN07

--

# UC04 — Realizar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar dados antropométricos e de saúde do aluno.

### Pré-condições
- Aluno deve estar ativo e regular.

### Pós-condições
- Avaliação salva e disponível para consulta.
  
### Fluxo Principal
1. O instrutor seleciona o aluno.

2. O instrutor insere Peso, IMC e Percentual de gordura (RF08).

3. O sistema salva os dados e anexa arquivos se necessário.

### Fluxos Alternativos

- **A1 - Aluno Irregular:**
  O sistema impede a abertura da avaliação conforme RN05.

### RF Relacionados
- RF08

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN05, RN06

--

# UC05 — Validar Acesso na Catraca (RFID)

### Ator Principal
Sistema de Catraca (API)

### Objetivo
Validar a entrada do aluno via integração com hardware.

### Pré-condições
- Aluno aproximar o RFID da catraca.

### Pós-condições
- Acesso liberado ou negado.
  
### Fluxo Principal
1. O sistema lê o sinal RFID (RF05).
   
2. O sistema verifica a regularidade do aluno (RF04).

3. A catraca libera o giro.

### Fluxos Alternativos

- **A1 - Inadimplência superior a 5 dias:**
  O sistema bloqueia a entrada conforme RN01.

### RF Relacionados
- RF04, RF05

### RNF Relacionados
- RNF03, RNF06

### RN Relacionadas
- RN01

--

# UC06 — Agendar Aula Coletiva

### Ator Principal
Aluno

### Objetivo
Reservar vaga em uma aula disponível na grade.

### Pré-condições
- Aluno logado e com mensalidade em dia.

### Pós-condições
- Reserva confirmada e vaga ocupada.
  
### Fluxo Principal
1. O aluno visualiza os horários das aulas (RF06).
   
2. O aluno seleciona a aula desejada.

3. O sistema confirma a reserva e envia notificação (RF10).

### Fluxos Alternativos

- **A1 - Limite de vagas atingido:**
  O sistema bloqueia a entrada conforme RN01.

### RF Relacionados
- RF06, RF10

### RNF Relacionados
- NF03 , RNF04

### RN Relacionadas
- RN02

--

# UC07 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Desistir de um agendamento realizado previamente.

### Pré-condições
- Agendamento ativo no sistema.

### Pós-condições
- O agendamento é removido e a vaga é liberada para outros alunos.
  
### Fluxo Principal
1. O aluno seleciona a aula agendada.
   
2. O sistema valida se faltam mais de 1 hora para o início (RN03).

3. O sistema remove o aluno da lista e libera a vaga.

### Fluxos Alternativos

- **A1 - Menos de 1 hora para a aula:**
  O sistema informa que o cancelamento não é mais permitido.

### RF Relacionados
- RF04, RF05

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN03

--

# UC08 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Confirmar o comparecimento dos alunos agendados.

### Pré-condições
- Aula iniciada e lista de agendados disponível.

### Pós-condições
- Presenças registradas no histórico do aluno e da aula.
  
### Fluxo Principal
1. O instrutor acessa a lista da aula agendada.
   
2. O instrutor marca a presença dos alunos presentes.

3. O sistema salva o registro de frequência.

### Fluxos Alternativos

- **A1 - Aluno não agendado:**
  O sistema permite incluir o aluno se houver vaga disponível.

### RF Relacionados
- RF07

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN06

--

# UC09 — Gerar Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Listar alunos com mensalidades vencidas há mais de 5 dias.

### Pré-condições
- Autenticação com perfil de Gerente.

### Pós-condições
- Relatório gerado com sucesso para análise financeira.
  
### Fluxo Principal
1. O gerente seleciona a opção de relatórios gerenciais.
   
2. O sistema filtra os alunos com débitos ativos conforme a regra de bloqueio.

3. O sistema exibe a lista para o gerente.

### Fluxos Alternativos

- **A1 - Nenhum inadimplente:**
  O sistema informa que todos os alunos estão regulares.

### RF Relacionados
- RF09

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN01, RN06

--

# UC10 — Gerenciar Tipos de Planos

### Ator Principal
Gerente

### Objetivo
Criar, editar ou desativar categorias de planos de serviço.

### Pré-condições
- Autenticação com perfil de Gerente.

### Pós-condições
- Configurações de planos atualizadas no banco de dados.
  
### Fluxo Principal
1. O gerente acede ao módulo de gestão de planos.
   
2. O sistema exibe os planos atuais.

3. O gerente altera valores, nomes ou status do plano.

4. O sistema guarda as alterações.
   
### Fluxos Alternativos

- **A1 - Tentativa de acesso por outro perfil:**
  O sistema bloqueia a ação conforme.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF01

### RN Relacionadas
- RN06

--

UC11 — Notificar Vencimento de Mensalidade

### Ator Principal
Sistema (Automático)

### Objetivo
Alertar o aluno sobre o prazo de pagamento via notificação push ou e-mail.

### Pré-condições
- Data atual próxima ao vencimento da fatura.

### Pós-condições
- Notificação enviada e registada no histórico do aluno.
  
### Fluxo Principal
1. O sistema verifica diariamente as faturas a vencer.
   
2. O sistema identifica alunos com pagamentos pendentes.

3. O gerente altera valores, nomes ou status do plano.
   
### Fluxos Alternativos

- **A1 - Falha no envio da notificação:**
  O sistema registra o erro no log de eventos e tenta o reenvio no ciclo seguinte.

### RF Relacionados
- RF10

### RNF Relacionados
- RNF03

### RN Relacionadas
- RN01

--

UC12 — Gerar Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Visualizar a listagem consolidada de alunos com situação regular.

### Pré-condições
- Autenticação com perfil de Gerente.

### Pós-condições
- Relatório gerado e exibido na tela para o usuário.
  
### Fluxo Principal
1. O gerente solicita o relatório de alunos ativos.
   
2. O sistema filtra as matrículas com status "Regular".

3. O sistema exibe a lista detalhada.
   
### Fluxos Alternativos

- **A1 - Nenhum aluno ativo encontrado:**
  O sistema exibe mensagem informando que não há registros para o filtro selecionado.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF01

### RN Relacionadas
- RN02, RN06

--


UC13 — Consultar Ocupação de Aula

### Ator Principal
Gerente

### Objetivo
Visualizar a listagem consolidada de alunos com situação regular.

### Pré-condições
- Autenticação com perfil de Gerente.

### Pós-condições
- Relatório gerado e exibido na tela para o usuário.
  
### Fluxo Principal
1. O gerente solicita o relatório de alunos ativos.
   
2. O sistema filtra as matrículas com status "Regular".

3. O sistema exibe a lista detalhada.
   
### Fluxos Alternativos

- **A1 - Nenhum aluno ativo encontrado:**
  O sistema exibe mensagem informando que não há registros para o filtro selecionado.

### RF Relacionados
- RF02

### RNF Relacionados
- RNF01

### RN Relacionadas
- RN02, RN06

--

UC14 — Configurar Limite de Vagas

### Ator Principal
Gerente

### Objetivo
Definir a capacidade máxima de alunos por modalidade ou sala.

### Pré-condições
- Perfil Gerente logado no sistema.

### Pós-condições
- Limite de vagas atualizado para as novas sessões de aula.
  
### Fluxo Principal
1. O gerente edita as configurações de uma aula ou modalidade.
   
2. O gerente define o número máximo de participantes.

3. O sistema valida e salva o novo limite.
   
### Fluxos Alternativos

- **A1 - Valor inválido:**
  O gerente insere um valor negativo ou zero; o sistema solicita a correção.
  
### RF Relacionados
- RF02

### RNF Relacionados
- RNF01

### RN Relacionadas
- RN02, RN06

- -

UC15 — Sincronizar Acesso API Catraca

### Ator Principal
Sistema de Catraca (API)

### Objetivo
Garantir a comunicação entre o hardware da catraca e o software central.

### Pré-condições
- Conexão de rede ativa entre os dispositivos.

### Pós-condições
- Dados de acesso sincronizados e autorização enviada ao hardware.
  
### Fluxo Principal
1. A catraca lê o identificador e envia os dados via JSON.
   
2. O sistema processa a validação de regularidade.

3. O sistema retorna o comando de autorização para o hardware.
   
### Fluxos Alternativos

- **A1 - Falha de comunicação:**
  O sistema de catraca opera em modo offline e armazena os logs para sincr
  
### RF Relacionados
- RF05

### RNF Relacionados
- RNF03, RNF06

### RN Relacionadas
- RN01

--

UC16 — Recuperar Senha de Usuário

### Ator Principal
Usuário

### Objetivo
Permitir a redefinição de credenciais de acesso esquecidas.

### Pré-condições
- Usuário deve possuir um e-mail válido cadastrado no sistema.

### Pós-condições
- Nova senha armazenada de forma criptografada.
  
### Fluxo Principal
1. O usuário solicita a recuperação na tela de login.
   
2. O sistema envia um token de segurança para o e-mail validado.

3. O usuário insere a nova senha e confirma.

   
### Fluxos Alternativos

- **A1 - E-mail não encontrado:**
  O sistema informa que o e-mail não consta na base de dados.
  
### RF Relacionados
- RNF01

### RNF Relacionados
- RNF02

### RN Relacionadas
- RN06

--

UC17 — Consultar Grade de Horários

### Ator Principal
Sistema (Automático)

### Objetivo
Visualizar a grade de aulas disponíveis através do dispositivo móvel.

### Pré-condições
- Aluno logado no aplicativo móvel.

### Pós-condições
- ade de horários apresentada de forma responsiva.
  
### Fluxo Principal
1. O aluno acessa o menu de horários e aulas.

2. O sistema busca as aulas ativas e horários na base de dados.

3. O sistema exibe a grade completa para o aluno.

### Fluxos Alternativos

- **A1 - Sem conexão com a internet:**
  O sistema exibe os dados armazenados em cache conforme.
  
### RF Relacionados
- RF06

### RNF Relacionados
- RNF04

### RN Relacionadas
- RN02

--

UC18 — Enviar Confirmação de Reserva

### Ator Principal
Aluno

### Objetivo
Confirmar o sucesso do agendamento de uma vaga para o aluno.

### Pré-condições
- Finalização bem-sucedida do agendamento.

### Pós-condições
- Notificação de confirmação enviada ao aluno.
  
### Fluxo Principal
1. O sistema valida o registro da reserva de vaga.

2. O sistema gera uma notificação de confirmação.

3. O aluno recebe o feedback no aplicativo.

### Fluxos Alternativos

- **A1 - Falha no serviço de push:**
  O sistema registra o erro e tenta o reenvio posterior.
  
### RF Relacionados
- RF10

### RNF Relacionados
- RNF03, RNF04

### RN Relacionadas
- RN02










