# Problemas Encontrados e Soluções Adotadas

Durante o desenvolvimento do sistema hospitalar, encontramos desafios técnicos que foram solucionados via PL/SQL (Procedures e Triggers).

### Problema 1: Controle de Ocupação de Leitos
**Situação:** Havia o risco de um paciente ser internado em um leito que já estava ocupado, ou o sistema não atualizar o status do leito após a alta.
**Solução:** Implementação da Trigger `TRG_GERENCIA_STATUS_LEITO`.
* **Funcionamento:** O sistema monitora a tabela de admissão. Ao inserir uma internação, ele muda o status do leito para 'OCUPADO'. Ao atualizar a data de alta, ele libera o leito para 'LIVRE' automaticamente.

### Problema 2: Inconsistência Financeira
**Situação:** O lançamento manual de preços na conta do paciente gerava erros frequentes (digitação incorreta de valores).
**Solução:** Criação da Procedure `PRC_LANCAR_ITEM_CONTA`.
* **Funcionamento:** O usuário informa apenas o código do serviço. A procedure busca o preço correto na tabela `CATALOGO_SERVICO` e grava o registro, eliminando o erro humano.

### Problema 3: Limpeza de Ambiente
**Situação:** Ao reiniciar os testes, a ordem de exclusão das tabelas gerava erros de chave estrangeira.
**Solução:** Criação de um script de limpeza que utiliza `DROP TABLE ... CASCADE CONSTRAINTS`, permitindo zerar o banco sem se preocupar com a ordem das dependências.