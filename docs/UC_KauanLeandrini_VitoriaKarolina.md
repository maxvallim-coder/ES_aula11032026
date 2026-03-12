## UC01 - Realizar Login
### Ator Principal
Usuário (qualquer perfil: Aluno, Recepcionista, Instrutor ou Gerente)
### Objetivo
Permitir que o usuário acesse o sistema com seu perfil específico.
### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.
### Pós-condições
- Sessão iniciada com sucesso e menu conforme perfil carregado.
### Fluxo Principal
1. O usuário informa e-mail e senha na tela de login.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial de acordo com o perfil.
### Fluxos Alternativos
- **A1: Credenciais inválidas** - O sistema exibe mensagem de erro e permite nova tentativa (máximo 3 tentativas).
- **A2: Conta bloqueada** - O sistema impede o login e orienta o usuário a recuperar o acesso ou regularizar pagamento.
### Requisitos e Regras
- **RF:** (base para todos os RF)
- **RNF:** RNF02, RNF03
- **RN:** RN06
<img width="458" height="717" alt="DUC_01_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/cd936bf9-3711-4bb5-a9ec-766d07d5de71" />


---

## UC02 - Cadastrar Aluno
### Ator Principal
Recepcionista
### Objetivo
Registrar um novo aluno no sistema para permitir o uso da academia.
### Pré-condições
Recepcionista autenticado no sistema.
### Pós-condições
Cadastro realizado com sucesso no banco de dados.
### Fluxo Principal
O recepcionista insere os dados pessoais (nome, CPF, contato).
O sistema valida se o CPF é único e se os campos obrigatórios foram preenchidos.
O sistema confirma o salvamento dos dados.
### Fluxos Alternativos
**A1: CPF já cadastrado** - O sistema informa que o aluno já existe e cancela a operação.
### Requisitos e Regras
**RF:** RF01
**RNF:** RNF04
**RN:** RN06
<img width="458" height="717" alt="DUC_01_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/e8815db9-22a6-43cb-b474-0074b30c8490" />


---

## UC03 - Efetuar Matrícula em Plano
### Ator Principal
Recepcionista
### Objetivo
Vincular um aluno a um plano específico de musculação ou aulas.
### Pré-condições
Aluno devidamente cadastrado.
### Pós-condições
Matrícula ativa no sistema vinculada ao perfil do aluno.
### Fluxo Principal
O recepcionista busca o aluno pelo nome ou CPF.
Seleciona o plano desejado (ex: Musculação Mensal).
O sistema gera o registro de matrícula e a primeira parcela financeira.
O recepcionista confirma a finalização da matrícula.
### Requisitos e Regras
**RF:** RF01, RF02
**RN:** RN06
<img width="458" height="717" alt="DUC_01_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/900f0023-d010-4d59-aec6-e9ed9ef2b381" />


---

## UC04 - Validar Acesso via Catraca
### Ator Principal
Sistema de Catraca (API)
### Objetivo
Permitir ou bloquear a entrada física do aluno na unidade.
### Pré-condições
Aluno possuir tag RFID cadastrada e ativa.
### Fluxo Principal
O aluno aproxima a tag da catraca.
O sistema consulta a regularidade financeira do aluno em tempo real.
O sistema envia comando de liberação para a catraca girar.
### Fluxos Alternativos
**A1: Inadimplência** - Se o pagamento estiver vencido há mais de 5 dias, o sistema bloqueia o acesso e exibe mensagem de erro na catraca.
### Requisitos e Regras
**RF:** RF05, RF04
**RNF:** RNF03, RNF06
**RN:** RN01
<img width="544" height="733" alt="DUC_02_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/397d2df3-81e7-4823-92c2-d61ece02f7f2" />

---

## UC05 - Registrar Pagamento
### Ator Principal
Recepcionista
### Objetivo
Registrar a entrada de valores e dar baixa em parcelas do aluno.
### Pós-condições
Situação financeira do aluno atualizada instantaneamente para "Regular".
### Fluxo Principal
O recepcionista acessa o módulo financeiro do aluno.
Seleciona a parcela que está em aberto.
Informa o método de pagamento (Dinheiro, Cartão ou PIX).
O sistema confirma o recebimento do valor integral.
### Requisitos e Regras
**RF:** RF03
**RN:** RN04, RN07
<img width="544" height="733" alt="DUC_02_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/bdc908f3-1db8-478e-9859-5b079b93125f" />

---

## UC06 - Agendar Aula Coletiva
### Ator Principal
Aluno
### Objetivo
Garantir uma vaga em uma modalidade específica com horário marcado.
### Fluxo Principal
O aluno consulta a grade de aulas disponíveis no aplicativo/sistema.
Seleciona a aula desejada e confirma a reserva.
O sistema verifica se o limite de vagas ainda não foi atingido.
O agendamento é confirmado com sucesso.
### Fluxos Alternativos
**A1: Limite de vagas atingido** - O sistema impede o agendamento e avisa que a turma está lotada.
### Requisitos e Regras
**RF:** RF06
**RN:** RN02
<img width="542" height="795" alt="DUC_03_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/e9764555-021a-4473-9cc0-7639a1f83bb0" />

---

## UC07 - Cancelar Agendamento de Aula
### Ator Principal
Aluno
### Objetivo
Remover a reserva de uma aula para liberar a vaga para outros.
### Fluxo Principal
O aluno visualiza sua lista de agendamentos ativos.
Solicita o cancelamento da aula selecionada.
O sistema valida se o tempo atual é superior a 1 hora do início da aula.
A vaga é liberada e o agendamento removido.
### Fluxos Alternativos
**A1: Fora do prazo** - O sistema impede o cancelamento por estar a menos de 1 hora do início.
### Requisitos e Regras
**RF:** RF06
**RN:** RN03
<img width="542" height="795" alt="DUC_03_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/9f6ee9bc-0c4e-47c5-b9b1-c260a673a772" />

---

## UC08 - Registrar Avaliação Física
### Ator Principal
Instrutor
### Objetivo
Cadastrar medidas corporais e índices de saúde do aluno.
### Pré-condições
Aluno estar com a situação financeira regular.
### Fluxo Principal
O instrutor seleciona o aluno no sistema.
Insere os dados coletados (peso, IMC, percentual de gordura).
O sistema salva a avaliação e notifica o aluno automaticamente.
### Requisitos e Regras
**RF:** RF08, RF10
**RN:** RN05, RN06
<img width="1827" height="300" alt="DUC_04_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/76f72f3e-5941-49b8-b1eb-6768dd6e53fa" />

---

## UC09 - Registrar Presença (Lista)
### Ator Principal
Instrutor
### Objetivo
Confirmar a participação real dos alunos que agendaram a aula.
### Fluxo Principal
O instrutor acessa a lista de agendados para a turma atual.
Marca os alunos que compareceram à sala.
O sistema armazena o histórico de presença para relatórios.
### Requisitos e Regras
**RF:** RF07
**RN:** RN06
<img width="542" height="795" alt="DUC_03_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/935d5b83-b39c-4c30-a949-7426c7034171" />

---

## UC010 - Emitir Relatório de Inadimplência
### Ator Principal
Gerente
### Objetivo
Listar todos os alunos que possuem mensalidades em atraso.
### Fluxo Principal
O gerente acessa o módulo de relatórios gerenciais.
Seleciona o filtro específico de inadimplência.
O sistema gera a listagem de nomes e valores pendentes.
### Requisitos e Regras
**RF:** RF09
**RN:** RN06
<img width="544" height="733" alt="DUC_02_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/606e8eb0-d8ec-4a65-8561-25e7716e71eb" />

---

## UC11 - Gerenciar Planos
### Ator Principal
Gerente
### Objetivo
Configurar novos valores, nomes e durações dos planos oferecidos.
### Fluxo Principal
O gerente acessa as configurações de sistema para planos.
Define nome do plano, preço e tempo de contrato.
O sistema atualiza as opções disponíveis para a recepção realizar vendas.
### Requisitos e Regras
**RF:** RF02
**RN:** RN06
<img width="458" height="717" alt="DUC_01_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/5c08f0c4-868b-4968-a593-e21a584b30b5" />

---

## UC12 - Emitir Relatório de Histórico de Acessos
### Ator Principal
Gerente
### Objetivo
Visualizar entradas/saídas de alunos.
### Pré-condições
- Gerente autenticado.
### Pós-condições
- Relatório exibido.
### Fluxo Principal
1. Seleciona "Histórico de Acessos".
2. Filtra por aluno/período.
3. Mostra datas, horários e status.
### Fluxos Alternativos
- **A1: Período sem registros** - Exibe "Nenhum acesso registrado".
### Requisitos e Regras
- **RF:** RF09
- **RNF:** RNF03
- **RN:** RN01
<img width="1827" height="300" alt="DUC_04_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/5ec47506-24d1-4adb-a063-31f78164e3f4" />

---

## UC13 - Emitir Relatório de Ocupação das Aulas
### Ator Principal
Gerente
### Objetivo
Analisar vagas ocupadas por aula.
### Pré-condições
- Gerente autenticado.
### Pós-condições
- Relatório gerado com gráficos/tabelas.
### Fluxo Principal
1. Seleciona "Ocupação das Aulas".
2. Filtra por período/modalidade.
3. Exibe % de ocupação e horários pico.
### Fluxos Alternativos
- **A1: Nenhuma aula no período** - Exibe "Nenhuma aula encontrada".
### Requisitos e Regras
- **RF:** RF09
- **RNF:** RNF04
- **RN:** RN02
<img width="1827" height="300" alt="DUC_04_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/6aa2c8c4-e24e-4ae2-bc49-a6ad649b9703" />

---

## UC14 - Enviar Notificação de Vencimento
### Ator Principal
Sistema (automático)
### Objetivo
Notificar aluno sobre mensalidade próxima do vencimento.
### Pré-condições
- Aluno com vencimento próximo.
### Pós-condições
- Notificação enviada (e-mail/app).
### Fluxo Principal
1. Sistema verifica diariamente vencimentos próximos.
2. Envia lembrete automático.
### Fluxos Alternativos
- **A1: Vencido** - Envia alerta de inadimplência.
### Requisitos e Regras
- **RF:** RF10
- **RNF:** RNF01
- **RN:** RN07
<img width="544" height="733" alt="DUC_02_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/83a19894-2771-4a88-b3a7-dd8dbbb03141" />

---

## UC15 - Consultar Plano e Status do Aluno
### Ator Principal
Aluno
### Objetivo
Visualizar plano contratado e regularidade.
### Pré-condições
- Aluno autenticado.
### Pós-condições
- Informações exibidas.
### Fluxo Principal
1. Aluno acessa "Meu Perfil/Plano".
2. Sistema mostra plano, vencimento e status.
### Fluxos Alternativos
- **A1: Aluno inadimplente** - Exibe status “Bloqueado” e botão para regularizar pagamento.
### Requisitos e Regras
- **RF:** RF01, RF04
- **RNF:** RNF04
- **RN:** RN07
<img width="544" height="733" alt="DUC_02_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/0105835d-f9f0-4bb1-89f5-ea870d9c5472" />

---

## UC16 - Visualizar e Reservar Aulas Disponíveis
### Ator Principal
Aluno
### Objetivo
Ver horários disponíveis e realizar reserva.
### Pré-condições
- Aluno regular e autenticado.
### Pós-condições
- Reserva realizada ou mensagem de lotação.
### Fluxo Principal
1. Aluno acessa “Aulas Disponíveis”.
2. Visualiza grade horária.
3. Seleciona aula e confirma reserva.
### Fluxos Alternativos
- **A1: Vagas esgotadas** - Sistema bloqueia e sugere horários alternativos.
### Requisitos e Regras
- **RF:** RF06
- **RNF:** RNF04
- **RN:** RN02
<img width="542" height="795" alt="DUC_03_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/dbc92825-bead-448d-918e-0afcc94fa747" />

---

## UC17 - Recuperar Senha Esquecida
### Ator Principal
Usuário
### Objetivo
Recuperar acesso via e-mail.
### Pré-condições
- E-mail cadastrado.
### Pós-condições
- Link de reset enviado.
### Fluxo Principal
1. Usuário clica “Esqueci minha senha”.
2. Informa e-mail.
3. Sistema envia link temporário.
### Fluxos Alternativos
- **A1: E-mail não encontrado** - Exibe mensagem “E-mail não cadastrado”.
### Requisitos e Regras
- **RF:** (base para login)
- **RNF:** RNF02
- **RN:** RN06
<img width="458" height="717" alt="DUC_01_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/2f30a8a5-6438-438f-a8b1-e0c434ed1e13" />

---

## UC18 - Realizar Check-in Manual (sem catraca)
### Ator Principal
Recepcionista ou Aluno (via app)
### Objetivo
Registrar presença manualmente.
### Pré-condições
- Aluno regular.
### Pós-condições
- Acesso registrado no histórico.
### Fluxo Principal
1. Busca aluno.
2. Confirma regularidade.
3. Registra entrada manual.
### Fluxos Alternativos
- **A1: Aluno inadimplente** - Sistema bloqueia e orienta regularização.
### Requisitos e Regras
- **RF:** RF05
- **RNF:** RNF03
- **RN:** RN01
<img width="542" height="795" alt="DUC_03_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/e3b6a105-6b51-4127-b77b-f0afd8fff399" />

---

## UC19 - Anexar Arquivo na Avaliação Física
### Ator Principal
Instrutor
### Objetivo
Anexar fotos/medidas extras na avaliação.
### Pré-condições
- Avaliação em andamento.
### Pós-condições
- Arquivo salvo e associado ao registro.
### Fluxo Principal
1. Durante o registro de avaliação, seleciona “Anexar arquivo”.
2. Faz upload.
3. Sistema associa ao aluno.
### Fluxos Alternativos
- **A1: Arquivo maior que limite** - Exibe erro e orienta redimensionar.
### Requisitos e Regras
- **RF:** RF08
- **RNF:** RNF02
- **RN:** RN05
<img width="1827" height="300" alt="DUC_04_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/c347827c-b146-4a5e-803b-7d782e00e4a6" />

---

## UC20 - Visualizar Histórico de Avaliações Físicas
### Ator Principal
Instrutor ou Aluno
### Objetivo
Consultar evolução das avaliações físicas.
### Pré-condições
- Usuário autenticado com permissão.
### Pós-condições
- Histórico exibido com gráficos.
### Fluxo Principal
1. Busca aluno.
2. Acessa “Histórico de Avaliações”.
3. Sistema mostra comparativos e gráficos.
### Fluxos Alternativos
- **A1: Nenhum registro** - Exibe “Nenhuma avaliação encontrada”.
### Requisitos e Regras
- **RF:** RF08, RF09
- **RNF:** RNF04
- **RN:** RN06
<img width="1827" height="300" alt="DUC_04_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/252d5f39-6440-4057-8e62-4c36e3ee3a9f" />

---

## UC21 - Gerar Boleto ou Link de Pagamento Online
### Ator Principal
Recepcionista
### Objetivo
Gerar boleto bancário ou link de pagamento PIX para o aluno realizar pagamento online.
### Pré-condições
- Recepcionista autenticado e aluno selecionado com mensalidade pendente.
### Pós-condições
- Boleto ou link gerado, enviado ao aluno e registro criado no sistema.
### Fluxo Principal
1. Recepcionista busca o aluno pelo nome ou matrícula.
2. Acessa a opção “Gerar Pagamento Online”.
3. Sistema calcula valor total devido.
4. Recepcionista escolhe boleto ou PIX e confirma.
5. Sistema gera o documento/link e envia automaticamente por e-mail/WhatsApp.
### Fluxos Alternativos
- **A1: Aluno sem pendência** - Sistema exibe mensagem “Aluno está com pagamento em dia” e não gera boleto.
- **A2: Erro na integração com gateway de pagamento** - Sistema exibe erro e permite tentar novamente em 30 segundos.
### Requisitos e Regras
- **RF:** RF03
- **RNF:** RNF03, RNF04
- **RN:** RN04, RN07
<img width="544" height="733" alt="DUC_02_KauanLeandrini_VitoriaKarolina" src="https://github.com/user-attachments/assets/8488a5a6-e007-428a-8aa1-f06212898c1e" />

---
