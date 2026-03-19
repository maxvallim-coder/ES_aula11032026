# Sistema de Gestão de Vendas - Documentação e Diagramas

## 1. Diagrama de Casos de Uso

````plantuml
@startuml
left to right direction
skinparam packageStyle rectangle

actor "Administrador" as admin
actor "Usuário" as user
actor "Funcionário" as func
actor "Sistema\n<<Automático>>" as sys

func -up-|> user

rectangle "Sistema de Gestão de Vendas" {
  usecase "UC03: Cadastrar usuário" as uc03
  usecase "UC04: Editar usuário" as uc04
  usecase "UC05: Excluir usuário" as uc05
  usecase "UC06: Consultar usuário" as uc06
  usecase "UC07: Cadastrar produto" as uc07
  usecase "UC08: Editar produto" as uc08
  usecase "UC09: Excluir produto" as uc09
  usecase "UC12: Cancelar venda" as uc12
  usecase "UC13: Gerar relatório" as uc13
  usecase "UC19: Cadastrar categoria" as uc19
  usecase "UC20: Gerenciar estoque" as uc20

  usecase "UC14: Atualizar perfil" as uc14
  usecase "UC15: Recuperar senha" as uc15
  usecase "UC18: Visualizar histórico" as uc18
  usecase "UC01: Fazer login" as uc01
  usecase "UC02: Fazer logout" as uc02
  usecase "UC10: Consultar produto" as uc10

  usecase "UC11: Registrar venda" as uc11
  usecase "UC16: Registrar pagamento" as uc16

  usecase "UC17: Emitir nota fiscal" as uc17
}

admin --> uc03
admin --> uc04
admin --> uc05
admin --> uc06
admin --> uc07
admin --> uc08
admin --> uc09
admin --> uc12
admin --> uc13
admin --> uc19
admin --> uc20

user --> uc14
user --> uc15
user --> uc18
user --> uc01
user --> uc02
user --> uc10

func --> uc11
func --> uc16

uc17 <-- sys
@enduml
````

==================================================================

## UC01 — Realizar Login
# Ator Principal
Usuário

# Objetivo
Permitir que o usuário acesse o sistema.

# Pré-condições
Usuário deve possuir cadastro ativo.

# Pós-condições
Sessão iniciada com sucesso.

# Fluxo Principal
O usuário informa e-mail e senha.

O sistema valida as credenciais.

O sistema autentica o usuário e redireciona para a tela inicial.

# Fluxos Alternativos
A1 — Senha incorreta: O sistema exibe mensagem de erro.

A2 — Conta bloqueada: O sistema impede o login e instrui o usuário a recuperar o acesso.

# RF Relacionados
O sistema deve permitir autenticação de usuários.

# RNF Relacionados
O login deve ser realizado em até 2 segundos.

# RN Relacionadas
O usuário pode errar a senha no máximo 5 vezes.

````plantuml
@startuml
start
:Usuário informa e-mail e senha;
:Sistema valida credenciais;
if (Credenciais válidas?) then (Sim)
  if (Conta bloqueada?) then (Não)
    :Sistema autentica usuário;
    :Redireciona para tela inicial;
  else (Sim - Fluxo A2)
    :Impede login e instrui recuperação;
  endif
else (Não - Fluxo A1)
  :Exibe mensagem de erro;
endif
stop
@enduml
````
==================================================================

## UC02 — Fazer Logout
# Ator Principal
Usuário

# Objetivo
Permitir que o usuário encerre a sessão.

# Pré-condições
Usuário deve estar logado.

# Pós-condições
A sessão será encerrada.

# Fluxo Principal
O usuário seleciona a opção logout.

O sistema encerra a sessão.

O sistema redireciona o usuário para a tela inicial.

# Fluxos Alternativos
Nenhum.

# RF Relacionados
O sistema deve permitir que o usuário encerre a sessão.

# RNF Relacionados
O logout deve ser realizado imediatamente.

# RN Relacionadas
Após logout, o usuário deve realizar login novamente para acessar o sistema.
````plantuml
@startuml
start
:Usuário seleciona logout;
:Sistema encerra sessão;
:Sistema redireciona para tela inicial;
stop
@enduml
````
==================================================================

## UC03 — Cadastrar usuário
# Ator Principal
Administrador

# Objetivo
Permitir que o administrador cadastre um novo usuário.

# Pré-condições
O administrador deve estar logado no sistema.

# Pós-condições
Um novo usuário será registrado no sistema.

# Fluxo Principal
O administrador acessa a tela de cadastro.

O administrador adiciona os dados do usuário.

O sistema valida as informações.

O sistema salva o usuário no banco de dados.

# Fluxos Alternativos
A1 — Dados inválidos: O sistema exibe mensagem de erro e o administrador corrige os dados.

# RF Relacionados
O sistema deve permitir cadastro de usuários.

# RNF Relacionados
O sistema deve armazenar os dados com segurança.

# RN Relacionadas
Cada usuário deve possuir um e-mail único.
````plantuml
@startuml
start
:Administrador acessa tela de cadastro;
repeat
  :Administrador insere dados;
  :Sistema valida informações;
  if (Dados válidos e e-mail único?) then (Sim)
    :Sistema salva usuário;
    break
  else (Não - Fluxo A1)
    :Exibe mensagem de erro;
  endif
repeat while (Administrador corrige dados)
stop
@enduml
````
==================================================================

## UC04 — Editar usuário
# Ator Principal
Administrador

# Objetivo
Permitir que o administrador altere dados dos usuários.

# Pré-condições
O administrador logado e o usuário alvo deve existir no sistema.

# Pós-condições
Os dados do usuário serão atualizados.

# Fluxo Principal
O administrador busca o usuário.

O administrador seleciona a opção editar.

O administrador altera os dados.

O sistema valida e salva as alterações.

# Fluxos Alternativos
A1 — Dados inválidos: O sistema exibe mensagem de erro e o administrador corrige os dados.

# RF Relacionados
O sistema deve permitir edição de usuários.

# RNF Relacionados
As alterações devem ser registradas em log no sistema.

# RN Relacionadas
Apenas administradores podem editar outros usuários.
````plantuml
@startuml
start
:Administrador busca usuário;
:Seleciona editar;
repeat
  :Altera dados;
  :Sistema valida;
  if (Dados válidos?) then (Sim)
    :Sistema salva alterações;
    break
  else (Não - Fluxo A1)
    :Exibe mensagem de erro;
  endif
repeat while (Corrige dados)
stop
@enduml
````
==================================================================

## UC05 — Excluir usuário
# Ator Principal
Administrador

# Objetivo
Permitir que o administrador exclua usuários.

# Pré-condições
O administrador logado e o usuário alvo deve existir.

# Pós-condições
O usuário será excluído do sistema.

# Fluxo Principal
O administrador localiza o usuário.

O administrador seleciona excluir.

O sistema solicita confirmação.

O administrador confirma.

O sistema remove o usuário.

# Fluxos Alternativos
A1 — Cancelamento: O administrador cancela a operação na tela de confirmação.

# RF Relacionados
O sistema deve permitir exclusão de usuários.

# RNF Relacionados
A exclusão deve ser registrada em log.

# RN Relacionadas
Apenas administradores podem excluir usuários.
````plantuml
@startuml
start
:Administrador localiza usuário;
:Seleciona excluir;
:Sistema solicita confirmação;
if (Administrador confirma?) then (Sim)
  :Sistema remove usuário;
else (Não - Fluxo A1)
  :Cancela operação;
endif
stop
@enduml
````
==================================================================

## UC06 — Consultar usuário
# Ator Principal
Administrador

# Objetivo
Permitir que o administrador encontre o usuário no sistema.

# Pré-condições
Administrador logado e usuários cadastrados.

# Pós-condições
As informações do usuário serão exibidas.

# Fluxo Principal
O administrador acessa a tela de consulta.

O administrador digita o nome ou e-mail.

O sistema exibe os resultados.

# Fluxos Alternativos
A1 — Usuário não encontrado: O sistema informa que não há resultados.

# RF Relacionados
O sistema deve permitir busca de usuários.

# RNF Relacionados
A busca deve ocorrer em até 2 segundos.

# RN Relacionadas
Apenas administradores podem visualizar a lista completa de usuários.
````plantuml
@startuml
start
:Administrador acessa consulta;
:Digita nome ou e-mail;
:Sistema processa busca;
if (Encontrou usuário?) then (Sim)
  :Exibe resultados;
else (Não - Fluxo A1)
  :Informa que não há resultados;
endif
stop
@enduml
````
================================================================

## UC07 — Cadastrar produto
# Ator Principal
Administrador

# Objetivo
Permitir que o administrador cadastre um produto.

# Pré-condições
O administrador deve estar logado.

# Pós-condições
O produto será registrado no sistema.

# Fluxo Principal
O administrador acessa cadastro de produto.

O administrador insere dados do produto.

O sistema valida as informações.

O sistema salva o produto.

# Fluxos Alternativos
A1 — Dados inválidos ou código duplicado: O sistema exibe mensagem de erro.

# RF Relacionados
O sistema deve permitir cadastro de produtos.

# RNF Relacionados
Os dados devem ser armazenados de forma segura.

# RN Relacionadas
Cada produto deve possuir código único.

````plantuml
@startuml
start
:Acessa cadastro de produto;
:Insere dados do produto;
:Sistema valida (incluindo código único);
if (Válido?) then (Sim)
  :Salva produto;
else (Não - Fluxo A1)
  :Exibe erro;
endif
stop
@enduml
````
==================================================================

## UC08 — Editar produto
# Ator Principal
Administrador

# Objetivo
Permitir que o administrador altere dados do produto.

# Pré-condições
Produto deve existir.

# Pós-condições
Dados do produto atualizados.

# Fluxo Principal
O administrador busca produto.

Seleciona editar.

Altera informações.

Sistema salva alterações.

# Fluxos Alternativos
A1 — Erro nos dados: O sistema exibe mensagem de erro.

# RF Relacionados
O sistema deve permitir edição de produtos.

# RNF Relacionados
Alterações devem ser registradas.

# RN Relacionadas
Apenas administradores podem editar produtos.
````plantuml
@startuml
start
:Busca produto;
:Seleciona editar;
:Altera informações;
if (Dados corretos?) then (Sim)
  :Salva alterações;
else (Não - Fluxo A1)
  :Exibe erro;
endif
stop
@enduml
````
==================================================================

## UC09 — Excluir produto
# Ator Principal
Administrador

# Objetivo
Permitir a exclusão de um produto.

# Pré-condições
Produto cadastrado.

# Pós-condições
Produto removido do sistema.

# Fluxo Principal
Administrador seleciona produto.

Clica em excluir.

Confirma exclusão.

Sistema remove produto.

# Fluxos Alternativos
A1 — Cancelamento: Administrador não confirma a exclusão.

A2 — Produto possui vendas: Sistema bloqueia a exclusão e exibe erro.

# RF Relacionados
O sistema deve permitir exclusão de produtos.

# RNF Relacionados
Exclusões devem ser registradas.

# RN Relacionadas
Produtos com vendas registradas não podem ser excluídos.
````plantuml
@startuml
start
:Seleciona produto;
:Clica em excluir;
if (Possui vendas registradas?) then (Sim - Fluxo A2)
  :Bloqueia exclusão e exibe erro;
else (Não)
  :Solicita confirmação;
  if (Confirma?) then (Sim)
    :Remove produto;
  else (Não - Fluxo A1)
    :Cancela exclusão;
  endif
endif
stop
@enduml
````
==================================================================

## UC10 — Consultar produto
# Ator Principal
Usuário

# Objetivo
Encontrar produtos dentro do sistema.

# Pré-condições
Produto cadastrado e ativo.

# Pós-condições
Exibir lista de produtos.

# Fluxo Principal
Usuário acessa tela de produtos.

O sistema exibe a listagem de produtos ativos.

Fluxos Alternativos
A1 — Nenhum produto encontrado: O sistema exibe mensagem informativa.

# RF Relacionados
O sistema deve permitir consulta de produtos.

# RNF Relacionados
Consulta deve ocorrer rapidamente.

# RN Relacionadas
Apenas produtos ativos devem ser exibidos.
````plantuml
@startuml
start
:Usuário acessa tela de produtos;
:Sistema busca produtos ativos;
if (Existem produtos?) then (Sim)
  :Exibe listagem;
else (Não - Fluxo A1)
  :Exibe mensagem informativa;
endif
stop
@enduml
````
==================================================================

## UC11 — Registrar venda
# Ator Principal
Funcionário

# Objetivo
Registrar uma nova venda no sistema.

# Pré-condições
Produtos cadastrados e com estoque.

# Pós-condições
Venda registrada.

# Fluxo Principal
Funcionário seleciona produto.

Informa quantidade.

Sistema calcula valor.

Sistema registra venda e abate do estoque.

# Fluxos Alternativos
A1 — Produto sem estoque: O sistema impede o registro e exibe mensagem de falta de estoque.

# RF Relacionados
O sistema deve registrar vendas.

# RNF Relacionados
Operação deve ser rápida.

# RN Relacionadas
Venda só ocorre se houver estoque suficiente.
````plantuml
@startuml
start
:Seleciona produto;
:Informa quantidade;
if (Estoque suficiente?) then (Sim)
  :Calcula valor;
  :Registra venda e atualiza estoque;
else (Não - Fluxo A1)
  :Impede registro e exibe erro de estoque;
endif
stop
@enduml
````
==================================================================

## UC12 — Cancelar venda
# Ator Principal
Administrador

# Objetivo
Realizar o cancelamento de uma venda.

# Pré-condições
Venda registrada.

# Pós-condições
Venda cancelada e estoque retornado.

# Fluxo Principal
Administrador localiza venda.

Seleciona cancelar.

Sistema cancela registro.

# Fluxos Alternativos
A1 — Venda não encontrada: O sistema exibe mensagem de erro.

# RF Relacionados
Sistema deve permitir cancelamento de vendas.

# RNF Relacionados
Cancelamentos devem ser registrados.

# RN Relacionadas
Apenas administradores podem cancelar vendas.
````plantuml
@startuml
start
:Administrador busca venda;
if (Venda encontrada?) then (Sim)
  :Seleciona cancelar;
  :Sistema cancela registro e estorna estoque;
else (Não - Fluxo A1)
  :Exibe mensagem de erro;
endif
stop
@enduml
````
==================================================================

## UC13 — Gerar relatório
# Ator Principal
Administrador

# Objetivo
Permitir que o administrador gere relatórios do sistema.

# Pré-condições
Dados cadastrados no período selecionado.

# Pós-condições
Relatório gerado e exibido.

# Fluxo Principal
Administrador seleciona o tipo de relatório.

Escolhe o período.

Sistema gera e exibe relatório.

# Fluxos Alternativos
A1 — Sem dados no período: O sistema exibe mensagem informando que não há registros.

# RF Relacionados
Sistema deve gerar relatórios.

# RNF Relacionados
Relatórios devem ser gerados rapidamente.

# RN Relacionadas
Apenas administradores acessam o módulo de relatórios.
````plantuml
@startuml
start
:Seleciona tipo de relatório;
:Escolhe período;
:Sistema busca dados;
if (Dados existem?) then (Sim)
  :Gera e exibe relatório;
else (Não - Fluxo A1)
  :Exibe aviso de ausência de dados;
endif
stop
@enduml
````
==================================================================

## UC14 — Atualizar perfil
# Ator Principal
Usuário

# Objetivo
Atualizar o seu próprio perfil.

# Pré-condições
Usuário logado.

# Pós-condições
Perfil atualizado com sucesso.

# Fluxo Principal
Usuário acessa o perfil.

Altera informações desejadas.

Sistema salva as alterações.

# Fluxos Alternativos
A1 — Dados inválidos: O sistema exibe mensagem de erro.

# RF Relacionados
Sistema deve permitir atualização de perfil.

# RNF Relacionados
Alterações devem ser salvas imediatamente.

# RN Relacionadas
Usuário só pode editar seu próprio perfil.
````plantuml
@startuml
start
:Acessa perfil;
:Altera informações;
:Sistema valida;
if (Válido?) then (Sim)
  :Salva perfil;
else (Não - Fluxo A1)
  :Exibe erro;
endif
stop
@enduml
````
==================================================================

## UC15 — Recuperar senha
# Ator Principal
Usuário

# Objetivo
Conseguir recuperar e alterar a senha de acesso.

# Pré-condições
Usuário previamente cadastrado.

# Pós-condições
Senha alterada (se o fluxo for concluído).

# Fluxo Principal
Usuário clica em recuperar senha.

Informa e-mail cadastrado.

Sistema envia link de redefinição para o e-mail.

# Fluxos Alternativos
A1 — E-mail não encontrado: O sistema exibe mensagem de erro.

# RF Relacionados
Sistema deve permitir recuperação de senha.

# RNF Relacionados
O envio do e-mail deve ser rápido.

# RN Relacionadas
O link de recuperação expira em 24h.
````plantuml
@startuml
start
:Clica em recuperar senha;
:Informa e-mail;
:Sistema verifica e-mail;
if (E-mail existe?) then (Sim)
  :Envia link de redefinição;
else (Não - Fluxo A1)
  :Exibe erro;
endif
stop
@enduml
````
==================================================================

## UC16 — Registrar pagamento
# Ator Principal
Funcionário

# Objetivo
Permitir que o funcionário registre o pagamento de uma venda.

# Pré-condições
Venda registrada no sistema.

# Pós-condições
Pagamento validado e registrado.

# Fluxo Principal
Funcionário seleciona a venda pendente.

Informa forma de pagamento e valor.

Sistema registra o pagamento.

# Fluxos Alternativos
A1 — Pagamento recusado/inválido: O sistema exibe mensagem de erro.

# RF Relacionados
Sistema deve registrar pagamentos.

# RNF Relacionados
Operação deve ser segura (integrações criptografadas).

# RN Relacionadas
Pagamento deve corresponder ao valor total da venda.
````plantuml
@startuml
start
:Seleciona venda;
:Informa forma de pagamento;
:Sistema processa pagamento;
if (Aprovado e valor correspondente?) then (Sim)
  :Registra pagamento;
else (Não - Fluxo A1)
  :Exibe mensagem de recusa/erro;
endif
stop
@enduml
````
==================================================================

## UC17 — Emitir nota fiscal
# Ator Principal
Sistema (Automático)

# Objetivo
Gerar e disponibilizar o documento fiscal da compra.

# Pré-condições
Venda e pagamento devidamente registrados.

# Pós-condições
Nota fiscal emitida.

# Fluxo Principal
Sistema detecta pagamento aprovado e gera nota fiscal.

Sistema registra o documento.

Sistema disponibiliza a NF para impressão/download.

# Fluxos Alternativos
A1 — Erro na comunicação com a SEFAZ (ou órgão emissor): O sistema retém a NF e tenta emitir novamente.

# RF Relacionados
Sistema deve emitir nota fiscal.

# RNF Relacionados
Documento deve ser gerado e assinado rapidamente.

# RN Relacionadas
A nota fiscal só é emitida após o registro do pagamento.
````plantuml
@startuml
start
:Detecta pagamento aprovado;
:Gera dados da NF;
:Envia para validação fiscal;
if (Validado?) then (Sim)
  :Registra e disponibiliza para impressão;
else (Não - Fluxo A1)
  :Retém e agenda retentativa;
endif
stop
@enduml
````
==================================================================

## UC18 — Visualizar histórico
# Ator Principal
Usuário

# Objetivo
Permitir que o usuário veja seu histórico de atividades ou compras.

# Pré-condições
Usuário logado.

# Pós-condições
Histórico exibido na tela.

# Fluxo Principal
Usuário acessa aba de histórico.

Sistema busca e exibe registros.

# Fluxos Alternativos
A1 — Nenhum histórico encontrado: O sistema exibe mensagem informativa ("Você ainda não possui histórico").

# RF Relacionados
Sistema deve mostrar histórico de movimentações/vendas.

# RNF Relacionados
Consulta deve ser rápida.

# RN Relacionadas
O usuário só pode ver seus próprios registros.
````plantuml
@startuml
start
:Acessa aba de histórico;
:Sistema busca registros do usuário;
if (Possui registros?) then (Sim)
  :Exibe lista;
else (Não - Fluxo A1)
  :Exibe mensagem informativa;
endif
stop
@enduml
````
==================================================================

## UC19 — Cadastrar categoria
# Ator Principal
Administrador

# Objetivo
Permitir a criação de categorias para agrupar produtos.

# Pré-condições
Administrador logado.

# Pós-condições
Categoria cadastrada e disponível.

# Fluxo Principal
Administrador acessa cadastro de categoria.

Insere nome da categoria.

Sistema valida e salva.

# Fluxos Alternativos
A1 — Categoria já existente: Sistema impede o cadastro e avisa o usuário.

# RF Relacionados
Sistema deve permitir cadastro de categorias de produtos.

# RNF Relacionados
Dados devem ser armazenados com segurança.

# RN Relacionadas
O nome da categoria deve ser único no sistema.
````plantuml
@startuml
start
:Acessa cadastro de categoria;
:Insere nome;
:Sistema verifica duplicidade;
if (Nome único?) then (Sim)
  :Salva categoria;
else (Não - Fluxo A1)
  :Impede cadastro e avisa duplicação;
endif
stop
@enduml
````
==================================================================

## UC20 — Gerenciar estoque
# Ator Principal
Administrador

# Objetivo
Administrar e corrigir a quantidade de itens no estoque.

# Pré-condições
Produtos previamente cadastrados.

# Pós-condições
Estoque atualizado.

# Fluxo Principal
Administrador acessa painel de estoque.

Seleciona o produto desejado.

Atualiza a quantidade (entrada/saída manual).

Sistema salva as alterações.

# Fluxos Alternativos
A1 — Quantidade inválida (ex: tentativa de deixar negativo): O sistema bloqueia a ação e exibe mensagem de erro.

# RF Relacionados
Sistema deve permitir controle e ajuste de estoque.

# RNF Relacionados
Atualizações devem ocorrer em tempo real.

# RN Relacionadas
O estoque nunca pode assumir valores negativos.
````plantuml
@startuml
start
:Acessa painel de estoque;
:Seleciona produto;
:Informa nova quantidade;
if (Quantidade >= 0?) then (Sim)
  :Salva alterações;
else (Não - Fluxo A1)
  :Bloqueia e exibe erro;
endif
stop
@enduml
````
