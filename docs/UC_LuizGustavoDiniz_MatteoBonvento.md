## UC01 — Realizar Matrícula

### Ator Principal

Aluno / Recepcionista

### Objetivo

Permitir que um novo aluno seja matriculado no sistema FitPass com todos os dados necessários.

### Pré-condições

- Aluno não deve possuir matrícula ativa no sistema.
- Recepcionista autenticada no sistema.

### Pós-condições

- Matrícula registrada com sucesso.
- Aluno vinculado a um plano e apto a realizar pagamento.

### Fluxo Principal

1. A recepcionista acessa a tela de nova matrícula.
2. O sistema exibe o formulário de cadastro de aluno.
3. A recepcionista preenche dados pessoais, contato, endereço e plano contratado.
4. O sistema valida os dados informados.
5. O sistema registra a matrícula e gera o primeiro boleto/cobrança.
6. O sistema exibe a confirmação da matrícula com o número gerado.

### Fluxos Alternativos

- **A1 — Dados inválidos ou incompletos:** O sistema destaca os campos com erro e solicita correção antes de prosseguir.
- **A2 — Aluno já cadastrado:** O sistema identifica o CPF/e-mail duplicado e impede o cadastro, sugerindo pesquisar o aluno existente.

### RF Relacionados

- RF01 — Cadastro de Alunos
- RF02 — Gerenciamento de Planos
- RF03 — Controle de Pagamentos

### RNF Relacionados

- RNF02 — Segurança (dados criptografados)
- RNF03 — Performance (resposta em até 3s)
- RNF04 — Usabilidade

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Recepcionista realiza matrículas)

---

## UC02 — Escolher Plano

### Ator Principal

Aluno / Recepcionista

### Objetivo

Permitir que o aluno visualize e selecione um plano disponível durante ou após a matrícula.

### Pré-condições

- Aluno deve estar em processo de matrícula ou com matrícula ativa.
- Planos devem estar cadastrados e ativos no sistema.

### Pós-condições

- Plano selecionado vinculado ao aluno.
- Valor do plano associado à próxima cobrança.

### Fluxo Principal

1. O sistema exibe a listagem de planos ativos (mensal, trimestral, anual, musculação, funcional etc.).
2. O aluno ou recepcionista visualiza detalhes de cada plano (valor, duração, benefícios).
3. O aluno ou recepcionista seleciona o plano desejado.
4. O sistema vincula o plano ao cadastro do aluno.
5. O sistema confirma a seleção e apresenta o valor a ser pago.

### Fluxos Alternativos

- **A1 — Nenhum plano disponível:** O sistema exibe mensagem informando que não há planos ativos no momento e orienta a contatar a gerência.
- **A2 — Troca de plano com vigência ativa:** O sistema notifica sobre a vigência do plano atual e calcula o valor proporcional de ajuste.

### RF Relacionados

- RF02 — Gerenciamento de Planos
- RF01 — Cadastro de Alunos

### RNF Relacionados

- RNF04 — Usabilidade
- RNF03 — Performance

### RN Relacionadas

- RN06 — Acesso restrito por perfil

---

## UC03 — Efetuar Pagamento

### Ator Principal

Aluno / Recepcionista

### Objetivo

Registrar o pagamento da mensalidade do aluno e atualizar sua situação de regularidade.

### Pré-condições

- Aluno deve possuir matrícula ativa e mensalidade em aberto.
- Recepcionista autenticada no sistema para pagamentos presenciais.

### Pós-condições

- Pagamento registrado com sucesso.
- Situação de regularidade do aluno atualizada imediatamente.

### Fluxo Principal

1. A recepcionista localiza o aluno pelo nome, CPF ou código.
2. O sistema exibe a(s) mensalidade(s) em aberto.
3. A recepcionista informa a forma de pagamento (dinheiro, cartão ou PIX).
4. O sistema registra o pagamento e emite o comprovante.
5. O sistema atualiza automaticamente a situação do aluno para "regular".
6. O sistema libera o acesso do aluno caso estivesse bloqueado por inadimplência.

### Fluxos Alternativos

- **A1 — Pagamento online:** O sistema gera boleto ou link de pagamento (PIX/cartão) enviado ao aluno por e-mail ou notificação.
- **A2 — Tentativa de pagamento parcial:** O sistema bloqueia o registro e exibe mensagem informando que somente o valor integral é aceito.

### RF Relacionados

- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados

- RNF02 — Segurança
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas

- RN04 — Pagamento parcial não permitido
- RN07 — Atualização automática da regularidade

---

## UC04 — Realizar Cadastro Facial na Catraca

### Ator Principal

Aluno / Recepcionista

### Objetivo

Registrar o dado biométrico facial do aluno para liberação de acesso via catraca.

### Pré-condições

- Aluno deve possuir matrícula ativa e mensalidade em dia.
- Sistema de catraca integrado e operacional.

### Pós-condições

- Dados faciais vinculados ao cadastro do aluno.
- Catraca apta a reconhecer e liberar o acesso do aluno.

### Fluxo Principal

1. A recepcionista acessa o módulo de controle de acesso no sistema.
2. O sistema localiza o cadastro do aluno.
3. O sistema solicita a captura da imagem facial via dispositivo de leitura.
4. O aluno posiciona-se para leitura facial.
5. O sistema envia os dados biométricos à API da catraca via REST/JSON.
6. A catraca confirma o cadastro e o sistema registra a operação com sucesso.

### Fluxos Alternativos

- **A1 — Leitura facial inválida:** O sistema solicita nova captura e orienta o aluno para melhor posicionamento.
- **A2 — Falha na integração com a catraca:** O sistema exibe mensagem de erro de comunicação e orienta tentativa posterior.
- **A3 — Aluno inadimplente:** O sistema bloqueia o cadastro facial e orienta a regularizar a situação financeira primeiro.

### RF Relacionados

- RF05 — Controle de Acesso
- RF01 — Cadastro de Alunos

### RNF Relacionados

- RNF06 — Integração (API REST/JSON)
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas

- RN01 — Bloqueio por inadimplência
- RN06 — Acesso restrito por perfil

---

## UC05 — Agendar Aula

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno visualize horários disponíveis e reserve vaga em uma aula.

### Pré-condições

- Aluno deve estar ativo e com mensalidade em dia.
- Aulas devem estar disponíveis com vagas abertas.

### Pós-condições

- Reserva registrada no sistema.
- Aluno recebe confirmação de agendamento.

### Fluxo Principal

1. O aluno acessa a tela de agendamento de aulas.
2. O sistema exibe as aulas disponíveis com horários, instrutores e vagas restantes.
3. O aluno seleciona a aula desejada.
4. O sistema verifica disponibilidade de vagas.
5. O sistema registra a reserva e envia notificação de confirmação ao aluno.

### Fluxos Alternativos

- **A1 — Aula sem vagas disponíveis:** O sistema informa que a aula está lotada e impede o agendamento.
- **A2 — Aluno inadimplente:** O sistema bloqueia o agendamento e orienta o aluno a regularizar o pagamento.
- **A3 — Cancelamento de agendamento:** O aluno cancela a reserva e o sistema libera a vaga, desde que seja com pelo menos 1 hora de antecedência.

### RF Relacionados

- RF06 — Agendamento de Aulas
- RF10 — Notificações
- RF04 — Regularidade do Aluno

### RNF Relacionados

- RNF04 — Usabilidade
- RNF03 — Performance
- RNF01 — Disponibilidade

### RN Relacionadas

- RN02 — Limite de vagas
- RN03 — Cancelamento de agendamento
- RN01 — Bloqueio por inadimplência

---

## UC06 — Registrar Presença em Aulas

### Ator Principal

Instrutor

### Objetivo

Registrar a presença dos alunos que compareceram a uma aula específica.

### Pré-condições

- Aula deve estar agendada e em andamento ou concluída.
- Instrutor autenticado no sistema.

### Pós-condições

- Presença dos alunos registrada no histórico da aula.
- Dados disponíveis para relatórios gerenciais.

### Fluxo Principal

1. O instrutor acessa o módulo de lista de presença.
2. O sistema exibe as aulas do dia com a lista de alunos agendados.
3. O instrutor seleciona a aula correspondente.
4. O sistema exibe a lista de alunos inscritos.
5. O instrutor marca a presença de cada aluno presente.
6. O sistema registra e salva a lista de presença.

### Fluxos Alternativos

- **A1 — Aluno não agendado comparece:** O instrutor pode registrar o aluno avulso, desde que haja vaga disponível.
- **A2 — Aula sem alunos agendados:** O sistema exibe lista vazia e o instrutor pode registrar presenças avulsas.

### RF Relacionados

- RF07 — Lista de Presença
- RF06 — Agendamento de Aulas
- RF09 — Relatórios Gerenciais

### RNF Relacionados

- RNF04 — Usabilidade
- RNF03 — Performance

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Instrutor registra presenças)

---

## UC07 — Passar pela Avaliação Física

### Ator Principal

Aluno / Instrutor

### Objetivo

Registrar a avaliação física do aluno com dados biométricos e de composição corporal.

### Pré-condições

- Aluno deve estar ativo e regular (mensalidade em dia).
- Instrutor autenticado no sistema.
- Avaliação anterior não pode estar pendente de liberação.

### Pós-condições

- Avaliação registrada e vinculada ao histórico do aluno.
- Aluno notificado sobre a liberação da avaliação.

### Fluxo Principal

1. O instrutor acessa o módulo de avaliação física.
2. O instrutor localiza o cadastro do aluno.
3. O sistema verifica se o aluno está ativo e regular.
4. O instrutor preenche os dados da avaliação (peso, IMC, percentual de gordura, medidas etc.).
5. O instrutor pode anexar arquivos de exames ou documentos complementares.
6. O sistema registra a avaliação e notifica o aluno sobre a nova avaliação disponível.

### Fluxos Alternativos

- **A1 — Aluno inadimplente:** O sistema bloqueia o registro da avaliação e exibe mensagem de irregularidade.
- **A2 — Aluno inativo:** O sistema impede o acesso ao módulo de avaliação para alunos com matrícula inativa.

### RF Relacionados

- RF08 — Avaliação Física
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados

- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas

- RN05 — Avaliação física somente para alunos ativos e regulares
- RN06 — Acesso restrito por perfil (Instrutor executa avaliações)

---

## UC08 — Gerenciar Matrículas

### Ator Principal

Recepcionista

### Objetivo

Permitir que a recepcionista consulte, edite, ative ou cancele matrículas de alunos.

### Pré-condições

- Recepcionista autenticada no sistema.
- Matrícula do aluno previamente registrada.

### Pós-condições

- Dados da matrícula atualizados conforme a operação realizada.
- Histórico de alterações registrado.

### Fluxo Principal

1. A recepcionista acessa o módulo de gerenciamento de matrículas.
2. O sistema exibe a lista de matrículas com filtros (ativas, inativas, inadimplentes etc.).
3. A recepcionista localiza o aluno pelo nome, CPF ou código.
4. A recepcionista seleciona a operação desejada: editar dados, ativar, suspender ou cancelar matrícula.
5. O sistema aplica a alteração e registra no histórico.
6. O sistema confirma a operação com mensagem de sucesso.

### Fluxos Alternativos

- **A1 — Aluno não encontrado:** O sistema exibe mensagem informando que nenhum cadastro foi localizado.
- **A2 — Tentativa de cancelamento com pendência financeira:** O sistema alerta sobre débitos em aberto antes de confirmar o cancelamento.

### RF Relacionados

- RF01 — Cadastro de Alunos
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados

- RNF04 — Usabilidade
- RNF02 — Segurança

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Recepcionista gerencia matrículas)

---

## UC09 — Indicar Planos

### Ator Principal

Recepcionista

### Objetivo

Apresentar ao aluno ou visitante as opções de planos disponíveis, auxiliando na escolha mais adequada.

### Pré-condições

- Recepcionista autenticada no sistema.
- Planos ativos cadastrados pelo gerente.

### Pós-condições

- Aluno orientado sobre as opções disponíveis.
- Plano selecionado vinculado ao aluno se confirmado.

### Fluxo Principal

1. A recepcionista acessa a listagem de planos disponíveis.
2. O sistema exibe todos os planos ativos com valores, duração e benefícios.
3. A recepcionista apresenta as opções ao aluno e tira dúvidas.
4. O aluno indica o plano de interesse.
5. A recepcionista vincula o plano selecionado ao cadastro do aluno.
6. O sistema confirma a associação e apresenta o valor da próxima cobrança.

### Fluxos Alternativos

- **A1 — Plano sem disponibilidade:** O sistema informa que o plano está temporariamente suspenso.
- **A2 — Aluno solicita plano personalizado:** A recepcionista orienta o aluno a contatar a gerência para negociação especial.

### RF Relacionados

- RF02 — Gerenciamento de Planos
- RF01 — Cadastro de Alunos

### RNF Relacionados

- RNF04 — Usabilidade

### RN Relacionadas

- RN06 — Acesso restrito por perfil

---

## UC10 — Gerenciar Pagamentos

### Ator Principal

Recepcionista

### Objetivo

Registrar, consultar e gerenciar pagamentos de mensalidades realizados pelos alunos.

### Pré-condições

- Recepcionista autenticada no sistema.
- Aluno com matrícula ativa e cobrança em aberto.

### Pós-condições

- Pagamento registrado e situação do aluno atualizada.
- Comprovante gerado para o aluno.

### Fluxo Principal

1. A recepcionista acessa o módulo financeiro de pagamentos.
2. O sistema exibe a lista de alunos com cobranças em aberto.
3. A recepcionista localiza o aluno e seleciona a cobrança a ser quitada.
4. A recepcionista informa a forma de pagamento (dinheiro, cartão, PIX).
5. O sistema registra o pagamento integral e emite comprovante.
6. O sistema atualiza o status do aluno para regular automaticamente.

### Fluxos Alternativos

- **A1 — Pagamento parcial:** O sistema bloqueia o registro e informa que apenas o valor integral é aceito.
- **A2 — Estorno de pagamento:** A recepcionista solicita estorno mediante justificativa; o sistema registra a operação e reverte a situação do aluno.

### RF Relacionados

- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados

- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas

- RN04 — Pagamento parcial não permitido
- RN07 — Atualização automática da regularidade
- RN06 — Acesso restrito por perfil

---

## UC11 — Gerenciar Horários e Agendamentos das Aulas

### Ator Principal

Recepcionista

### Objetivo

Criar, editar e controlar os horários das aulas e os agendamentos realizados pelos alunos.

### Pré-condições

- Recepcionista autenticada no sistema.
- Instrutores e aulas previamente cadastrados.

### Pós-condições

- Grade de horários atualizada e disponível para os alunos.
- Agendamentos registrados e associados a aulas e alunos.

### Fluxo Principal

1. A recepcionista acessa o módulo de agendamento.
2. O sistema exibe a grade de aulas com instrutores, horários e capacidades.
3. A recepcionista cria, edita ou remove horários de aulas conforme necessidade.
4. O sistema valida conflitos de horário e capacidade.
5. A recepcionista pode visualizar ou alterar agendamentos de alunos em aulas específicas.
6. O sistema confirma as alterações e notifica os alunos afetados.

### Fluxos Alternativos

- **A1 — Conflito de horário para o instrutor:** O sistema detecta sobreposição e bloqueia o cadastro do horário conflitante.
- **A2 — Aula com alunos agendados é removida:** O sistema alerta sobre os alunos inscritos e envia notificação de cancelamento antes de prosseguir.

### RF Relacionados

- RF06 — Agendamento de Aulas
- RF07 — Lista de Presença
- RF10 — Notificações

### RNF Relacionados

- RNF04 — Usabilidade
- RNF01 — Disponibilidade

### RN Relacionadas

- RN02 — Limite de vagas
- RN03 — Cancelamento de agendamento
- RN06 — Acesso restrito por perfil

---

## UC12 — Fornecer Horários Disponíveis para as Aulas

### Ator Principal

Instrutor

### Objetivo

Permitir que o instrutor informe sua disponibilidade de horários para ministrar aulas.

### Pré-condições

- Instrutor autenticado no sistema.
- Grade de aulas previamente configurada ou em configuração.

### Pós-condições

- Disponibilidade do instrutor registrada.
- Recepcionista e gerente podem visualizar e utilizar a disponibilidade para escalonamento.

### Fluxo Principal

1. O instrutor acessa o módulo de disponibilidade de horários.
2. O sistema exibe um calendário semanal para marcação de disponibilidade.
3. O instrutor seleciona os dias e horários em que está disponível.
4. O sistema valida e registra a disponibilidade informada.
5. O sistema confirma e disponibiliza as informações para a gestão.

### Fluxos Alternativos

- **A1 — Horário já alocado:** O sistema alerta que o horário informado já possui aula atribuída ao instrutor e solicita confirmação.
- **A2 — Sem disponibilidade no período:** O instrutor pode registrar indisponibilidade temporária com justificativa.

### RF Relacionados

- RF06 — Agendamento de Aulas
- RF07 — Lista de Presença

### RNF Relacionados

- RNF04 — Usabilidade

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Instrutor fornece horários)

---

## UC13 — Executar Avaliações Físicas

### Ator Principal

Instrutor

### Objetivo

Realizar e registrar a avaliação física completa do aluno, com possibilidade de anexar arquivos.

### Pré-condições

- Instrutor autenticado no sistema.
- Aluno ativo e regular (mensalidade em dia).
- Aluno deve ter solicitado ou ter avaliação liberada pelo sistema.

### Pós-condições

- Avaliação física salva no histórico do aluno.
- Aluno notificado sobre disponibilidade da avaliação.

### Fluxo Principal

1. O instrutor acessa o módulo de avaliação física.
2. O sistema exibe a lista de alunos com avaliação pendente ou a realizar.
3. O instrutor seleciona o aluno e verifica o histórico anterior de avaliações.
4. O instrutor coleta e registra os dados: peso, altura, IMC, percentual de gordura, circunferências e demais métricas.
5. O instrutor pode anexar arquivos (laudos, fotos, exames).
6. O sistema salva a avaliação e notifica o aluno.

### Fluxos Alternativos

- **A1 — Aluno inadimplente:** O sistema bloqueia o acesso à avaliação e exibe mensagem de irregularidade financeira.
- **A2 — Aluno inativo:** O sistema impede o registro para alunos com matrícula cancelada ou suspensa.

### RF Relacionados

- RF08 — Avaliação Física
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados

- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas

- RN05 — Avaliação física somente para alunos ativos e regulares
- RN06 — Acesso restrito por perfil

---

## UC14 — Cadastrar Facial na Catraca para Acesso do Instrutor

### Ator Principal

Instrutor / Recepcionista

### Objetivo

Registrar os dados biométricos faciais do instrutor no sistema de catraca para liberação de acesso à academia.

### Pré-condições

- Instrutor com cadastro ativo no sistema.
- Sistema de catraca integrado e operacional.

### Pós-condições

- Dados faciais do instrutor registrados na catraca.
- Instrutor apto a acessar a academia via reconhecimento facial.

### Fluxo Principal

1. A recepcionista ou o próprio instrutor acessa o módulo de controle de acesso.
2. O sistema localiza o cadastro do instrutor.
3. O sistema solicita a captura da imagem facial.
4. O instrutor posiciona-se para a leitura biométrica.
5. O sistema envia os dados à API da catraca via REST/JSON.
6. A catraca confirma o cadastro e o sistema registra com sucesso.

### Fluxos Alternativos

- **A1 — Leitura facial inválida:** O sistema solicita nova captura com orientação de posicionamento.
- **A2 — Falha de comunicação com a catraca:** O sistema exibe mensagem de erro e orienta nova tentativa após verificação da integração.

### RF Relacionados

- RF05 — Controle de Acesso

### RNF Relacionados

- RNF06 — Integração (API REST/JSON)
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas

- RN06 — Acesso restrito por perfil

---

## UC15 — Gerenciar Planos

### Ator Principal

Gerente

### Objetivo

Criar, editar, ativar e desativar planos oferecidos pela academia.

### Pré-condições

- Gerente autenticado no sistema.
- Acesso ao módulo de configuração de planos.

### Pós-condições

- Plano criado, editado ou desativado conforme solicitado.
- Lista de planos atualizada e disponível para recepcionistas e alunos.

### Fluxo Principal

1. O gerente acessa o módulo de gerenciamento de planos.
2. O sistema exibe os planos cadastrados com status (ativo/inativo) e detalhes.
3. O gerente seleciona criar novo plano ou editar um existente.
4. O gerente preenche nome, valor, duração, modalidades incluídas e demais condições.
5. O sistema valida as informações e salva o plano.
6. O sistema exibe confirmação e atualiza a listagem de planos disponíveis.

### Fluxos Alternativos

- **A1 — Desativação de plano com alunos vinculados:** O sistema alerta que há alunos associados ao plano e solicita confirmação antes de desativar.
- **A2 — Dados inválidos:** O sistema destaca os campos incorretos e impede o salvamento até a correção.

### RF Relacionados

- RF02 — Gerenciamento de Planos

### RNF Relacionados

- RNF04 — Usabilidade
- RNF05 — Escalabilidade
- RNF02 — Segurança

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Gerente configura planos)

---

## UC16 — Análise de Relatórios Gerenciais

### Ator Principal

Gerente

### Objetivo

Emitir e analisar relatórios sobre inadimplência, alunos ativos, histórico de acessos e ocupação das aulas.

### Pré-condições

- Gerente autenticado no sistema.
- Dados de alunos, pagamentos e aulas disponíveis no sistema.

### Pós-condições

- Relatório gerado e exibido ao gerente.
- Possibilidade de exportar os dados.

### Fluxo Principal

1. O gerente acessa o módulo de relatórios.
2. O sistema exibe as categorias de relatórios disponíveis.
3. O gerente seleciona o tipo de relatório desejado e aplica filtros (período, unidade etc.).
4. O sistema processa os dados e exibe o relatório com gráficos e tabelas.
5. O gerente pode exportar o relatório em PDF ou planilha.

### Fluxos Alternativos

- **A1 — Sem dados no período selecionado:** O sistema exibe mensagem informando ausência de registros no filtro aplicado.
- **A2 — Falha no processamento:** O sistema exibe mensagem de erro e orienta nova tentativa.

### RF Relacionados

- RF09 — Relatórios Gerenciais
- RF04 — Regularidade do Aluno
- RF05 — Controle de Acesso
- RF07 — Lista de Presença

### RNF Relacionados

- RNF01 — Disponibilidade
- RNF05 — Escalabilidade
- RNF03 — Performance

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Gerente acessa relatórios)

---

## UC17 — Gerir Pagamentos de Funcionários

### Ator Principal

Gerente

### Objetivo

Registrar e acompanhar os pagamentos de salários e comissões dos funcionários da academia.

### Pré-condições

- Gerente autenticado no sistema.
- Funcionários cadastrados no sistema com dados bancários e tipo de remuneração.

### Pós-condições

- Pagamento registrado e histórico atualizado.
- Comprovante de pagamento gerado.

### Fluxo Principal

1. O gerente acessa o módulo financeiro de funcionários.
2. O sistema exibe a lista de funcionários com competências e valores a pagar.
3. O gerente seleciona o funcionário e verifica o valor calculado (salário, comissões, descontos).
4. O gerente confirma o pagamento e informa a data de processamento.
5. O sistema registra o pagamento e emite comprovante.
6. O sistema atualiza o histórico financeiro do funcionário.

### Fluxos Alternativos

- **A1 — Divergência nos valores:** O gerente pode ajustar manualmente o valor com justificativa antes de confirmar.
- **A2 — Funcionário sem dados bancários:** O sistema alerta sobre a ausência de dados e bloqueia o pagamento eletrônico até a regularização.

### RF Relacionados

- RF03 — Controle de Pagamentos
- RF09 — Relatórios Gerenciais

### RNF Relacionados

- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Gerente gere pagamentos de funcionários)

---

## UC18 — Analisar Presença de Alunos

### Ator Principal

Gerente

### Objetivo

Visualizar e analisar a frequência dos alunos nas aulas e no uso geral da academia.

### Pré-condições

- Gerente autenticado no sistema.
- Registros de presença lançados pelos instrutores.

### Pós-condições

- Relatório de presença gerado com dados consolidados por período, aula ou aluno.

### Fluxo Principal

1. O gerente acessa o módulo de análise de presença.
2. O sistema exibe opções de visualização: por aluno, por aula, por período ou por instrutor.
3. O gerente aplica os filtros desejados.
4. O sistema processa e exibe os dados com taxa de frequência, faltas e tendências.
5. O gerente pode exportar o relatório ou compartilhar internamente.

### Fluxos Alternativos

- **A1 — Sem registros de presença no período:** O sistema exibe mensagem informando ausência de dados para os filtros aplicados.

### RF Relacionados

- RF07 — Lista de Presença
- RF09 — Relatórios Gerenciais
- RF06 — Agendamento de Aulas

### RNF Relacionados

- RNF05 — Escalabilidade
- RNF03 — Performance
- RNF01 — Disponibilidade

### RN Relacionadas

- RN06 — Acesso restrito por perfil (Gerente analisa dados)

---

## UC19 — Sincronizar Matrículas com a Catraca

### Ator Principal

Sistema de Catraca

### Objetivo

Garantir que o sistema de catraca possua os dados atualizados de todos os alunos aptos a acessar a academia.

### Pré-condições

- Sistema FitPass integrado à API da catraca.
- Matrícula de aluno criada, atualizada ou cancelada no sistema.

### Pós-condições

- Dados de acesso do aluno sincronizados com a catraca em tempo real.
- Catraca apta a validar ou negar o acesso conforme a situação do aluno.

### Fluxo Principal

1. O sistema FitPass detecta uma alteração em matrícula (novo cadastro, atualização ou cancelamento).
2. O sistema envia a requisição de sincronização à API da catraca via REST/JSON.
3. A catraca processa os dados recebidos e atualiza sua base local.
4. A catraca retorna confirmação de sincronização ao sistema FitPass.
5. O sistema registra o log de sincronização com status de sucesso.

### Fluxos Alternativos

- **A1 — Falha na comunicação com a catraca:** O sistema registra o erro, enfileira a sincronização pendente e realiza nova tentativa automaticamente.
- **A2 — Dados rejeitados pela catraca:** O sistema registra o erro de validação no log e notifica o administrador para verificação.

### RF Relacionados

- RF05 — Controle de Acesso
- RF01 — Cadastro de Alunos

### RNF Relacionados

- RNF06 — Integração (API REST/JSON)
- RNF03 — Performance
- RNF01 — Disponibilidade

### RN Relacionadas

- RN01 — Bloqueio por inadimplência
- RN07 — Atualização automática da regularidade

---

## UC20 — Bloquear Acesso de Alunos com Pagamentos Atrasados

### Ator Principal

Sistema de Catraca

### Objetivo

Impedir automaticamente o acesso à academia de alunos com mensalidade em atraso superior ao prazo permitido.

### Pré-condições

- Sistema de catraca integrado ao FitPass.
- Aluno com mensalidade vencida há mais de 5 dias.

### Pós-condições

- Acesso do aluno bloqueado na catraca.
- Aluno notificado sobre a inadimplência e orientado a regularizar o pagamento.

### Fluxo Principal

1. O sistema FitPass identifica alunos com mensalidade vencida há mais de 5 dias.
2. O sistema atualiza o status do aluno para "bloqueado por inadimplência".
3. O sistema envia a instrução de bloqueio à catraca via API REST/JSON.
4. A catraca registra o bloqueio e nega o acesso ao aluno na próxima tentativa.
5. O sistema envia notificação ao aluno informando o bloqueio e orientando o pagamento.
6. Ao regularizar o pagamento, o sistema envia desbloqueio automático à catraca.

### Fluxos Alternativos

- **A1 — Aluno tenta acesso bloqueado:** A catraca nega a passagem e exibe mensagem orientando o aluno a contatar a recepção.
- **A2 — Falha ao enviar bloqueio à catraca:** O sistema registra a falha, tenta novamente e notifica o administrador caso persista.

### RF Relacionados

- RF05 — Controle de Acesso
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados

- RNF06 — Integração (API REST/JSON)
- RNF03 — Performance
- RNF01 — Disponibilidade

### RN Relacionadas

- RN01 — Bloqueio por inadimplência (vencida há mais de 5 dias)
- RN07 — Atualização automática da regularidade
