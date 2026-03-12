## UC01 — Realizar Login
### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

### Objetivo
Permitir que o usuário acesse o sistema com seu nível de permissão.

### Pré-condições
Usuário deve possuir cadastro ativo.

### Pós-condições
Sessão iniciada com sucesso.

### Fluxo Principal
O usuário acessa a tela de login e informa e-mail e senha.

O sistema valida as credenciais.

O sistema autentica o usuário, identifica seu perfil e redireciona para a tela inicial correspondente.

### Fluxos Alternativos
**A1 — Senha incorreta: O sistema exibe mensagem de erro ("Credenciais inválidas").**

**A2 — Conta bloqueada/Inativa: O sistema impede o login e instrui o usuário a procurar a recepção.**

### RF Relacionados
Não tem.

### RNF Relacionados
RNF02 — Segurança

RNF04 — Usabilidade

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC02 — Cadastrar Aluno
###Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema.

### Pré-condições
Recepcionista deve estar logado no sistema.

### Pós-condições
Novo aluno salvo no banco de dados e apto a contratar um plano.

### Fluxo Principal
O recepcionista acessa o módulo de alunos e seleciona "Novo Cadastro".

O recepcionista preenche os dados pessoais, contato e endereço.

O sistema valida os dados e salva o registro.

O sistema exibe mensagem de sucesso.

### Fluxos Alternativos
**A1 — CPF já cadastrado: O sistema alerta que o aluno já existe e sugere abrir o perfil existente.**

### RF Relacionados
RF01 — Cadastro de Alunos

### RNF Relacionados
RNF02 — Segurança

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC03 — Editar Cadastro de Aluno
###Ator Principal
Recepcionista

### Objetivo
Atualizar informações de um aluno existente.

### Pré-condições
Aluno deve estar cadastrado.

### Pós-condições
Dados do aluno atualizados no sistema.

### Fluxo Principal
O recepcionista busca o aluno pelo nome ou CPF.

O sistema exibe o perfil do aluno.

O recepcionista altera os dados necessários e clica em salvar.

O sistema atualiza o registro e confirma a ação.

### Fluxos Alternativos
**A1 — Falha na validação de dados: Se um campo obrigatório for apagado, o sistema bloqueia a gravação e exige preenchimento.**

### RF Relacionados
RF01 — Cadastro de Alunos

### RNF Relacionados
RNF04 — Usabilidade

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC04 — Criar Plano
### Ator Principal
Gerente

### Objetivo
Cadastrar um novo tipo de plano na academia (ex.: Anual, Funcional).

### Pré-condições
Gerente autenticado no sistema.

### Pós-condições
Novo plano disponível para comercialização.

### Fluxo Principal
O gerente acessa o gerenciamento de planos e seleciona "Criar Plano".

O gerente informa nome, descrição, valor e periodicidade.

O sistema salva o plano e o marca como "Ativo".

### Fluxos Alternativos
**A1 — Dados incompletos: O sistema exige o preenchimento de todos os campos obrigatórios antes de salvar.**

### RF Relacionados
RF02 — Gerenciamento de Planos

### RNF Relacionados
RNF04 — Usabilidade

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC05 — Desativar Plano
### Ator Principal
Gerente

### Objetivo
Inativar um plano para que não seja mais vendido.

### Pré-condições
O plano deve existir e estar ativo.

### Pós-condições
Plano inativado, não disponível para novos alunos (alunos antigos mantêm até o fim do ciclo).

### Fluxo Principal
O gerente lista os planos e seleciona o plano desejado.

O gerente clica em "Desativar Plano".

O sistema inativa o plano para novas vendas e exibe confirmação.

### Fluxos Alternativos
**A1 — Cancelamento da ação: O gerente desiste de inativar e o sistema retorna à tela anterior.**

### RF Relacionados
RF02 — Gerenciamento de Planos

### RNF Relacionados
RNF04 — Usabilidade

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC06 — Registrar Pagamento na Recepção
Ator Principal
Recepcionista

### Objetivo
Registrar o recebimento da mensalidade de um aluno.

### Pré-condições
Aluno deve possuir um plano contratado.

### Pós-condições
Pagamento registrado e situação do aluno regularizada.

### Fluxo Principal
O recepcionista busca o aluno e seleciona a fatura em aberto.

O recepcionista seleciona a forma de pagamento (Dinheiro, Cartão, PIX).

O recepcionista confirma o valor integral e processa o pagamento.

O sistema registra o pagamento e atualiza a regularidade do aluno imediatamente.

### Fluxos Alternativos
**A1 — Tentativa de pagamento parcial: O recepcionista insere um valor menor. O sistema bloqueia a ação informando que não é permitido.**

### RF Relacionados
RF03 — Controle de Pagamentos

RF04 — Regularidade do Aluno

### RNF Relacionados
RNF03 — Performance

### RN Relacionadas
RN04 — Pagamento parcial

RN06 — Acesso restrito por perfil

RN07 — Atualização automática da regularidade

## UC07 — Gerar Boleto/Link de Pagamento
### Ator Principal
Recepcionista (ou Aluno)

### Objetivo
Gerar a cobrança online para pagamento remoto.

### Pré-condições
Aluno possuir fatura a vencer ou vencida.

### Pós-condições
Link ou código de barras gerado e disponibilizado.

### Fluxo Principal
O usuário acessa a área financeiro/mensalidades.

Seleciona a fatura desejada e clica em "Gerar Boleto/PIX".

O sistema processa a requisição e exibe o código na tela.

### Fluxos Alternativos
**A1 — Sistema de pagamento fora do ar: O sistema exibe mensagem de indisponibilidade temporária do gateway financeiro.**

### RF Relacionados
RF03 — Controle de Pagamentos

### RNF Relacionados
RNF01 — Disponibilidade

### RN Relacionadas
Não tem.

## UC08 — Verificar Regularidade do Aluno
### Ator Principal
Sistema (Processo Automático)

### Objetivo
Verificar rotineiramente quais alunos estão com pagamentos atrasados.

### Pré-condições
O sistema possuir registro de faturas geradas.

### Pós-condições
Alunos com mais de 5 dias de atraso têm seu status alterado para "Bloqueado".

### Fluxo Principal
O sistema varre diariamente as faturas vencidas.

O sistema identifica alunos com faturas vencidas há mais de 5 dias.

O sistema altera o status desses alunos para inadimplentes/bloqueados.

### Fluxos Alternativos
**A1 — Fatura paga hoje: O sistema identifica a baixa do pagamento (UC06) e não aplica o bloqueio.**

### RF Relacionados
RF04 — Regularidade do Aluno

### RNF Relacionados
RNF03 — Performance

### RN Relacionadas
RN01 — Bloqueio por inadimplência

## UC09 — Validar Acesso na Catraca
### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Permitir ou negar a entrada física do aluno na academia via RFID.

### Pré-condições
Aluno passa o cartão na catraca física.

### Pós-condições
Catraca liberada ou bloqueada, e acesso registrado.

### Fluxo Principal
A catraca lê o RFID e envia a requisição via API REST para o sistema.

O sistema verifica o status de regularidade do aluno associado àquele RFID.

O sistema constata que o aluno está regular e retorna autorização em até 3 segundos.

A catraca é liberada e o sistema registra o horário do acesso.

### Fluxos Alternativos
**A1 — Aluno Inadimplente: O sistema constata atraso maior que 5 dias e retorna negação. A catraca não abre e acende luz vermelha.**

**A2 — RFID não reconhecido: O sistema não encontra o ID e nega o acesso.**

### RF Relacionados
RF05 — Controle de Acesso

RF04 — Regularidade do Aluno

### RNF Relacionados
RNF03 — Performance

RNF06 — Integração

### RN Relacionadas
RN01 — Bloqueio por inadimplência

## UC10 — Consultar Horários de Aulas
### Ator Principal
Aluno

### Objetivo
Visualizar a grade de horários das aulas oferecidas.

### Pré-condições
Aluno logado na aplicação.

### Pós-condições
Grade de aulas visualizada pelo usuário.

### Fluxo Principal
O aluno seleciona a aba "Aulas".

O sistema lista a grade semanal com horários, instrutores e disponibilidade de vagas.

O aluno navega pelos dias da semana.

### Fluxos Alternativos
**A1 — Nenhuma aula agendada para o dia: O sistema exibe a mensagem "Não há aulas disponíveis nesta data".**

### RF Relacionados
RF06 — Agendamento de Aulas

### RNF Relacionados
RNF04 — Usabilidade

### RN Relacionadas
Não tem.

## UC11 — Agendar Aula
###Ator Principal
Aluno

### Objetivo
Reservar uma vaga em uma aula específica.

### Pré-condições
Aluno logado e visualizando uma aula com vagas disponíveis.

### Pós-condições
Vaga reservada para o aluno.

### Fluxo Principal
O aluno seleciona uma aula desejada na grade.

O sistema verifica a disponibilidade de vagas.

O sistema confirma que há vagas e o aluno clica em "Reservar".

O sistema deduz uma vaga do limite e vincula o aluno à lista de presença.

### Fluxos Alternativos
**A1 — Limite de vagas atingido: O sistema desabilita o botão de agendamento e informa "Aula Lotada".**

### RF Relacionados
RF06 — Agendamento de Aulas

### RNF Relacionados
RNF03 — Performance

### RN Relacionadas
RN02 — Limite de vagas

## UC12 — Cancelar Agendamento de Aula
### Ator Principal
Aluno

### Objetivo
Desistir de uma vaga previamente reservada.

### Pré-condições
Aluno possuir um agendamento futuro ativo.

### Pós-condições
Agendamento cancelado e vaga liberada no sistema.

### Fluxo Principal
O aluno acessa "Minhas Aulas".

O aluno seleciona a aula agendada e clica em "Cancelar Reserva".

O sistema verifica se falta mais de 1 hora para o início da aula.

O sistema processa o cancelamento e libera a vaga para outro aluno.

### Fluxos Alternativos
**A1 — Cancelamento fora do prazo: Se faltar menos de 1 hora, o sistema bloqueia a ação informando sobre a regra de prazo.**

### RF Relacionados
RF06 — Agendamento de Aulas

### RNF Relacionados
Não tem.

### RN Relacionadas
RN03 — Cancelamento de agendamento

## UC13 — Registrar Presença em Aula
### Ator Principal
Instrutor

### Objetivo
Fazer a chamada e registrar os alunos presentes em sua aula.

### Pré-condições
Instrutor logado e a aula deve estar em andamento ou finalizada.

### Pós-condições
Lista de presença salva no banco de dados.

### Fluxo Principal
O instrutor acessa suas turmas do dia e abre a lista de inscritos.

O instrutor marca a opção de "Presente" ou "Ausente" para cada aluno.

O instrutor clica em "Salvar Chamada".

O sistema registra as presenças.

### Fluxos Alternativos
**A1 — Aluno não agendado quer participar: O instrutor tenta adicionar o aluno manualmente. Se houver vaga, o sistema permite; se lotado, bloqueia.**

### RF Relacionados
RF07 — Lista de Presença

### RNF Relacionados
RNF04 — Usabilidade

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC14 — Iniciar Avaliação Física
Ator Principal
Instrutor

### Objetivo
Abrir um formulário para inserir os dados físicos de um aluno.

### Pré-condições
Instrutor logado.

### Pós-condições
Formulário de avaliação salvo com as métricas do aluno.

### Fluxo Principal
O instrutor busca o perfil do aluno.

O sistema verifica se o aluno está ativo e regular.

O instrutor preenche os dados de peso, IMC e percentual de gordura.

O instrutor anexa fotos/documentos, se necessário, e salva.

O sistema registra a avaliação no histórico do aluno.

### Fluxos Alternativos
**A1 — Aluno irregular/inativo: No passo 2, o sistema emite um alerta de bloqueio e não permite iniciar a avaliação.**

### RF Relacionados
RF08 — Avaliação Física

### RNF Relacionados
RNF02 — Segurança

### RN Relacionadas
RN05 — Avaliação física

RN06 — Acesso restrito por perfil

## UC15 — Consultar Avaliação Física
### Ator Principal
Aluno

### Objetivo
Visualizar os resultados e o histórico de suas avaliações físicas.

### Pré-condições
Aluno logado no sistema e possuir pelo menos uma avaliação cadastrada.

### Pós-condições
Histórico visualizado com sucesso.

### Fluxo Principal
O aluno clica em "Meu Progresso".

O sistema busca o histórico de avaliações físicas.

O sistema exibe gráficos evolutivos e os dados cadastrados pelos instrutores.

### Fluxos Alternativos
**A1 — Nenhuma avaliação encontrada: O sistema exibe uma mensagem encorajando o aluno a marcar uma avaliação com um instrutor.**

### RF Relacionados
RF08 — Avaliação Física

### RNF Relacionados
RNF04 — Usabilidade

### RN Relacionadas
Não tem.
## UC16 — Emitir Relatório de Inadimplência
### Ator Principal
Gerente

### Objetivo
Gerar uma lista de alunos com pagamentos em atraso.

### Pré-condições
Gerente autenticado no sistema.

### Pós-condições
Relatório gerado e exibido/exportado.

### Fluxo Principal
O gerente acessa o módulo de "Relatórios".

Seleciona a opção "Inadimplência".

Filtra pelo período desejado e clica em gerar.

O sistema processa os dados e exibe a lista de alunos com faturas atrasadas.

### Fluxos Alternativos
**A1 — Exportação de dados: O gerente escolhe baixar o relatório em PDF. O sistema compila o arquivo e inicia o download.**

### RF Relacionados
RF09 — Relatórios Gerenciais

### RNF Relacionados
RNF03 — Performance

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC17 — Emitir Relatório de Ocupação de Aulas
### Ator Principal
Gerente

### Objetivo
Analisar o engajamento e a lotação das aulas oferecidas.

### Pré-condições
Gerente autenticado.

### Pós-condições
Relatório de ocupação gerado.

### Fluxo Principal
O gerente navega até "Relatórios" e seleciona "Ocupação de Aulas".

Escolhe a semana ou mês de referência.

O sistema compila os dados comparando vagas disponíveis em relação às presenças registradas.

O sistema exibe um painel com as aulas mais e menos procuradas.

### Fluxos Alternativos
**A1 — Período sem registros: Se o gerente filtrar uma data futura sem agendamentos, o sistema exibe gráficos zerados.**

### RF Relacionados
RF09 — Relatórios Gerenciais

### RNF Relacionados
RNF05 — Escalabilidade

### RN Relacionadas
RN06 — Acesso restrito por perfil

## UC18 — Enviar Notificação de Vencimento
Ator Principal
Sistema (Processo Automático)

### Objetivo
Avisar o aluno que sua mensalidade está prestes a vencer ou já venceu.

### Pré-condições
Aluno possuir e-mail/telefone cadastrado e fatura com vencimento próximo (ex.: 3 dias antes).

### Pós-condições
E-mail ou notificação disparado.

### Fluxo Principal
O sistema verifica diariamente as datas de vencimento.

O sistema identifica faturas que vencem em 3 dias, no dia, ou estão atrasadas.

O sistema gera uma mensagem padrão com o link de pagamento.

O sistema dispara a notificação via e-mail e aplicativo.

### Fluxos Alternativos
**A1 — Falha no envio de e-mail: O sistema registra o erro no log e tenta reenviar na próxima execução da rotina.**

### RF Relacionados
RF10 — Notificações

RF03 — Controle de Pagamentos

### RNF Relacionados
RNF01 — Disponibilidade

### RN Relacionadas
Não tem.

## UC19 — Enviar Confirmação de Agendamento
### Ator Principal
Sistema

### Objetivo
Confirmar para o aluno que sua vaga na aula foi garantida.

### Pré-condições
Aluno ter concluído o UC11 (Agendar Aula).

### Pós-condições
Notificação enviada para o aluno.

### Fluxo Principal
Assim que o aluno finaliza o agendamento, o sistema intercepta a confirmação.

O sistema formata uma notificação com o nome da aula, instrutor e horário.

O sistema envia uma notificação  para o celular do aluno avisando: "Aula Confirmada!".

### Fluxos Alternativos
**A1 — Dispositivo sem aplicativo: Se o aluno acessou pelo Desktop, o sistema exibe o aviso na tela e envia um e-mail paralelo.**

### RF Relacionados
RF10 — Notificações

RF06 — Agendamento de Aulas

### RNF Relacionados
RNF04 — Usabilidade

### RN Relacionadas
Não tem.

## UC20 — Enviar Aviso de Avaliação Liberada
### Ator Principal
Sistema

### Objetivo
Notificar o aluno de que sua avaliação física está disponível para consulta.

### Pré-condições
Instrutor ter concluído o UC14 (Iniciar Avaliação Física).

### Pós-condições
Aluno notificado.

### Fluxo Principal
O instrutor clica em "Salvar" na avaliação física.

O sistema salva o registro e engatilha um evento de notificação.

O sistema dispara a mensagem para o aplicativo do aluno: "Sua avaliação física já está no sistema".

### Fluxos Alternativos
**A1 — Falha na conexão da internet do Aluno: A notificação fica pendente no servidor (fila) e é entregue assim que o aluno conectar à internet.**

### RF Relacionados
RF10 — Notificações

RF08 — Avaliação Física

### RNF Relacionados
RNF01 — Disponibilidade

### RN Relacionadas
Não tem.
