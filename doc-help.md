------------------------------------------------------------------------------------
PASSO A PASSO CHAMADOS CÓDIGO

----- Alterações no código -----

1 - Validar se não tem outro chamado com o mesmo proposito e da pra fazer em cima
2 - Caso tenha, mudar ele e testar com os arquivos de todos os chamados para ver se não quebrou o anterior
3 - Validar se a logica pega o arquivo de forma especifica e não vai pegar outros arquivos
4 - Validar logInfo, principal logInfo tem que ta separado
5 - Validar se não tem comentários errados
6 - Validar se não tem linhas em branco
7 - Validar se ta tudo identado
8 - Validar se ta comentado e documentado
9 - OLha sempre antes de commitar, olha as alterações do arquivo e ve se não alterou nada aleatório do código.
10 - Criar branch seguindo o padrão (chore, fix, feat, hotfix)/tag-jira/o que-foi-feito
feat - Nova coisa criada que não tinha nada antes, um novo serviço
chore - Nova coisa mais já tinha algo, exemplo uma nova tratativa que não tinha
fix - Bug básicamente, algo que quebrou o sistema, pode na Dev (pode acontecer na produ mas não afeta ninguem)
hotfix - Algo urgente que quebrou no cliente
11 - git add .
12 - git commit -m "exemplo" 
13 - ir no git e concluir o PR, colocando o que foi perguntado na tela antes da dar o PR
14 - validar as alterações no git

----- Após o PR ser reprovado -----

15 - git checkout nomedabranch
16 - dá uma olhada pra ver se ta tudo certo, tente salvar pra evitar erros
17 - realizar alteração
18 - git add .
19 - git commit -m "exemplo" 
20 - validar as alterações no git

----- Após o PR ser aprovado -----

15 - Da o merge
16 - deleta a branch
17 - Faz o deploy no actions -> deploy scripts io_contabil
18 - Vai no jira e procura o chamado e a entra na tarefa
19 - Vai em informações principais em "Outros"
20 - Vai em detalhes da solução e adiciona esse texto mudando só o básico.

Problema: Pode ser algo que não funciona, ou algo novo, ou seja o cliente não ter a tratativa. Explicar o que tava dando pau
Origem do problema: 
Solução: Explicar o que foi feito para solucionar o problema, de forma simples

Problema: Cliente queria fazer um corte de data em um documento que já tinha tratativa e optamos por deixar o metodo global e arrumar a tratativa
Origem do problema: Interno, o sistema não tinha a tratativa
Solução: Alterado a tratativa para biblioteca para que possar reconhecer os documentos com mesmo layout de outras contabilidades e competencia esperada

15 - Move pra Done e coloca Resolução itens concluídos
16 - Vai no salesForce e procura o chamado
17 - Clica no chamado e vai em movimentos dos antendimentos
18 - clica no número do movimento
19 - Vai abrir o movimento e nele tu clica no primeiro botão de clonar
20 - Muda data do movimento para a data atual
21 - Coloca em teste de qualidade
21 - na descrição coloca o seu nome e data (Gustavo Alves - 04/03/2026)
22 - Deixa uma linha em branco e cola o texto que tu tinha colado do jira, no caso já atualizado
23 - valida se não está visível no Portal
23 - Clica em salvar  
24 - Terminado


------------------------------------------------------------------------------------
PASSO A PASSO CHAMADOS INOUT SERVER

1 - Vai no inout server
2 - Loga
3 - Vai em status e coloca todos
4 - Vai em nome e pesquisa tareffa e clica em atualizar
5 - Clica na rota Tareffa.ReprocessaBaixaServico
6 - Clica no Tareffa.ReprocessaBaixaServico do lado do raio e do verde de certinho
7 - Clica em origem e depois no botão que é um S
8 - Procura esse começo de query select ot_objeto_questor, ot_token_usuario from ottimizza_schema.log_questor lq where ot_created_at between 
9 - Copia a query
10 - Vai no chamado e pega os Log, aquela tripa de json
11 - Copia o campo Date até os segundos (fica embaixo do collection)
12 - muda a data da query que você copiou por esse
13 - altera a primeira data pra 4 horas a menos, e a segundo data por 4 horas a mais
14 - Procura o CNPJ e copia 
15 - Altera o CNPJ da query por esse copiado
16 - vai no inout, naquela tela onde tu copiou a query, e troca a query por esse que você alterou.
17 - Clica em salvar e depois fechar
18 - clica em voltar
19 - Clique no raio para executar
20 - Se tiver mais de um logm repita o processo até acabar o log
21 - Tire print de tudo que foi processado no inout, só os que você processou
22 - Vá no chamado e anexe os prints
23 - Responda o chamado assim:
(Nome Pessoa - Data Completa)

Olá, foi reprocessado os logs, segue print em anexo
24 - Feito

------------------------------------------------------------------------
MENSAGENS PADRÃO

----- Pedir alteração de uma view -----
Titulo chamado: Alteração da view escritorionaves_view_empresas_responsaveis

Bom dia, 
Gostaria de solicitar a alteração da view escritorionaves_view_empresas_responsaveis
BD: Ordem de Serviço (Tareffa)

*Anexo o código da view*

----- liberar uma view que o cliente não tem views Jarbas-----
Titulo chamado: Liberação da view Ellos

Bom dia,
Gostaria de solicitar a liberação da view para a contabilidade: Ellos.
OBS.: A contabilidade ainda não possui acesso a nenhuma views.
BD: Ordem de Serviço (Tareffa)

*Anexo o código da view*

----- liberar todas as views padrão para um cliente que não tem views Jarbas-----
Titulo chamado: Liberação das views padrões Ellos

Bom dia,
Gostaria de solicitar a liberação das views padrões para a contabilidade: Ellos.
OBS.: A contabilidade ainda não possui acesso a nenhuma views.
BD: Ordem de Serviço (Tareffa)

----- Pedir criação de um index novo -----
Titulo chamado: Criação do novo index para a tabela ot_mov_processo_atividades

Bom dia, 
Gostaria de solicitar a criação de um novo index, segue os dados abaixo.

Ambiente: PRD
API: api-ordemservicos
Banco: d5cjhu9om6udeu
Tabela: ot_mov_processo_atividades

* Criação de INDEX
Nome da Coluna      | Tipo de Dado | Collation | Não nulo |
fk_contabilidade_id | INTEGER (8)  |           | nullable |
fk_mov_processo_id  | INTEGER (8)  |           | nullable |
fk_atividade_id     | INTEGER (8)  |           | nullable |

Justificativa: Essa tabela só contém o index padrão que é o pelo ID, com esse index é possível pesquisar pelas principais fk da tabela o que otimiza em muitas querys, criei depois de uma view ficar muito pesada, onde depois da criação do index ela diminuiu 20x o custo. Já alinhado com o Airam a criação desse index.

----- responder chamado padrão -----
(Gustavo Alves - 17/03/2026)

Problema: Sistema estava reconhecendo outra competência e o cliente queria pegar como competência o valor Parcela 13/2025 e reconhecer como 11/2025
Origem do problema: Interno, o sistema não tinha a tratativa
Solução: Alterado a tratativa para biblioteca, para que possa reconhecer os documentos com mesmo layout de outras contabilidades

----- responder chamado log -----
(Gustavo Alves - 16/03/2026)

Olá, foi reprocessado os logs, segue print em anexo

----- responder chamado nem view -----
(Gustavo Alves - 17/03/2026)

Olá, foi criado e liberado a nova view conforme pedido pelo cliente. 

Nome da View: rioservicecontabilidade_view_processo_atividade_comentario
Schema para uso View: ottimizza_clientes
Tipo de View: ordemservico

----- responder chamado nem view padrões-----
(Gustavo Alves - 17/03/2026)

Olá, foi criado e liberado as views padrões, conforme pedido pelo cliente. 

Tipo de View: OrdemServicos
Usuário: usuario_view
Senha: senha_view
HOST: link_host
Banco: banco
Porta: 5432 
Schema para uso VIEW: ottimizza_clientes


------------------------------------------------------------------------
Link uteis

Chamados Jarbas: https://ottimizza.atlassian.net/servicedesk/customer/portal/1/group/6
meet aberto: https://meet.google.com/eyq-wphe-exj
daily: https://meet.google.com/wpm-pjdx-ayi
inout server: http://s1.ottimizza.com.br:8055/inout/
inout local: http://localhost:8055/inout/
github io_contabil: https://github.com/Tareffa/Tareffa-io_contabil
jira tareffa: https://ottimizza.atlassian.net/jira/software/c/projects/TAR/boards/6


