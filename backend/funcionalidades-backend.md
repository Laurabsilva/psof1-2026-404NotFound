A API do Back-End funciona como o "cérebro" da aplicação MedLife. Ela conecta as telas desenhadas no Figma com o banco de dados, garantindo que as informações só sejam salvas se seguirem todas as regras da clínica.
1. Login e Controle de Acesso
Rota: /login (Reflete as Telas 2 e 3 do Figma)
O que faz: Autentica o usuário e identifica se ele é paciente, médico ou a dona da clínica.
Regra de Negócio:
O Back-End faz um IF checando o perfil do usuário logado.
Se for a Dona, libera o acesso total ao sistema (telas administrativas, financeiras e médicas).
Se for Médico, o Back-End bloqueia a visão financeira e libera apenas o acesso ao histórico médico e prontuário dos pacientes.
2. Cadastro do Paciente
Rota: /cadastrarPaciente (Reflete as Telas 4 e 5 do Figma)
O que faz: Recebe as informações do formulário de cadastro.
Regra de Negócio:
Validação de Vacina: O Back-End faz um IF checando a opção de vacinação. Se estiver como "não vacinado", o cadastro é cancelado e o sistema exibe uma mensagem de bloqueio.
Validação de Convênio: O Back-End faz um IF para checar o convênio digitado. O cadastro só é aceito se for Unimed, SUS ou Samaritano. Qualquer outro convênio é rejeitado.
Se passar pelas duas verificações, a API salva os dados do paciente (incluindo as informações de aparência física e histórico).
3. Agendamento da Consulta
Rota: /agendarConsulta (Reflete as Telas 7, 8 e 9 do Figma)
O que faz: Registra a marcação de consultas online com o médico, data e horário escolhidos.
Regra de Negócio:
O Back-End faz um IF checando se a data e o horário selecionados estão livres na agenda do médico.
Se o horário estiver livre, a API grava a consulta e dispara uma notificação de confirmação para o paciente.
4. Pagamento e Confirmação
Rota: /pagarConsulta (Reflete as Telas 10 e 11 do Figma)
O que faz: Registra o pagamento e finaliza o agendamento da consulta.
Regra de Negócio:
O Back-End faz um IF para validar o pagamento realizado no site.
Se o pagamento for aprovado, ele salva a transação no banco de dados, altera o status da consulta para "Paga/Confirmada" e direciona para a tela de mensagem final.
