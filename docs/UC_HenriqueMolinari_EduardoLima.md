# Casos de Uso – FitPass Gym Management

---

## UC01 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Permitir que a recepcionista registre um novo aluno no sistema com seus dados pessoais e plano contratado.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- O plano a ser atribuído deve estar ativo no sistema.

### Pós-condições
- Aluno cadastrado com situação "ativo" no sistema.
- Cartão RFID vinculado ao aluno.

### Fluxo Principal
1. A recepcionista acessa o módulo de matrículas.
2. O sistema exibe o formulário de cadastro.
3. A recepcionista preenche os dados pessoais, de contato e endereço do aluno.
4. A recepcionista seleciona o plano contratado.
5. O sistema valida os dados informados.
6. O sistema registra o aluno e vincula o cartão RFID.
7. O sistema exibe confirmação de cadastro realizado com sucesso.

### Fluxos Alternativos
- **A1 — Dados obrigatórios não preenchidos:**
  O sistema exibe mensagem de erro indicando os campos ausentes e aguarda a correção.

- **A2 — Plano selecionado está inativo:**
  O sistema alerta que o plano não está disponível e solicita a seleção de outro.

### RF Relacionados
- RF01 — Cadastro de Alunos
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF02 — Segurança (dados armazenados de forma criptografada)
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Recepcionista realiza matrículas)

---

## UC02 — Gerenciar Planos

### Ator Principal
Gerente

### Objetivo
Permitir que o gerente crie, edite, ative ou desative planos oferecidos pela academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Plano criado, alterado ou com status atualizado no sistema.

### Fluxo Principal
1. O gerente acessa o módulo de gerenciamento de planos.
2. O sistema exibe a lista de planos cadastrados e seus status.
3. O gerente seleciona a ação desejada: criar, editar, ativar ou desativar.
4. O sistema exibe o formulário correspondente à ação.
5. O gerente preenche ou altera as informações do plano.
6. O sistema valida e salva as alterações.
7. O sistema exibe confirmação da operação realizada.

### Fluxos Alternativos
- **A1 — Tentativa de desativar plano com alunos vinculados:**
  O sistema alerta que existem alunos ativos no plano e solicita confirmação para prosseguir.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF04 — Usabilidade
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Gerente configura planos)

---

## UC03 — Realizar Login

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor ou Gerente)

### Objetivo
Permitir que o usuário acesse o sistema autenticando-se com suas credenciais.

### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.

### Pós-condições
- Sessão iniciada com sucesso.
- Sistema redireciona o usuário para a tela inicial correspondente ao seu perfil.

### Fluxo Principal
1. O usuário acessa a tela de login do sistema.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais informadas.
4. O sistema identifica o perfil do usuário (Aluno, Recepcionista, Instrutor ou Gerente).
5. O sistema inicia a sessão e redireciona para a tela inicial do perfil correspondente.

### Fluxos Alternativos
- **A1 — Credenciais inválidas:**
  O sistema exibe mensagem de erro e permite nova tentativa.

- **A2 — Conta bloqueada ou inativa:**
  O sistema impede o login e orienta o usuário a contatar a recepção.

### RF Relacionados
- RF04 — Regularidade do Aluno (verificação de situação ao autenticar)

### RNF Relacionados
- RNF02 — Segurança (dados de autenticação criptografados)
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC04 — Editar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Permitir a atualização dos dados pessoais, de contato ou de plano de um aluno já cadastrado.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- Aluno deve estar cadastrado no sistema.

### Pós-condições
- Dados do aluno atualizados e salvos no sistema.

### Fluxo Principal
1. A recepcionista acessa o módulo de matrículas e busca o aluno pelo nome ou CPF.
2. O sistema exibe os dados atuais do aluno.
3. A recepcionista seleciona a opção de edição.
4. O sistema exibe o formulário preenchido com os dados existentes.
5. A recepcionista altera os campos desejados.
6. O sistema valida os dados informados.
7. O sistema salva as alterações e exibe confirmação.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema informa que o aluno não foi localizado e retorna à tela de busca.

- **A2 — Dados inválidos:**
  O sistema exibe mensagem de erro indicando os campos com problema e aguarda a correção.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Recepcionista edita cadastros)

---

## UC05 — Verificar Regularidade do Aluno

### Ator Principal
Recepcionista

### Objetivo
Consultar a situação financeira e de cadastro de um aluno para fins de atendimento ou suporte.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- Aluno deve estar cadastrado no sistema.

### Pós-condições
- Situação do aluno exibida na tela (regular, inadimplente ou inativo).

### Fluxo Principal
1. A recepcionista acessa o módulo de consulta de alunos.
2. A recepcionista busca o aluno pelo nome ou CPF.
3. O sistema localiza o aluno e exibe seu status atual: regular, inadimplente ou inativo.
4. O sistema exibe também o histórico de pagamentos e a data do próximo vencimento.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema informa que o aluno não foi localizado e retorna à tela de busca.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN07 — Atualização automática da regularidade

---

## UC06 — Registrar Pagamento de Mensalidade

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento da mensalidade de um aluno e atualizar sua situação de regularidade.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- Aluno deve estar cadastrado no sistema.

### Pós-condições
- Pagamento registrado no histórico do aluno.
- Situação do aluno atualizada para "regular".

### Fluxo Principal
1. A recepcionista busca o aluno pelo nome ou CPF.
2. O sistema exibe os dados do aluno e o valor da mensalidade em aberto.
3. A recepcionista seleciona a forma de pagamento (dinheiro, cartão ou PIX).
4. O sistema registra o pagamento pelo valor integral.
5. O sistema atualiza imediatamente a situação do aluno para "regular".
6. O sistema exibe confirmação do pagamento.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema informa que o aluno não foi localizado e retorna à tela de busca.

- **A2 — Tentativa de pagamento parcial:**
  O sistema bloqueia a operação e exibe mensagem informando que apenas pagamento integral é permitido.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN04 — Pagamento parcial não permitido
- RN07 — Atualização automática da regularidade

---

## UC07 — Gerar Cobrança Online

### Ator Principal
Aluno

### Objetivo
Gerar boleto ou link de pagamento online para que o aluno quite sua mensalidade de forma remota.

### Pré-condições
- Aluno deve estar cadastrado e ativo no sistema.
- Mensalidade deve estar em aberto.

### Pós-condições
- Cobrança gerada e enviada ao aluno pelo canal configurado (e-mail ou app).

### Fluxo Principal
1. O sistema identifica os alunos com mensalidade em aberto.
2. O sistema gera o boleto ou o link de pagamento para cada aluno elegível.
3. O sistema envia a cobrança ao aluno pelo canal configurado.
4. O sistema registra a geração da cobrança no histórico do aluno.
5. Após o pagamento confirmado, o sistema atualiza a situação do aluno para "regular".

### Fluxos Alternativos
- **A1 — Falha na geração da cobrança:**
  O sistema registra o erro e agenda nova tentativa de geração.

- **A2 — Pagamento não confirmado até a data de vencimento:**
  O sistema mantém a situação do aluno como inadimplente e aciona o bloqueio de acesso conforme RN01.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN04 — Pagamento parcial não permitido
- RN07 — Atualização automática da regularidade

---

## UC08 — Enviar Notificação de Vencimento de Mensalidade

### Ator Principal
Aluno

### Objetivo
Notificar automaticamente o aluno sobre o próximo vencimento de sua mensalidade, a fim de evitar inadimplência.

### Pré-condições
- Aluno deve estar cadastrado e ativo no sistema.
- Data de vencimento da mensalidade deve estar configurada.

### Pós-condições
- Notificação enviada ao aluno com as informações de vencimento.

### Fluxo Principal
1. O sistema verifica diariamente as datas de vencimento das mensalidades.
2. O sistema identifica os alunos com vencimento próximo (conforme regra de antecedência configurada).
3. O sistema gera a notificação com os dados do valor e da data de vencimento.
4. O sistema envia a notificação ao aluno pelo canal configurado (e-mail ou app).
5. O sistema registra o envio da notificação no histórico do aluno.

### Fluxos Alternativos
- **A1 — Falha no envio da notificação:**
  O sistema registra a falha e realiza nova tentativa de envio no ciclo seguinte.

### RF Relacionados
- RF10 — Notificações (vencimento de mensalidade)

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança

### RN Relacionadas
- RN01 — Bloqueio por inadimplência (a notificação visa prevenir o bloqueio)

---

## UC09 — Validar Acesso pela Catraca

### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Verificar se o aluno possui autorização para entrar na academia via leitura do cartão RFID.

### Pré-condições
- O sistema de catraca deve estar integrado via API REST.
- O aluno deve possuir cartão RFID vinculado ao seu cadastro.

### Pós-condições
- Acesso liberado e registrado no histórico do aluno.
- Ou acesso negado com registro da tentativa.

### Fluxo Principal
1. O aluno aproxima o cartão RFID da catraca.
2. A catraca envia o código RFID ao sistema via API REST.
3. O sistema identifica o aluno pelo código RFID.
4. O sistema verifica se o aluno está com a mensalidade em dia.
5. O sistema retorna autorização de acesso à catraca.
6. A catraca libera a entrada e o sistema registra o acesso.

### Fluxos Alternativos
- **A1 — Mensalidade vencida há mais de 5 dias:**
  O sistema retorna negação de acesso. A catraca permanece bloqueada.

- **A2 — Cartão RFID não reconhecido:**
  O sistema retorna erro de identificação. O acesso é negado.

### RF Relacionados
- RF04 — Regularidade do Aluno
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF03 — Performance (resposta em até 3 segundos)
- RNF06 — Integração via API REST com JSON

### RN Relacionadas
- RN01 — Bloqueio por inadimplência (vencida há mais de 5 dias)

---

## UC10 — Agendar Aula

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno reserve uma vaga em uma aula disponível.

### Pré-condições
- Aluno deve estar autenticado no sistema.
- Aluno deve estar com situação "regular".
- A aula deve possuir vagas disponíveis.

### Pós-condições
- Reserva registrada para o aluno na aula selecionada.
- Notificação de confirmação enviada ao aluno.

### Fluxo Principal
1. O aluno acessa o módulo de agendamento.
2. O sistema exibe a lista de aulas disponíveis com horários e vagas.
3. O aluno seleciona a aula desejada.
4. O sistema verifica a disponibilidade de vagas.
5. O sistema registra a reserva do aluno.
6. O sistema envia notificação de confirmação ao aluno.

### Fluxos Alternativos
- **A1 — Aula sem vagas disponíveis:**
  O sistema informa que a capacidade máxima foi atingida e bloqueia o agendamento.

- **A2 — Aluno inadimplente:**
  O sistema impede o agendamento e orienta o aluno a regularizar a situação.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF10 — Notificações (confirmação de agendamento)

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas por aula

---

## UC11 — Confirmar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Confirmar automaticamente o agendamento do aluno e enviar notificação de confirmação após a reserva ser registrada.

### Pré-condições
- Agendamento do aluno deve ter sido realizado com sucesso (UC10).
- Aluno deve possuir canal de notificação configurado (e-mail ou app).

### Pós-condições
- Notificação de confirmação enviada ao aluno com os dados da aula agendada.

### Fluxo Principal
1. O sistema recebe o registro de novo agendamento (originado pelo UC10).
2. O sistema verifica o canal de notificação do aluno.
3. O sistema gera a mensagem de confirmação com nome da aula, data e horário.
4. O sistema envia a notificação ao aluno.
5. O sistema registra o envio no histórico de notificações do aluno.

### Fluxos Alternativos
- **A1 — Falha no envio da notificação:**
  O sistema registra a falha e realiza nova tentativa de envio.

- **A2 — Canal de notificação não configurado:**
  O sistema ignora o envio e registra que o aluno não possui canal ativo.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF10 — Notificações (confirmação de agendamento)

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF03 — Performance

### RN Relacionadas
- RN02 — Limite de vagas por aula

---

## UC12 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno cancele uma reserva em uma aula previamente agendada.

### Pré-condições
- Aluno deve estar autenticado no sistema.
- Aluno deve possuir agendamento ativo para a aula.
- O cancelamento deve ser realizado com pelo menos 1 hora de antecedência.

### Pós-condições
- Reserva cancelada.
- Vaga liberada para outros alunos.

### Fluxo Principal
1. O aluno acessa seus agendamentos.
2. O sistema lista as aulas reservadas.
3. O aluno seleciona a aula que deseja cancelar.
4. O sistema verifica se o cancelamento respeita o prazo mínimo de 1 hora.
5. O sistema cancela a reserva e libera a vaga.
6. O sistema exibe confirmação do cancelamento.

### Fluxos Alternativos
- **A1 — Cancelamento fora do prazo permitido:**
  O sistema informa que o prazo de cancelamento (1 hora antes) foi encerrado e bloqueia a operação.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN03 — Cancelamento de agendamento até 1 hora antes

---

## UC13 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Registrar a presença dos alunos em uma aula ministrada.

### Pré-condições
- Instrutor deve estar autenticado no sistema.
- A aula deve estar cadastrada e no horário vigente.

### Pós-condições
- Presença registrada no histórico da aula e do aluno.

### Fluxo Principal
1. O instrutor acessa o módulo de aulas do dia.
2. O sistema exibe a lista de aulas e os alunos agendados.
3. O instrutor seleciona a aula correspondente.
4. O sistema exibe a lista de alunos com agendamento confirmado.
5. O instrutor marca a presença de cada aluno.
6. O sistema salva o registro de presença.

### Fluxos Alternativos
- **A1 — Aluno presente sem agendamento:**
  O instrutor pode incluir manualmente o aluno na lista, desde que haja vaga disponível.

### RF Relacionados
- RF07 — Lista de Presença

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Instrutor registra presença)

---

## UC14 — Registrar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar os dados de avaliação física de um aluno, como peso, IMC e percentual de gordura.

### Pré-condições
- Instrutor deve estar autenticado no sistema.
- Aluno deve estar com situação "ativo" e "regular".

### Pós-condições
- Avaliação física registrada e vinculada ao histórico do aluno.
- Notificação enviada ao aluno informando sobre a nova avaliação.

### Fluxo Principal
1. O instrutor acessa o módulo de avaliações físicas.
2. O instrutor busca e seleciona o aluno a ser avaliado.
3. O sistema verifica se o aluno está ativo e regular.
4. O instrutor preenche os dados da avaliação (peso, IMC, percentual de gordura etc.).
5. O instrutor pode anexar arquivos complementares, se necessário.
6. O sistema salva a avaliação e notifica o aluno.

### Fluxos Alternativos
- **A1 — Aluno inadimplente ou inativo:**
  O sistema bloqueia o registro e exibe mensagem indicando que o aluno não está elegível para avaliação.

### RF Relacionados
- RF08 — Avaliação Física
- RF10 — Notificações (liberação de nova avaliação)

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN05 — Avaliação física somente para aluno ativo e regular
- RN06 — Acesso restrito por perfil (somente Instrutor registra avaliações)

---

## UC15 — Notificar Liberação de Avaliação Física

### Ator Principal
Aluno

### Objetivo
Notificar o aluno quando uma nova avaliação física for registrada pelo instrutor e estiver disponível para consulta.

### Pré-condições
- Avaliação física deve ter sido registrada com sucesso pelo instrutor (UC14).
- Aluno deve possuir canal de notificação configurado.

### Pós-condições
- Notificação enviada ao aluno informando a disponibilidade da nova avaliação física.

### Fluxo Principal
1. O sistema detecta o registro de uma nova avaliação física vinculada ao aluno.
2. O sistema verifica o canal de notificação do aluno.
3. O sistema gera a mensagem de notificação com a data da avaliação.
4. O sistema envia a notificação ao aluno.
5. O sistema registra o envio no histórico de notificações do aluno.

### Fluxos Alternativos
- **A1 — Falha no envio:**
  O sistema registra a falha e agenda nova tentativa de envio.

### RF Relacionados
- RF08 — Avaliação Física
- RF10 — Notificações (liberação de nova avaliação física)

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança

### RN Relacionadas
- RN05 — Avaliação física somente para aluno ativo e regular

---

## UC16 — Consultar Avaliação Física

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize os resultados de suas avaliações físicas registradas pelo instrutor.

### Pré-condições
- Aluno deve estar autenticado no sistema.
- Deve existir ao menos uma avaliação física registrada para o aluno.

### Pós-condições
- Dados da avaliação exibidos ao aluno (peso, IMC, percentual de gordura e histórico).

### Fluxo Principal
1. O aluno acessa o módulo de avaliações físicas.
2. O sistema exibe a lista de avaliações registradas em ordem cronológica.
3. O aluno seleciona a avaliação desejada.
4. O sistema exibe os detalhes completos da avaliação selecionada.
5. O aluno pode visualizar arquivos anexados, se houver.

### Fluxos Alternativos
- **A1 — Nenhuma avaliação registrada:**
  O sistema informa que ainda não há avaliações físicas disponíveis para o aluno.

### RF Relacionados
- RF08 — Avaliação Física

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN05 — Avaliação física somente para aluno ativo e regular

---

## UC17 — Emitir Relatório Gerencial

### Ator Principal
Gerente

### Objetivo
Permitir que o gerente gere relatórios sobre a situação da academia, como inadimplência e alunos ativos.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório gerado e disponível para visualização ou exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O sistema exibe os tipos de relatórios disponíveis.
3. O gerente seleciona o tipo de relatório e o período desejado.
4. O sistema processa e gera o relatório solicitado.
5. O gerente visualiza o relatório e pode exportá-lo.

### Fluxos Alternativos
- **A1 — Nenhum dado encontrado para o período:**
  O sistema informa que não há registros para os filtros aplicados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF02 — Segurança
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Gerente emite relatórios)

---

## UC18 — Emitir Relatório de Ocupação de Aulas

### Ator Principal
Gerente

### Objetivo
Gerar um relatório com a taxa de ocupação das aulas em um período selecionado, identificando aulas com alta ou baixa adesão.

### Pré-condições
- Gerente deve estar autenticado no sistema.
- Devem existir registros de agendamento e presença no período consultado.

### Pós-condições
- Relatório de ocupação gerado com os dados de vagas, agendamentos e presenças por aula.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o tipo "Ocupação de Aulas".
3. O gerente define o período de análise desejado.
4. O sistema processa os dados de agendamento e presença das aulas no período.
5. O sistema gera o relatório com percentual de ocupação por aula.
6. O gerente visualiza o relatório e pode exportá-lo.

### Fluxos Alternativos
- **A1 — Nenhum dado no período selecionado:**
  O sistema informa que não há registros para os filtros aplicados.

### RF Relacionados
- RF09 — Relatórios Gerenciais (ocupação das aulas)

### RNF Relacionados
- RNF02 — Segurança
- RNF05 — Escalabilidade

### RN Relacionadas
- RN02 — Limite de vagas por aula
- RN06 — Acesso restrito por perfil (somente Gerente emite relatórios)

---

## UC19 — Consultar Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Permitir que o gerente visualize o histórico de entradas dos alunos na academia para fins de controle e auditoria.

### Pré-condições
- Gerente deve estar autenticado no sistema.
- Devem existir registros de acesso no período consultado.

### Pós-condições
- Histórico de acessos exibido com data, horário e identificação do aluno.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o tipo "Histórico de Acessos".
3. O gerente define o período e, opcionalmente, filtra por aluno.
4. O sistema consulta os registros de entrada no período informado.
5. O sistema exibe a listagem de acessos com data, horário e nome do aluno.
6. O gerente pode exportar o relatório.

### Fluxos Alternativos
- **A1 — Nenhum registro encontrado:**
  O sistema informa que não há acessos para os filtros aplicados.

### RF Relacionados
- RF09 — Relatórios Gerenciais (histórico de acessos)

### RNF Relacionados
- RNF02 — Segurança
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Gerente acessa relatórios)

---

## UC20 — Realizar Logout

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor ou Gerente)

### Objetivo
Encerrar a sessão autenticada do usuário no sistema de forma segura.

### Pré-condições
- Usuário deve estar autenticado com sessão ativa.

### Pós-condições
- Sessão encerrada.
- Usuário redirecionado para a tela de login.

### Fluxo Principal
1. O usuário acessa a opção de logout no sistema.
2. O sistema solicita confirmação do encerramento da sessão.
3. O usuário confirma.
4. O sistema invalida o token de sessão do usuário.
5. O sistema redireciona para a tela de login.

### Fluxos Alternativos
- **A1 — Sessão expirada por inatividade:**
  O sistema encerra a sessão automaticamente e redireciona o usuário para a tela de login com aviso de expiração.

### RF Relacionados
- RF04 — Regularidade do Aluno (sessão encerrada impede ações indevidas)

### RNF Relacionados
- RNF02 — Segurança (invalidação de token ao encerrar sessão)
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil
