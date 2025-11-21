# Relatório de Consultas e Análise de Resultados

O sistema conta com 5 relatórios gerenciais principais desenvolvidos em SQL. Abaixo, a análise do que cada um entrega:

### 1. Relatório de Internações Ativas
* **Objetivo:** Listar pacientes que estão ocupando leitos no momento.
* **Análise:** Filtra apenas os registros onde a data de alta é nula (`NULL`), permitindo à gestão saber exatamente quem está internado em tempo real.

### 2. Taxa de Ocupação Hospitalar
* **Objetivo:** Medir a eficiência do uso dos leitos por setor.
* **Análise:** Calcula a porcentagem de leitos ocupados versus o total disponível. É crucial para identificar superlotação na Emergência ou ociosidade na Internação.

### 3. Faturamento por Atendimento
* **Objetivo:** Calcular o custo total da passagem do paciente pelo hospital.
* **Análise:** Soma (`SUM`) todos os itens (exames, consultas, diárias) vinculados a um registro de atendimento, gerando a conta final para cobrança do convênio.

### 4. Produtividade do Corpo Clínico
* **Objetivo:** Monitorar quantos atendimentos cada médico realizou.
* **Análise:** Agrupa os atendimentos pelo ID do profissional, permitindo identificar os médicos mais ativos e as especialidades com maior demanda.