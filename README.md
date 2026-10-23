
# HACKATHON 2026

*Organização Colaborativa de Projetos e Tarefas.*

Um sistema web para organizar projetos, gerenciar tarefas e acompanhar atividades individuais e em grupo. A aplicação contará com um quadro Kanban, controle de prioridades, notificações de vencimento, calendário e integração planejada com o Google Drive.

Equipe:

- [Bianca Isadora Joselli de Souza](https://github.com/BiancaJoselli)
- [Giovana Rosa](https://github.com/giovana-rosa)
- [Helena Soares Pereira](https://github.com/helenasoaresp)
- [Rafael August Otto](https://github.com/rafael-otto)
- [Thayná de Oliveira Becker](https://github.com/thaynabecker)

Links do projeto:

- Documentação: [Repositório](https://github.com/Hackathon-IFC-2026/documentacao)
- Backend: [Repositório](https://github.com/Hackathon-IFC-2026/backend) e [Publicação](https://backend-mknu.onrender.com)
- Frontend: [Repositório](https://github.com/Hackathon-IFC-2026/frontend) e [Publicação](https://frontendhackathon2026.vercel.app/)
- Figma: [Prototipagem](https://www.figma.com/design/0XiZumK2970i3Sq4aWXkb3/Hackathon-2026?m=auto&t=PvgcgpD17W1eLANo-6)
- Documento: [Anotações internas da equipe](https://docs.google.com/document/d/19xeWs5Gohuo6uG9HJgv1I0vq9AvRGCQZCKXD2qN7AdI/edit?usp=sharing)
- Modelagem do banco: [Arquivo MySQL Workbench](arquivo%20modelagem/19.10.mwb)

# 1. Situação Problema

A organização de projetos e tarefas é fundamental para o cumprimento de prazos e para a distribuição eficiente das responsabilidades entre os integrantes de uma equipe. Em ambientes acadêmicos e profissionais, diversas atividades precisam ser planejadas, atribuídas a responsáveis e acompanhadas durante sua execução.

Entretanto, quando as informações ficam distribuídas entre anotações, mensagens, planilhas e documentos separados, torna-se mais difícil acompanhar o andamento das atividades. Essa falta de centralização pode ocasionar atrasos, falhas de comunicação, dificuldade na identificação de prioridades e dúvidas sobre os responsáveis por cada tarefa.

Outro problema está relacionado ao acompanhamento dos prazos. Sem notificações automáticas, os integrantes podem esquecer datas importantes ou perceber que uma atividade está atrasada somente depois do vencimento. Além disso, documentos relacionados aos projetos podem ficar dispersos em diferentes pastas e serviços, dificultando sua localização.

Diante dessa situação, identifica-se a necessidade de um sistema que centralize projetos, tarefas, responsáveis, prioridades, prazos e documentos. Uma aplicação web com recursos de colaboração e acompanhamento visual pode facilitar o planejamento, melhorar a comunicação e contribuir para o cumprimento dos prazos.

# 2. Descrição da proposta

O projeto consiste no desenvolvimento de um sistema web para organização colaborativa de projetos e tarefas. Seu principal objetivo é permitir que usuários planejem atividades, distribuam responsabilidades e acompanhem o progresso dos projetos em um ambiente centralizado.

O sistema será destinado a estudantes, equipes de trabalho e grupos que precisam organizar atividades individuais ou colaborativas.

A aplicação permitirá cadastrar usuários, criar projetos, adicionar participantes e registrar tarefas com título, descrição, responsável, prazo, prioridade e tipo. As tarefas serão organizadas em um quadro Kanban com três situações: "A fazer", "Em andamento" e "Concluído".

As prioridades serão classificadas em três níveis:

- Baixa: identificada pela cor amarela.
- Média: identificada pela cor laranja.
- Alta: identificada pela cor vermelha.

Também será possível classificar as tarefas como "Individual" ou "Em grupo", consultar as atividades atribuídas ao usuário na seção "Minhas tarefas" e utilizar filtros para localizar tarefas específicas.

O sistema deverá disponibilizar um calendário para visualizar os prazos das atividades e notificações para alertar os responsáveis um dia antes do vencimento de tarefas ainda não concluídas.

Como diferencial, o projeto prevê integração com o Google Drive para facilitar a associação e o acesso a documentos relacionados aos projetos. Também está prevista a possibilidade de integração com o Google Calendar para sincronizar os prazos das atividades com a agenda dos usuários.

O acesso às informações deverá respeitar as permissões de cada usuário, garantindo que somente pessoas autorizadas possam consultar ou modificar os dados dos projetos.

# 3. Modelagem de Dados

O sistema utilizará um banco de dados relacional desenvolvido em MySQL para gerenciar usuários, projetos, participantes, tarefas, comentários, documentos e notificações.

A modelagem será realizada no MySQL Workbench, utilizando chaves primárias e estrangeiras para garantir a integridade e a consistência dos dados.

![Diagrama de Entidade-Relacionamento](arquivo%20modelagem/19.10.png)

## 3.1. Descrição das Entidades

- **Usuários:** armazena os dados das contas cadastradas, como nome, e-mail, senha protegida e data de cadastro.
- **Projetos:** armazena o nome, a descrição, o criador e a data de criação dos projetos.
- **Participantes do Projeto:** relaciona usuários aos projetos dos quais participam.
- **Tarefas:** armazena título, descrição, situação, prioridade, tipo, prazo e responsável.
- **Checklists:** armazena os itens de verificação associados às tarefas.
- **Comentários:** armazena o conteúdo, o autor e a data dos comentários.
- **Anexos:** armazena links e informações de documentos associados aos projetos ou às tarefas.
- **Notificações:** armazena avisos destinados aos usuários, incluindo data de criação e estado de leitura.
- **Integrações:** poderá registrar as conexões autorizadas com serviços externos.

## 3.2. Relacionamentos e Tabelas Associativas

Para resolver os relacionamentos de Muitos-para-Muitos (N:N), serão utilizadas tabelas associativas.

- **Participantes do Projeto:** relaciona usuários e projetos. Um usuário pode participar de vários projetos, e um projeto pode possuir vários participantes.
- **Participantes da Tarefa (opcional):** relaciona usuários e tarefas, caso uma tarefa possa ter vários responsáveis.

Os principais relacionamentos previstos são:

- Um usuário pode criar vários projetos.
- Um projeto pode possuir várias tarefas.
- Um projeto pode possuir vários participantes.
- Uma tarefa pode possuir vários itens de checklist.
- Uma tarefa pode possuir vários comentários.
- Uma tarefa ou projeto pode possuir vários anexos.
- Um usuário pode receber várias notificações.
- Um usuário pode ser responsável por várias tarefas.

# 4. Requisitos Funcionais e Regras de Negócio

# 4. Requisitos Funcionais e Regras de Negócio

## 4.1. Requisitos Funcionais (RF)

- **RF001 -** o sistema deve manter os usuários cadastrados.
- **RF002 -** o sistema deve permitir que os usuários realizem login e logout.
- **RF003 -** o sistema deve manter os projetos cadastrados.
- **RF004 -** o sistema deve manter os participantes vinculados aos projetos.
- **RF005 -** o sistema deve manter as tarefas vinculadas aos projetos.
- **RF006 -** o sistema deve manter os responsáveis pelas tarefas.
- **RF007 -** o sistema deve organizar as tarefas nas colunas "A fazer", "Em andamento" e "Concluído".
- **RF008 -** o sistema deve permitir selecionar as prioridades das tarefas, classificadas como Baixa, Média ou Alta.
- **RF009 -** o sistema deve permitir a classificação das tarefas como "Individual" ou "Em grupo".
- **RF010 -** o sistema deve apresentar as tarefas atribuídas ao usuário autenticado.
- **RF011 -** o sistema deve permitir filtrar tarefas por projeto, responsável, situação, prioridade, prazo e tipo.
- **RF012 -** o sistema deve permitir pesquisar tarefas pelo título.
- **RF013 -** o sistema deve manter os checklists vinculados às tarefas.
- **RF014 -** o sistema deve manter os comentários associados às tarefas.
- **RF015 -** o sistema deve manter os anexos associados aos projetos e às tarefas.
- **RF016 -** o sistema deve permitir a integração com o Google Drive para acesso a documentos autorizados.
- **RF017 -** o sistema deve manter a visualização dos prazos das tarefas em um calendário.
- **RF018 -** o sistema deve permitir a integração com o Google Calendar para sincronização de eventos.
- **RF019 -** o sistema deve enviar notificações destinadas aos usuários.
- **RF020 -** o sistema deve notificar os responsáveis um dia antes do vencimento das tarefas pendentes.
- **RF021 -** o sistema deve ter as configurações e os dados cadastrais dos usuários.
- **RF022 -** o sistema deve apresentar o percentual de conclusão das tarefas de cada projeto.
- **RF023 -** o sistema deve destacar as tarefas vencidas que ainda não foram concluídas.
- **RF024 -** o sistema deve controlar o acesso às funcionalidades e aos dados conforme as permissões dos usuários.
- **RF025 -** o sistema deve manter os dados armazenados no banco de dados.

## 4.2. Regras de Negócio (RN)

- **RN001:** cada usuário deve possuir um endereço de e-mail único.
- **RN002:** somente usuários autenticados podem acessar as funcionalidades restritas.
- **RN003:** as operações devem respeitar as permissões de acesso.
- **RN004:** toda tarefa deve estar vinculada a um projeto existente.
- **RN005:** as situações permitidas para as tarefas são "A fazer", "Em andamento" e "Concluído".
- **RN006:** as prioridades permitidas são Baixa, Média e Alta.
- **RN007:** as prioridades devem ser identificadas pelas cores amarela, laranja e vermelha, respectivamente.
- **RN008:** as tarefas devem ser classificadas como "Individual" ou "Em grupo".
- **RN009:** uma tarefa será considerada atrasada quando seu prazo vencer e ela não estiver concluída.
- **RN010:** o progresso do projeto deve ser calculado com base na proporção de tarefas concluídas.
- **RN011:** o sistema deve gerar notificações de vencimento um dia antes do prazo das tarefas pendentes.
- **RN012:** alterações nos prazos devem atualizar as notificações correspondentes.
- **RN013:** tarefas concluídas não devem gerar novos avisos de vencimento.
- **RN014:** a exclusão de registros deve respeitar a integridade dos dados relacionados.
- **RN015:** as integrações externas devem respeitar as permissões concedidas pelos usuários.
- **RN016:** os anexos devem respeitar as permissões de acesso aos projetos e às tarefas.

# 5. Requisitos Não Funcionais

Requisitos não funcionais (RNFs) são restrições que definem os atributos de qualidade do sistema, como segurança, desempenho, usabilidade, compatibilidade e confiabilidade.

- **RNF001 -** o sistema deve armazenar senhas utilizando hash seguro, nunca em texto puro.
- **RNF002 -** o sistema deve validar as permissões no servidor antes de executar operações protegidas.
- **RNF003 -** o sistema deve impedir o acesso não autorizado aos dados dos projetos.
- **RNF004 -** a interface deve ser intuitiva e organizada.
- **RNF005 -** a aplicação deve adaptar-se a computadores e celulares.
- **RNF006 -** o sistema deve apresentar tempo de resposta adequado nas operações comuns.
- **RNF007 -** o banco de dados deve utilizar chaves e validações para manter a consistência das informações.
- **RNF008 -** o sistema deve funcionar nos principais navegadores modernos.
- **RNF009 -** o código deve ser organizado para facilitar correções e atualizações.
- **RNF010 -** a interface não deve depender exclusivamente de cores para identificar prioridades ou situações.
- **RNF011 -** o sistema deve evitar perda e duplicação indevida de dados.

# 9. Considerações Finais

O sistema proposto busca melhorar a organização e o acompanhamento de projetos por meio da centralização de tarefas, responsáveis, prazos e documentos. O quadro Kanban, os filtros e as notificações deverão facilitar a visualização do andamento das atividades e contribuir para a redução de atrasos.

O desenvolvimento deverá priorizar inicialmente o cadastro, os projetos, as tarefas, o controle de acesso e a persistência no banco de dados. As integrações com Google Drive e Google Calendar deverão ser consideradas concluídas somente após a implementação e os testes das operações nos serviços externos.
