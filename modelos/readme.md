# 📊 Diagramas UML do Sistema

> Visão Geral

<br>

## 🔹 [DIAGRAMA DE CASOS DE USO (PNG)](./DiagramaCasodeUso/Diagrama%20Caso%20de%20Uso.png)

> Ferramenta: LucidChart

> ### [Detalhamento dos Casos de Uso](./modelos/CasosUsoDescricao.md)

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

<br>

| Nome                                                                            | Obs                               |
| ----------------------------------------------------------------------------    | --------------------------------- |
| [Buscar Jogadores](./DiagramaDeAtividade/DiagramaDeATVbuscarJogador.png)        | Filtro, Sugestões e Notificações  |
| [Editar Perfil](./DiagramaDeAtividade/DiagramaDeATVeditarPerfil.png)            | Preferências                      |
| [Acessar](./DiagramaDeAtividade/DiagramaDeATVloginCadastro.png)                 | Cadastro, Login                   |
| [Enviar Mensagem](./DiagramaDeAtividade/DiagramaDeATVenviarMensagem.png)        | Chat                              |
| [Enviar Notificação](./DiagramaDeAtividade/DiagramaDeATVenviarNotificação.png)  | Notificação                       |
| [Vizualizar Perfil](./DiagramaDeAtividade/DiagramaDeATVvisualizarPerfil.png)    | Vizualização, Bloqueio, Avaliação |

<br>

## 🔹 [DIAGRAMA DE CLASSE](./DiagramaDeClasses)

### Módulo de Usuário

> BREVE DESCRIÇÃO/LEGENDA

<br>

[ADICIONAR IMAGEM OU CODIGO (EXEMPLO)]([./DiagramaCasodeUso/Diagrama%20Caso%20de%20Uso.png)

<br>

## 🔹 [DIAGRAMA DE ESTADOS](./DiagramaDeEstados)

### TITULO DO DIAGRAMA

> Mostra os estados possíveis de cada entidade [ex: login] e as transições entre eles.

<br>

| Nome                            | Finalidade / Obs  |
| ------------------------------- | ----------------- |
| [Status Usuário](./DE_login.md) | Status do usuário |
| A2                              | B2                |
| A3                              | B3                |

