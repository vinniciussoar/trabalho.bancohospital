# Justificativas e Decisões Técnicas do Projeto

## 1. Escolha do Modelo de Dados
O banco de dados foi modelado seguindo as formas normais (3FN) para evitar redundância de dados e garantir a integridade das informações.

* **Separação de Entidades:** Criamos tabelas separadas para `BENEFICIARIO`, `CORPO_CLINICO` e `UNIDADE_HOSPITALAR` para que as informações cadastrais não se misturem com os atendimentos.
* **Tabela Associativa:** A tabela `ITENS_ATENDIMENTO` foi criada para permitir que um único atendimento tenha vários serviços (ex: uma consulta e dois exames) sem duplicar linhas na tabela principal.

## 2. Tipos de Dados
* **NUMBER/IDENTITY:** Utilizamos chaves primárias autoincrementais (`GENERATED ALWAYS AS IDENTITY`) para facilitar a gestão de IDs e evitar erros manuais na inserção.
* **DATE:** Utilizamos o tipo `DATE` padrão do Oracle para garantir que cálculos de tempo (como dias de internação) sejam precisos.

## 3. Integridade Referencial
Todas as tabelas estão amarradas por *Foreign Keys* (Chaves Estrangeiras). Isso impede, por exemplo, que um atendimento seja registrado para um médico que não existe, garantindo a consistência do sistema.