A API do Back-End é o "cérebro" do site da clínica Med Life. Ela recebe as informações enviadas pelas telas, faz as validações exigidas e salva ou busca tudo no banco de dados.
Funcionalidades e Regras de Negócio do Back-End
Rota: /cadastrarPaciente
Recebe as informações do formulário de cadastro do paciente.
Regra de Negócio: O Back-End faz um IF checando se o paciente é vacinado. Se não for, bloqueia e retorna erro. Depois, faz outro IF verificando se o convênio é Unimed, SUS ou Samaritano. Se for outro convênio, bloqueia e retorna erro. Se passar nas duas verificações, salva o cadastro e a foto/aparência do paciente no banco.
Rota: /agendarConsulta
Recebe o pedido de agendamento de consulta online.
Regra de Negócio: O Back-End salva o agendamento no banco e aciona o sistema para enviar uma notificação de confirmação da consulta para o paciente.
Rota: /consultarHistorico
Busca o histórico médico e prontuário dos pacientes.
Regra de Negócio: O Back-End faz um IF verificando o tipo de usuário. Se for "Médico" ou "Dona", libera o acesso às informações médicas. Se for outro perfil, retorna erro de acesso negado (403).
Rota: /acessoTotal
Libera todas as funções administrativas e financeiras do sistema.
Regra de Negócio: O Back-End faz um IF verificando o usuário logado. Se for a "Dona", libera o sistema completo. Se for um "Médico" ou qualquer outro usuário, retorna erro de acesso negado.
Rota: /pagarConsulta
Recebe a confirmação de pagamento da consulta no site.
Regra de Negócio: O Back-End valida se o pagamento foi concluído, registra a transação financeira no banco de dados e muda o status da consulta para "Paga".
