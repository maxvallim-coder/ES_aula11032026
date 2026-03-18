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
- O sistema deve permitir autenticação de usuários.

### RNF Relacionados
- O login deve ser realizado em até 2 segundos.

### RN Relacionadas
- O usuário pode errar a senha no máximo 5 vezes.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC02 – Fazer logout
### Ator Principal
Usuário: 

### Objetivo
Permitir que o usuário encerre.

### Pré-condições
- Usuário deve estar logado.

### Pós-condições
- A sessão será encerrada.

### Fluxo Principal
1. O usuário seleciona a opção logout.
2. O sistema encerra.
3. O sistema o joga para a tela inicial.

### Fluxos Alternativos
- **Nenhum

### RF Relacionados
- O sistema deve permitir que o usuário encerre a sessão.

### RNF Relacionados
- O logout deve ser realizado imediatamente.

### RN Relacionadas
- Após logout, o usuário deve realizar login novamente.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC03 – Cadastrar usuário

### Ator Principal
Administrador

### Objetivo
Permitir que o administrador cadastre um novo usuário.

### Pré-condições
- O administrador deve estar no sistema.

### Pós-condições
- Um novo usuário será registrado no sistema.

### Fluxo Principal
1. O administrador acessa a tela de cadastro.
2. O administrador adiciona os dados do usuário.
3. O sistema valida as informações.
4. O sistema salva o usuário no banco de dados.

### Fluxos Alternativos
- **A1 — Dados inválidos:**  
  O sistema exibe mensagem de erro.
  O administrador corrige os dados.

### RF Relacionados
- O sistema deve permitir cadastro de usuários.

### RNF Relacionados
- O sistema deve armazenar os dados com segurança.

### RN Relacionadas
- Cada usuário deve possuir um email único.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC04 – Editar usuário

### Ator Principal
Administrador

### Objetivo
O administrador altera dados dos usuários.

### Pré-condições
O usuário deve existir no sistema.

### Pós-condições
Os dados do usuário serão atualizados.

### Fluxo Principal
1. O administrador busca o usuário.
2. O administrador seleciona editar.
3. O administrador altera os dados.

### Fluxos Alternativos
- **A1 — Dados inválidos:**  
  O sistema exibe mensagem de erro.
  O administrador corrige os dados.

### RF Relacionados
O sistema deve permitir edição de usuários.

### RNF Relacionados
- As alterações devem ser registradas no sistema.

### RN Relacionadas
- Apenas administradores podem editar usuários.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

UC05 – Excluir usuário

### Ator Principal
Administrador

### Objetivo
Permitir que o administrador exclua usuários.

### Pré-condições
- O usuário deve existir no sistema.

### Pós-condições
- O usuário será excluído do sistema.

### Fluxo Principal
1. O administrador localiza o usuário.
2. O administrador seleciona excluir.
3. O sistema solicita confirmação.
4. O administrador confirma.
5. O sistema remove o usuário.

### Fluxos Alternativos
- **A1 — Cancelamento:**  
 O administrador cancela a operação.

### RF Relacionados
- O sistema deve permitir exclusão de usuários.

### RNF Relacionados
- A exclusão deve ser registrada em log.

### RN Relacionadas
- Apenas administradores podem excluir usuários.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC06 – Consultar usuário

### Ator Principal
Administrador.

### Objetivo
Permitir que o administrador encontre o usuário.

### Pré-condições
- Usuários devem estar cadastrados.

### Pós-condições
- As informações do usuário serão exibidas.

### Fluxo Principal
1. O administrador acessa a tela de consulta.
2. O administrador digita o nome ou email.
3. O sistema exibe os resultados.

### Fluxos Alternativos
- **A1 — Usuário não encontrado:**  
 O sistema informa que não há resultados.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- O sistema deve permitir busca de usuários.

### RNF Relacionados
- A busca deve ocorrer em até 2 segundos.

### RN Relacionadas
- Apenas administradores podem visualizar todos os usuários.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

UC07 – Cadastrar produto

### Ator Principal
Administrador

### Objetivo
Permitir que o administrador cadastre um produto.

### Pré-condições
- O administrador deve estar logado.

### Pós-condições
- O produto será registrado no sistema.

### Fluxo Principal
1. O administrador acessa cadastro de produto.
2. O administrador insere dados do produto.
3. O sistema valida as informações.
4. O sistema salva o produto.

### Fluxos Alternativos
- **A1 — Dados inválidos:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- O sistema deve permitir cadastro de produtos.

### RNF Relacionados
- Os dados devem ser armazenados de forma segura.

### RN Relacionadas
- Cada produto deve possuir código único.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC08 – Editar produto

### Ator Principal
Administrador

### Objetivo
Permitir que o adminstrador altere o produto.

### Pré-condições
- Produto extiste

### Pós-condições
- Dados do produto atualizado.

### Fluxo Principal
1. O administrador busca produto.
2. Seleciona editar.
3. Altera informações.
4. Sistema salva alterações.

### Fluxos Alternativos
- **A1 — Erro nos dados:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- O sistema deve permitir edição de produtos.

### RNF Relacionados
- Alterações devem ser registradas.

### RN Relacionadas
- Apenas administradores podem editar produtos.
  
---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC09 – Excluir produto

### Ator Principal
Administrador.

### Objetivo
Permitir a exclusão de um produto.

### Pré-condições
- Produto cadastrado

### Pós-condições
- Produto removido.

### Fluxo Principal
1. Administrador seleciona produto.
2. Clica em excluir.
3. Confirma exclusão.
4. Sistema remove produto.

### Fluxos Alternativos
- **A1 — Cancelamento da exclusão:**  

### RF Relacionados
- O sistema deve permitir exclusão de produtos.

### RNF Relacionados
- Exclusões devem ser registradas.

### RN Relacionadas
- Produtos com vendas registradas não podem ser excluídos.

---------------------------------------------------------------------------
---------------------------------------------------------------------------
##UC10 – Consultar produto

### Ator Principal
Usuário

### Objetivo.
Encontrar o produto dentro do sistema.

### Pré-condições
- Produto cadastrado.

### Pós-condições
- Exibir lista de produtos.

### Fluxo Principal
1. Usuário acessa tela de produtos.
2. O sistema exibe.

### Fluxos Alternativos
- **A1 — Nenhum produto encontrado:**  
  O sistema exibe mensagem de erro.
  
### RF Relacionados
- O sistema deve permitir consulta de produtos.

### RNF Relacionados
- Consulta deve ocorrer rapidamente.

### RN Relacionadas
- Apenas produtos ativos devem ser exibidos.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

UC11 – Registrar venda

### Ator Principal
Funcionário.

### Objetivo
Exibir vendas.

### Pré-condições
- Produtos cadastrados.

### Pós-condições
- Venda registrada.

### Fluxo Principal
1. Funcionário seleciona produto.
2. Informa quantidade.
3. Sistema calcula valor.
4. Sistema registra venda.

### Fluxos Alternativos
- **A1 — Produto sem estoque:**  
  O sistema exibe mensagem de produto inexistente.

### RF Relacionados
- O sistema deve registrar vendas.

### RNF Relacionados
- Operação deve ser rápida.

### RN Relacionadas
- Venda só ocorre se houver estoque.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC12 – Cancelar venda

### Ator Principal
Administrador

### Objetivo
Cancelamento de venda.

### Pré-condições
- Venda registrada.

### Pós-condições
- Venda cancelada.

### Fluxo Principal
1. Administrador localiza venda.
2. Seleciona cancelar.
3. Sistema cancela registro.

### Fluxos Alternativos
- **A1 — Venda não encontrada:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- Sistema deve permitir cancelamento.

### RNF Relacionados
- Cancelamentos devem ser registrados.

### RN Relacionadas
- Apenas administradores podem cancelar vendas.

---------------------------------------------------------------------------
---------------------------------------------------------------------------
##UC13 – Gerar relatório
### Ator Principal
Administrador

### Objetivo
Permitir que o administrador gere relatório sobre o que ppertence ao sistema.

### Pré-condições
- Dados cadastrados.

### Pós-condições
- Relatório exibido.

### Fluxo Principal
1. Administrador seleciona relatório.
2. Escolhe período.
3. Sistema gera relatório.

### Fluxos Alternativos
- **A1 — Sem dados no período:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- Sistema deve gerar relatórios.

### RNF Relacionados
- Relatórios devem ser gerados rapidamente.

### RN Relacionadas
- Apenas administradores acessam relatórios.

---------------------------------------------------------------------------
---------------------------------------------------------------------------
##UC14 – Atualizar perfil
### Ator Principal
Usuário

### Objetivo
Atualizar o seu próprio perfil.

### Pré-condições
- Usuário cadastrado.

### Pós-condições
- Perfil atualizado com sucesso.

### Fluxo Principal
1. Usuário acessa perfil.
2. Altera informações.
3. Sistema salva.

### Fluxos Alternativos
- **A1 — Dados inválidos:**  
  O sistema exibe mensagem de erro.
  
### RF Relacionados
- Sistema deve permitir atualização de perfil.

### RNF Relacionados
- Alterações devem ser salvas imediatamente.

### RN Relacionadas
- Usuário só pode editar seu próprio perfil.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

UC15 – Recuperar senha
### Ator Principal
Usuário

### Objetivo
Conseguir recuperar e alterar senha.

### Pré-condições
- Usuário cadastrado.

### Pós-condições
- Altera senha.

### Fluxo Principal
1. Usuário clica em recuperar senha.
2. Informa email.
3. Sistema envia link de redefinição.

### Fluxos Alternativos
- **A1 — Email não encontrado:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- Sistema deve permitir recuperação de senha.

### RNF Relacionados
- O envio do email deve ser rápido.

### RN Relacionadas
- Link de recuperação expira em 24h.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC16 – Registrar pagamento

### Ator Principal
Funcionário.

### Objetivo
Permitir que o funcionário registre o pagamento.

### Pré-condições
- Venda registrada.

### Pós-condições
- Pagamento válido.

### Fluxo Principal
1. Funcionário seleciona venda.
2. Informa forma de pagamento.
3. Sistema registra pagamento.

### Fluxos Alternativos
- **A1 — Pagamento recusado:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- Sistema deve registrar pagamentos.

### RNF Relacionados
- Operação deve ser segura.

### RN Relacionadas
- Pagamento deve corresponder ao valor da venda.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC17 – Emitir nota fiscal

### Ator Principal
Sistema

### Objetivo
Exibir dados das compras.

### Pré-condições
- Venda e pagamento registrados.

### Pós-condições
- Nota fiscal emitida.

### Fluxo Principal
1. Sistema gera nota fiscal.
2. Sistema registra documento.
3. Sistema disponibiliza para impressão.

### Fluxos Alternativos
- **A1 — Erro na emissão:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- Sistema deve emitir nota fiscal.

### RNF Relacionados
- Documento deve ser gerado rapidamente.

### RN Relacionadas
- Nota fiscal só é emitida após pagamento.

---------------------------------------------------------------------------
---------------------------------------------------------------------------

##UC18 – Visualizar histórico

### Ator Principal
Usuário

### Objetivo
Permitir que o usuário acesse o sistema e veja seu histórico.

### Pré-condições
- Usuário logado.

### Pós-condições
- Histórico exibido.

### Fluxo Principal
1. Usuário acessa histórico.
2. Sistema exibe registros.

### Fluxos Alternativos
- **A1 — Nenhum histórico encontrado:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- Sistema deve mostrar histórico.

### RNF Relacionados
- Consulta deve ser rápida.

### RN Relacionadas
- Usuário só vê seus próprios registros.

---------------------------------------------------------------------------
---------------------------------------------------------------------------
##UC19 – Cadastrar categoria

### Ator Principal
Administrador

### Objetivo
Permitir que o usuário acesse o sistema.

### Pré-condições
- Administrador logado.

### Pós-condições
- Categoria cadastrada.    

### Fluxo Principal
1. Administrador acessa cadastro de categoria.
2. Insere nome da categoria.
3. Sistema salva.

### Fluxos Alternativos
- **A1 — Categoria já existente:**  

### RF Relacionados
- Sistema deve permitir cadastro de categorias.

### RNF Relacionados
- Dados devem ser armazenados com segurança.

### RN Relacionadas
- Nome da categoria deve ser único.

---------------------------------------------------------------------------
---------------------------------------------------------------------------
##UC20 – Gerenciar estoque

### Ator Principal
Administrador

### Objetivo
Administrar o estoque.

### Pré-condições
- Produtos cadastrados.

### Pós-condições
- Estoque atualizado

### Fluxo Principal
1. Administrador acessa estoque.
2. Seleciona produto.
3. Atualiza quantidade.
4. Sistema salva alterações.

### Fluxos Alternativos
- **A1 — Quantidade inválida:**  
  O sistema exibe mensagem de erro.

### RF Relacionados
- Sistema deve permitir controle de estoque.

### RNF Relacionados
- Atualizações devem ocorrer em tempo real.

### RN Relacionadas
- O estoque não pode ser negativo.

---------------------------------------------------------------------------
---------------------------------------------------------------------------
