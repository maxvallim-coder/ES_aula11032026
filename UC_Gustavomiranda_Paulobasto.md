# UC_GustavoMiranda_PauloBastos.md

# Documento de Casos de Uso
**Sistema:** FitPass Gym Management  
**Alunos:** Gustavo Miranda e Paulo Bastos  

---

## UC01 – Cadastrar aluno

**Atores:** Recepcionista  
**Pré-condições:** O recepcionista deve estar autenticado no sistema.  
**Pós-condições:** O aluno é cadastrado com sucesso no sistema e fica apto a realizar matrícula em um plano.  

### Fluxo principal
1. O recepcionista acessa a opção de cadastro de aluno.
2. O sistema exibe o formulário de cadastro.
3. O recepcionista informa os dados pessoais do aluno.
4. O sistema valida os dados informados.
5. O recepcionista confirma o cadastro.
6. O sistema registra o aluno na base de dados.
7. O sistema exibe mensagem de sucesso.

### Fluxos alternativos
**FA1. Dados obrigatórios não informados**
1. O sistema identifica ausência de campos obrigatórios.
2. O sistema informa os campos pendentes.
3. O recepcionista corrige os dados e retoma o fluxo principal.

**FA2. Aluno já cadastrado**
1. O sistema identifica aluno já existente com mesmo documento.
2. O sistema informa a duplicidade.
3. O cadastro não é concluído.

**Requisitos funcionais relacionados:** Cadastro de alunos, matrículas  
**Requisitos não funcionais relacionados:** Validação de dados, usabilidade, segurança  
**Regras de negócio relacionadas:** Não permitir cadastro duplicado; campos obrigatórios devem ser preenchidos.

---

## UC02 – Atualizar dados do aluno

**Atores:** Recepcionista, Aluno  
**Pré-condições:** O aluno deve estar cadastrado no sistema.  
**Pós-condições:** Os dados do aluno são atualizados com sucesso.  

### Fluxo principal
1. O ator solicita a atualização dos dados cadastrais.
2. O sistema localiza o cadastro do aluno.
3. O sistema exibe os dados atuais.
4. O ator altera as informações desejadas.
5. O sistema valida os dados atualizados.
6. O ator confirma a atualização.
7. O sistema salva as alterações.

### Fluxos alternativos
**FA1. Aluno não encontrado**
1. O sistema não localiza o cadastro.
2. O sistema informa que o aluno não foi encontrado.

**FA2. Dados inválidos**
1. O sistema detecta inconsistência nos dados informados.
2. O sistema solicita correção.
3. O ator corrige e retoma o fluxo principal.

**Requisitos funcionais relacionados:** Matrículas, cadastro de alunos  
**Requisitos não funcionais relacionados:** Integridade dos dados, segurança  
**Regras de negócio relacionadas:** Apenas usuários autorizados podem atualizar dados.

---

## UC03 – Cadastrar plano

**Atores:** Gerente  
**Pré-condições:** O gerente deve estar autenticado no sistema.  
**Pós-condições:** Um novo plano é registrado e fica disponível para matrícula.  

### Fluxo principal
1. O gerente acessa a opção de cadastro de plano.
2. O sistema exibe o formulário do plano.
3. O gerente informa nome, valor, duração e benefícios.
4. O sistema valida os dados.
5. O gerente confirma o cadastro.
6. O sistema registra o plano.
7. O sistema exibe confirmação.

### Fluxos alternativos
**FA1. Dados obrigatórios ausentes**
1. O sistema aponta os campos obrigatórios não preenchidos.
2. O gerente corrige as informações.

**FA2. Plano duplicado**
1. O sistema identifica plano já existente com mesmo nome e configuração.
2. O sistema informa a duplicidade.

**Requisitos funcionais relacionados:** Planos  
**Requisitos não funcionais relacionados:** Segurança, usabilidade  
**Regras de negócio relacionadas:** O plano deve possuir valor e duração válidos.

---

## UC04 – Atualizar plano

**Atores:** Gerente  
**Pré-condições:** O plano deve estar cadastrado no sistema.  
**Pós-condições:** Os dados do plano são atualizados.  

### Fluxo principal
1. O gerente seleciona um plano existente.
2. O sistema exibe os dados do plano.
3. O gerente altera as informações desejadas.
4. O sistema valida os novos dados.
5. O gerente confirma as alterações.
6. O sistema atualiza o plano.

### Fluxos alternativos
**FA1. Plano não encontrado**
1. O sistema informa que o plano não foi localizado.

**FA2. Dados inválidos**
1. O sistema informa inconsistência nos dados.
2. O gerente corrige as informações.

**Requisitos funcionais relacionados:** Planos  
**Requisitos não funcionais relacionados:** Integridade dos dados, segurança  
**Regras de negócio relacionadas:** Alterações em planos devem respeitar políticas da academia.

---

## UC05 – Realizar matrícula do aluno em plano

**Atores:** Recepcionista  
**Pré-condições:** O aluno deve estar cadastrado; deve existir pelo menos um plano ativo.  
**Pós-condições:** A matrícula do aluno é registrada e vinculada a um plano.  

### Fluxo principal
1. O recepcionista acessa a opção de matrícula.
2. O sistema solicita a identificação do aluno.
3. O recepcionista seleciona o aluno.
4. O sistema exibe os planos disponíveis.
5. O recepcionista escolhe o plano desejado.
6. O sistema registra a matrícula.
7. O sistema informa a conclusão da matrícula.

### Fluxos alternativos
**FA1. Aluno não cadastrado**
1. O sistema informa que o aluno não existe.
2. O recepcionista deve realizar o cadastro antes da matrícula.

**FA2. Nenhum plano disponível**
1. O sistema informa ausência de planos ativos.
2. A matrícula não é concluída.

**Requisitos funcionais relacionados:** Matrículas, planos  
**Requisitos não funcionais relacionados:** Desempenho, integridade dos dados  
**Regras de negócio relacionadas:** O aluno deve estar cadastrado antes da matrícula.

---

## UC06 – Renovar matrícula

**Atores:** Recepcionista  
**Pré-condições:** O aluno deve possuir matrícula anterior ou ativa.  
**Pós-condições:** A matrícula é renovada por novo período.  

### Fluxo principal
1. O recepcionista localiza a matrícula do aluno.
2. O sistema exibe os dados da matrícula atual.
3. O recepcionista seleciona a opção de renovação.
4. O sistema apresenta os planos disponíveis.
5. O recepcionista escolhe o plano da renovação.
6. O sistema registra a renovação.
7. O sistema confirma a operação.

### Fluxos alternativos
**FA1. Matrícula inexistente**
1. O sistema informa que não há matrícula vinculada ao aluno.

**FA2. Plano indisponível**
1. O sistema informa que o plano escolhido não está disponível.
2. O recepcionista seleciona outro plano.

**Requisitos funcionais relacionados:** Matrículas, planos  
**Requisitos não funcionais relacionados:** Integridade, confiabilidade  
**Regras de negócio relacionadas:** Renovação depende da existência de histórico do aluno.

---

## UC07 – Cancelar matrícula

**Atores:** Recepcionista, Gerente  
**Pré-condições:** O aluno deve possuir matrícula ativa.  
**Pós-condições:** A matrícula é cancelada e o aluno perde os benefícios associados.  

### Fluxo principal
1. O ator localiza a matrícula ativa do aluno.
2. O sistema exibe os dados da matrícula.
3. O ator solicita o cancelamento.
4. O sistema solicita confirmação.
5. O ator confirma a operação.
6. O sistema registra o cancelamento.
7. O sistema exibe mensagem de sucesso.

### Fluxos alternativos
**FA1. Matrícula não encontrada**
1. O sistema informa que não existe matrícula ativa.

**FA2. Cancelamento não autorizado**
1. O sistema identifica falta de permissão do usuário.
2. O cancelamento é bloqueado.

**Requisitos funcionais relacionados:** Matrículas  
**Requisitos não funcionais relacionados:** Segurança, rastreabilidade  
**Regras de negócio relacionadas:** Apenas usuários autorizados podem cancelar matrícula.

---

## UC08 – Registrar pagamento

**Atores:** Recepcionista  
**Pré-condições:** O aluno deve possuir matrícula ou cobrança associada.  
**Pós-condições:** O pagamento é registrado no sistema.  

### Fluxo principal
1. O recepcionista localiza o aluno ou a cobrança pendente.
2. O sistema exibe os dados financeiros.
3. O recepcionista informa o pagamento realizado.
4. O sistema valida valor e referência.
5. O recepcionista confirma o registro.
6. O sistema grava o pagamento.
7. O sistema atualiza a situação financeira do aluno.

### Fluxos alternativos
**FA1. Cobrança inexistente**
1. O sistema informa que não há cobrança pendente.

**FA2. Valor divergente**
1. O sistema detecta valor incompatível.
2. O sistema solicita conferência.
3. O recepcionista corrige ou confirma conforme regra interna.

**Requisitos funcionais relacionados:** Pagamentos  
**Requisitos não funcionais relacionados:** Segurança, integridade, auditoria  
**Regras de negócio relacionadas:** Pagamentos devem ser vinculados a uma cobrança ou matrícula válida.

---

## UC09 – Consultar histórico de pagamentos

**Atores:** Recepcionista, Gerente, Aluno  
**Pré-condições:** O aluno deve estar cadastrado.  
**Pós-condições:** O histórico financeiro é exibido ao ator autorizado.  

### Fluxo principal
1. O ator solicita a consulta do histórico de pagamentos.
2. O sistema solicita a identificação do aluno.
3. O ator informa ou seleciona o aluno.
4. O sistema recupera o histórico financeiro.
5. O sistema exibe pagamentos realizados, pendências e datas.

### Fluxos alternativos
**FA1. Aluno não encontrado**
1. O sistema informa que o aluno não foi localizado.

**FA2. Sem histórico**
1. O sistema informa que não existem pagamentos registrados para o aluno.

**Requisitos funcionais relacionados:** Pagamentos, relatórios  
**Requisitos não funcionais relacionados:** Desempenho, segurança  
**Regras de negócio relacionadas:** Apenas perfis autorizados podem consultar dados financeiros.

---

## UC10 – Registrar identificação RFID do aluno

**Atores:** Recepcionista  
**Pré-condições:** O aluno deve estar cadastrado.  
**Pós-condições:** O identificador RFID fica vinculado ao aluno.  

### Fluxo principal
1. O recepcionista acessa a opção de vincular RFID.
2. O sistema solicita a identificação do aluno.
3. O recepcionista seleciona o aluno.
4. O recepcionista informa ou aproxima o dispositivo RFID.
5. O sistema valida o identificador.
6. O sistema vincula o RFID ao cadastro do aluno.
7. O sistema confirma o vínculo.

### Fluxos alternativos
**FA1. RFID já vinculado**
1. O sistema detecta que o identificador já está associado a outro aluno.
2. O sistema bloqueia a operação.

**FA2. Aluno inexistente**
1. O sistema informa que o aluno não foi encontrado.

**Requisitos funcionais relacionados:** Controle de acesso por catraca (RFID), matrículas  
**Requisitos não funcionais relacionados:** Segurança, confiabilidade  
**Regras de negócio relacionadas:** Um RFID não pode estar vinculado a mais de um aluno.

---

## UC11 – Validar acesso na catraca

**Atores:** Sistema de Catraca (API externa), Sistema FitPass  
**Pré-condições:** O aluno deve possuir RFID cadastrado; a integração deve estar disponível.  
**Pós-condições:** O acesso é autorizado ou negado e o evento é registrado.  

### Fluxo principal
1. O aluno aproxima o RFID na catraca.
2. A catraca envia a solicitação para o sistema FitPass.
3. O sistema localiza o aluno vinculado ao RFID.
4. O sistema verifica situação da matrícula e pagamento.
5. O sistema retorna autorização de acesso.
6. A catraca libera a entrada.
7. O sistema registra o evento de acesso.

### Fluxos alternativos
**FA1. RFID não encontrado**
1. O sistema não identifica o RFID.
2. O sistema retorna acesso negado.
3. O evento é registrado.

**FA2. Matrícula irregular**
1. O sistema verifica matrícula inativa ou pendência financeira.
2. O sistema retorna acesso negado.

**FA3. Falha na integração**
1. A comunicação com a catraca falha.
2. O sistema registra erro de integração.
3. O acesso não é autorizado automaticamente.

**Requisitos funcionais relacionados:** Controle de acesso por catraca (RFID), pagamentos, matrículas  
**Requisitos não funcionais relacionados:** Disponibilidade, desempenho, confiabilidade  
**Regras de negócio relacionadas:** Apenas alunos regulares podem acessar a academia.

---

## UC12 – Cadastrar aula/turma

**Atores:** Instrutor, Gerente  
**Pré-condições:** O ator deve estar autenticado e autorizado.  
**Pós-condições:** A aula/turma fica disponível para agendamento.  

### Fluxo principal
1. O ator acessa a opção de cadastro de aula.
2. O sistema exibe o formulário da aula/turma.
3. O ator informa nome, horário, capacidade e instrutor responsável.
4. O sistema valida os dados.
5. O ator confirma o cadastro.
6. O sistema registra a aula/turma.
7. O sistema disponibiliza a aula para agendamento.

### Fluxos alternativos
**FA1. Dados inválidos**
1. O sistema informa inconsistências nos dados.
2. O ator corrige e continua.

**FA2. Conflito de horário**
1. O sistema identifica conflito com outra aula ou instrutor.
2. O sistema informa o problema.
3. O ator ajusta o horário.

**Requisitos funcionais relacionados:** Agendamento de aulas  
**Requisitos não funcionais relacionados:** Integridade, usabilidade  
**Regras de negócio relacionadas:** Não deve haver conflito de horário para a mesma turma ou instrutor.

---

## UC13 – Agendar aula

**Atores:** Aluno, Recepcionista  
**Pré-condições:** O aluno deve possuir matrícula ativa; a aula deve possuir vaga disponível.  
**Pós-condições:** O agendamento da aula é registrado.  

### Fluxo principal
1. O ator acessa a lista de aulas disponíveis.
2. O sistema exibe as aulas com datas e horários.
3. O ator seleciona a aula desejada.
4. O sistema verifica disponibilidade de vaga.
5. O sistema registra o agendamento.
6. O sistema exibe confirmação.

### Fluxos alternativos
**FA1. Aula lotada**
1. O sistema informa indisponibilidade de vagas.
2. O agendamento não é concluído.

**FA2. Matrícula inativa**
1. O sistema identifica que o aluno não está regular.
2. O sistema impede o agendamento.

**Requisitos funcionais relacionados:** Agendamento de aulas, matrículas  
**Requisitos não funcionais relacionados:** Desempenho, disponibilidade  
**Regras de negócio relacionadas:** Apenas alunos com matrícula ativa podem agendar aulas.

---

## UC14 – Cancelar agendamento de aula

**Atores:** Aluno, Recepcionista  
**Pré-condições:** Deve existir agendamento previamente registrado.  
**Pós-condições:** O agendamento é cancelado e a vaga é liberada.  

### Fluxo principal
1. O ator consulta os agendamentos do aluno.
2. O sistema exibe a lista de aulas agendadas.
3. O ator seleciona o agendamento a cancelar.
4. O sistema solicita confirmação.
5. O ator confirma.
6. O sistema cancela o agendamento.
7. O sistema libera a vaga.

### Fluxos alternativos
**FA1. Agendamento inexistente**
1. O sistema informa que o agendamento não foi encontrado.

**FA2. Prazo de cancelamento expirado**
1. O sistema identifica que o cancelamento não é mais permitido.
2. O sistema informa a restrição.

**Requisitos funcionais relacionados:** Agendamento de aulas  
**Requisitos não funcionais relacionados:** Integridade, rastreabilidade  
**Regras de negócio relacionadas:** O cancelamento pode estar sujeito a prazo definido pela academia.

---

## UC15 – Registrar presença em aula

**Atores:** Instrutor  
**Pré-condições:** A aula deve estar cadastrada; deve haver alunos agendados.  
**Pós-condições:** A presença dos alunos é registrada.  

### Fluxo principal
1. O instrutor acessa a aula em andamento ou concluída.
2. O sistema exibe a lista de alunos agendados.
3. O instrutor marca os alunos presentes.
4. O sistema registra as presenças.
5. O sistema confirma o registro.

### Fluxos alternativos
**FA1. Aula sem alunos agendados**
1. O sistema informa que não há alunos vinculados à aula.

**FA2. Tentativa de registro duplicado**
1. O sistema identifica presença já registrada.
2. O sistema informa ao instrutor.

**Requisitos funcionais relacionados:** Presença em aulas, agendamento de aulas  
**Requisitos não funcionais relacionados:** Integridade, usabilidade  
**Regras de negócio relacionadas:** A presença deve ser vinculada a uma aula válida e a um aluno agendado.

---

## UC16 – Consultar presença em aulas

**Atores:** Aluno, Instrutor, Gerente  
**Pré-condições:** Devem existir registros de presença.  
**Pós-condições:** O histórico de presenças é exibido.  

### Fluxo principal
1. O ator solicita a consulta de presenças.
2. O sistema identifica o aluno ou a turma consultada.
3. O sistema recupera os registros de presença.
4. O sistema exibe os resultados.

### Fluxos alternativos
**FA1. Sem registros encontrados**
1. O sistema informa que não existem presenças registradas.

**Requisitos funcionais relacionados:** Presença em aulas, relatórios  
**Requisitos não funcionais relacionados:** Desempenho, segurança  
**Regras de negócio relacionadas:** A consulta deve respeitar permissões de acesso.

---

## UC17 – Registrar avaliação física

**Atores:** Instrutor  
**Pré-condições:** O aluno deve estar cadastrado.  
**Pós-condições:** A avaliação física do aluno é registrada no sistema.  

### Fluxo principal
1. O instrutor acessa a opção de avaliação física.
2. O sistema solicita a identificação do aluno.
3. O instrutor seleciona o aluno.
4. O sistema exibe formulário de avaliação.
5. O instrutor informa os dados coletados.
6. O sistema valida as informações.
7. O instrutor confirma o registro.
8. O sistema salva a avaliação.

### Fluxos alternativos
**FA1. Aluno não encontrado**
1. O sistema informa que o aluno não está cadastrado.

**FA2. Dados incompletos**
1. O sistema informa campos obrigatórios não preenchidos.
2. O instrutor corrige e continua.

**Requisitos funcionais relacionados:** Avaliações físicas  
**Requisitos não funcionais relacionados:** Segurança, integridade, confidencialidade  
**Regras de negócio relacionadas:** Apenas instrutores autorizados podem registrar avaliações físicas.

---

## UC18 – Consultar avaliação física

**Atores:** Aluno, Instrutor  
**Pré-condições:** Deve existir ao menos uma avaliação registrada.  
**Pós-condições:** As avaliações do aluno são exibidas.  

### Fluxo principal
1. O ator solicita a consulta da avaliação física.
2. O sistema localiza o histórico do aluno.
3. O sistema exibe as avaliações registradas.

### Fluxos alternativos
**FA1. Nenhuma avaliação encontrada**
1. O sistema informa ausência de avaliações cadastradas.

**Requisitos funcionais relacionados:** Avaliações físicas  
**Requisitos não funcionais relacionados:** Segurança, confidencialidade  
**Regras de negócio relacionadas:** O acesso às avaliações deve respeitar perfil de usuário.

---

## UC19 – Emitir relatório gerencial de matrículas e alunos

**Atores:** Gerente  
**Pré-condições:** O gerente deve estar autenticado.  
**Pós-condições:** O relatório é exibido ou gerado para consulta.  

### Fluxo principal
1. O gerente acessa a área de relatórios.
2. O sistema exibe os tipos de relatório disponíveis.
3. O gerente seleciona o relatório de matrículas e alunos.
4. O gerente informa filtros, se desejado.
5. O sistema processa os dados.
6. O sistema exibe ou gera o relatório.

### Fluxos alternativos
**FA1. Sem dados para o período**
1. O sistema informa que não existem dados para os filtros informados.

**Requisitos funcionais relacionados:** Relatórios gerenciais, matrículas  
**Requisitos não funcionais relacionados:** Desempenho, confiabilidade  
**Regras de negócio relacionadas:** Relatórios gerenciais são restritos a perfis autorizados.

---

## UC20 – Emitir relatório financeiro e de frequência

**Atores:** Gerente  
**Pré-condições:** O gerente deve estar autenticado.  
**Pós-condições:** O relatório financeiro e/ou de frequência é disponibilizado.  

### Fluxo principal
1. O gerente acessa a área de relatórios.
2. O sistema apresenta os relatórios disponíveis.
3. O gerente seleciona relatório financeiro ou de frequência.
4. O gerente informa período e filtros.
5. O sistema reúne os dados de pagamentos e/ou presenças.
6. O sistema gera o relatório.
7. O sistema apresenta o resultado.

### Fluxos alternativos
**FA1. Período inválido**
1. O sistema informa que o período informado é inválido.
2. O gerente corrige os dados.

**FA2. Nenhum registro encontrado**
1. O sistema informa ausência de dados para o filtro selecionado.

**Requisitos funcionais relacionados:** Relatórios gerenciais, pagamentos, presença em aulas  
**Requisitos não funcionais relacionados:** Desempenho, confiabilidade, segurança  
**Regras de negócio relacionadas:** Apenas gerentes podem acessar relatórios financeiros consolidados.

---
