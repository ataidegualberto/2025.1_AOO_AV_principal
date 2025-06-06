# 📊 Diagramas UML do Sistema

> Visão Geral

<br>

## 🔹 [DIAGRAMA DE CASOS DE USO (PNG)](./DiagramaCasodeUso/Diagrama%20Caso%20de%20Uso.png)

> Ferramenta: LucidChart

> ### [Detalhamento dos Casos de Uso](./CasosUsoDescricao.md)

| Nome                   | Ator    | Descrição breve                        |
| ---------------------- | ------- | -------------------------------------- |
| Fazer Login            | Jogador | Permite acesso ao sistema              |
| Fazer Cadastro         | Jogador | Permite acesso ao sistemas             |
| Editar Perfil          | Jogador | Permite inserir informações no sistema |
| Buscar Jogadores       | Jogador | Permite integração entre usuários      |
| Visualizar Perfil      | Jogador | Permite obter informações de usuários  |
| Verificar Login        | Sistema | Permite validar o acesso ao sistema    |
| Cadastrar Jogos        | Jogador | Permite listar preferências            |
| Cadastrar Estilos      | Jogador | Permite listar preferências            |
| Cadastrar Horários     | Jogador | Permite listar preferências            |
| Cadastrar Plataformas  | Jogador | Permite listar preferências            |
| Filtrar por Plataforma | Jogador | Permite selecionar preferências        |
| Filtrar por Região     | Jogador | Permite selecionar preferências        |
| Filtrar por Jogos      | Jogador | Permite selecionar preferências        |
| Enviar Convites        | Jogador | Permite comunicação entre usuários     |
| Conversar com Jogadores| Jogador | Permite comunicação entre usuários     |
| Avaliar Jogadores      | Jogador | Permite rankear usuários               |
| Bloquear Jogadores     | Jogador | Permite gerenciar preferências         |
| Sugerir Jogadores      | Sistema | Permite integração entre usuários      |
| Gerenciar Chat         | Sistema | Permite boa experiência ao usuário     |
| Eviar Notificações     | Sistema | Permite integração entre usuários      |

<br>

## 🔹 [DIAGRAMA DE ATIVIDADE](./DiagramaDeAtividade)

### Fluxo de Ações

> Ferramenta: LucidChart

> ### [Detalhamento das Ações](./modelos/AtividadesDescricao.md)

| Nome                                                                            | Obs                               |
| ----------------------------------------------------------------------------    | --------------------------------- |
| [Buscar Jogadores](./DiagramaDeAtividade/DiagramaDeATVbuscarJogador.png)        | Filtro, Sugestões e Notificações  |
| [Editar Perfil](./DiagramaDeAtividade/DiagramaDeATVeditarPerfil.png)            | Preferências                      |
| [Acessar](./DiagramaDeAtividade/DiagramaDeATVloginCadastro.png)                 | Cadastro, Login                   |
| [Enviar Mensagem](./DiagramaDeAtividade/DiagramaDeATVenviarMensagem.png)        | Chat                              |
| [Enviar Notificação](./DiagramaDeAtividade/DiagramaDeATVenviarNotificação.png)  | Notificação                       |
| [Vizualizar Perfil](./DiagramaDeAtividade/DiagramaDeATVvisualizarPerfil.png)    | Vizualização, Bloqueio, Avaliação |

<br>

## 🔹 [DIAGRAMA DE CLASSE](./DiagramaDeClasse/DiagramaDeClasses.png)

### Abstração das Entidades

> Ferramenta: StarUML

> ### [Descrição das Classes]([./ClassesDescricao.md)

| Classes                | Métodos (Exemplos)                              |
| ---------------------- | ----------------------------------------------- |
| Usuário                | Login, Mudar Senha, Recuperar Senha             |
| Jogador                | Editar Perfil, Buscar Meus Jogos                |
| Sugestão               | Pontuação de Compatibilidade                    |
| Chat                   | Adicionar Mensagem                              |
| Mensagem               | Status de Leitura Para Jogador                  |
| Avaliação              |                                                 |
| Notificação            | Marcar Como Lida                                |
| Convite                | Aceitar Convite, Recusar Convite                |
| Serviço de Notificação | Enviar Notificação                              |
| Serviço de Matchmaking | Gerar Sugestão Para                             |
| Jogo                   | Obter Detalhes                                  |
| Estilo de Jogo         |                                                 |
| Serviço de Catalogo    | Listar Todos Jogos, Cadastrar Nova Plataforma   |
| Plataforma             | Listar Jogos                                    |
| Serviço de Usuário     | Cadastrar Usuário, Autenticar Usuário           |
| Serviço de Jogador     | Atualizar Perfil Jogador                        |
| Sistema                | Serviço Usuário, Serviço Jogador                |
| Serviço de Moderação   | Bloquear Jogador Sistema                        |

<br>

## 🔹 [DIAGRAMA DE ESTADOS](./DiagramaDeEstados)

### Possíveis Estados e suas Respectivas Transições

> Ferramenta: LucidChart

> ### [Descrição dos Estados]([./EstadosDescricao.md)

| Estados                                                             | Transições                                           |
| ------------------------------------------------------------------- | ---------------------------------------------------- |
| [Acesso ao Sistema](./DiagramaDeEstados/Acesso%20ao%20Sistema.png)  | Filtro, Sugestão e Notificação                       |
| [Buscar Jogadores](./DiagramaDeEstados/Buscar%20Jogadores.png)      | Filtro, Sugestão, Vizualização, Convite, Notificação |
| [Enviar Mensagem](./DiagramaDeEstados/Enviar%20Mensagem.png)        | Mensagem, Notificação                                |
| [Vizualizar Perfil](./DiagramaDeEstados/Visualizar%20Perfil.png)    | Vizualização, Funções                                |

<br>
