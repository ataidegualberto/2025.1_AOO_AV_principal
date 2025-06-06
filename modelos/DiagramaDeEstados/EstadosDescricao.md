## 🔹 [Descrição dos Diagramas de Estados](./DiagramaDeEstados)


## DEM01 – Acesso ao Sistema

Este diagrama modela o ciclo de vida da sessão de um usuário, desde a tentativa de acesso até o logout.

**Finalidade:**
Descrever os estados em que um usuário pode se encontrar durante o processo de autenticação, cadastro e sessão ativa.

**Descrição dos Estados e Transições:**
- O processo inicia e, após um evento `Acessar`, o sistema entra em um de dois estados, dependendo da escolha do usuário:
    - **Estado `Entrando no sistema`**: Representa a tentativa de login.
        - **Ações (`do`)**: Enquanto neste estado, o sistema executa as atividades contínuas de `validarEmail` e `validarSenha`.
        - **Transição**: Ao receber o evento `Logar Usuario`, o sistema transita para o estado `Logando no sistema`.
    - **Estado `Cadastrando Usuario`**: Representa o processo de registro de um novo usuário.
        - **Ações (`do`)**: Executa as atividades de `validarNickname`, `validarEmail`, `validarSenha` e, por fim, `cadastrarUsuario`.
        - **Transição**: Após a conclusão, o evento `Logar Usuario` move o sistema para o estado `Logando no sistema`.
- **Estado `Logando no sistema`**: O estado em que o usuário está autenticado e com a sessão ativa.
    - **Transição**: Ao receber o evento `Sair`, o sistema transita para o estado `Deslogando`.
- **Estado `Deslogando`**: Um estado transitório que representa o encerramento da sessão.
    - **Transição**: Após a conclusão, o sistema retorna ao ponto inicial de escolha (Acessar).

**Requisitos Relacionados:**
- **RF01:** Cadastro de usuário.
- **RF06:** Login com autenticação segura.
- **RF07:** Edição e visualização de perfil de jogador (pressupõe um usuário logado).

---

## DEM02 – Buscar Jogadores

Este diagrama descreve os diferentes estados de um processo de busca por jogadores, desde a filtragem até o envio de convites.

**Finalidade:**
Modelar o comportamento e os estados de uma sessão de busca de jogadores.

**Descrição dos Estados e Transições:**
- O processo inicia no estado `Buscando Jogadores`. Uma condição determina o próximo estado:
    - **Se `Sem Filtro`**: Transita diretamente para `Sugerindo jogadores`.
    - **Se houver filtros**: Transita para o estado `Filtrando`.
- **Estado `Filtrando`**: Representa a aplicação de critérios de busca.
    - **Ações de Entrada (`entry`)**: Ao entrar neste estado, o sistema executa as ações `filtrarPorRegião`, `filtrarPorJogo` e `filtrarPorPlataforma`.
    - **Transição**: Após a conclusão, transita automaticamente para `Sugerindo jogadores`.
- **Estado `Sugerindo jogadores`**: O sistema processou os dados e aguarda a ação do usuário sobre a lista de sugestões.
    - **Transição**: Ao selecionar um jogador, transita para `Visualizando o Perfil`.
- **Estado `Visualizando o Perfil`**: O usuário está analisando o perfil de um jogador encontrado.
    - **Transição**: A partir daqui, o usuário pode:
        - Iniciar um convite, transicionando para `Enviando Convite`.
        - Acionar o evento `Cancelar busca`, que finaliza o processo.
- **Estado `Enviando Convite`**: O sistema está processando um convite para o jogador visualizado.
    - **Ação (`do`)**: Executa a atividade `enviarConvite`.
    - **Transição**: Ao concluir, transita para `Enviando notificação`.
- **Estado `Enviando notificação`**: O sistema está gerando a notificação sobre o convite enviado.
    - **Ação (`do`)**: Executa a atividade `enviarNotificacao`.
    - **Transição**: Ao finalizar, pode retornar ao estado de `Sugerindo jogadores` (para que o usuário possa interagir com outros resultados da busca) ou finalizar o processo.

**Requisitos Relacionados:**
- **RF08:** Sugestão automática de jogadores compatíveis.
- **RF09:** Busca com filtros.
- **RF11:** Envio e recebimento de convites para jogos.
- **RF12:** Notificações sobre mensagens, convites e novas sugestões.

---

## DEM03 – Visualizar Perfil

Este diagrama  ilustra as funcionalidades disponíveis quando um usuário está no estado de visualização de um perfil.

**Finalidade:**
Modelar o estado de "visualização de perfil" como um estado que habilita um conjunto de ações (funcionalidades).

**Descrição dos Estados e Transições:**
- **Estado `Visualizando Perfil`**: O estado inicial onde o usuário está na tela de perfil de outro jogador.
    - **Transição**: O sistema transita automaticamente para o estado composto `Funcionalidades`.
- **Estado Composto `Funcionalidades`**: Este é um superestado que contém um conjunto de subestados, representando todas as ações que o usuário pode realizar a partir do perfil. Os subestados são:
    - `Adicionar como amigo`
    - `Convite para Jogar`
    - `Enviar Mensagem`
    - `Bloquear Perfil`
    - `Avaliar Jogador`
- **Transição de Saída**: Após o usuário executar qualquer uma das funcionalidades, o sistema transita para o estado `Saindo do Perfil`.
- **Estado `Saindo do Perfil`**: Um estado finalizador que representa a conclusão da interação com o perfil, levando ao término do fluxo.

**Requisitos Relacionados:**
- **RF07:** Edição e visualização de perfil de jogador.
- **RF10:** Conversas entre jogadores.
- **RF11:** Envio e recebimento de convites para jogos.
- **RF13:** Avaliação de jogadores após partidas.
- **RF14:** Bloqueio de jogadores indesejados.

---

## DEM04 – Enviar Mensagem

Este diagrama ilustra o ciclo de vida de um objeto de mensagem durante o processo de envio, considerando diferentes permissões.

**Finalidade:**
Modelar os estados de uma mensagem desde sua criação até a notificação de envio, diferenciando o envio para amigos e não amigos.

**Descrição dos Estados e Transições:**
- O fluxo se inicia e a mensagem entra em um estado geral `Enviando Mensagem`.
- A partir daqui, uma condição (se o destinatário é amigo ou não) define o próximo estado:
    - **Estado `Enviando para amigo`**: Estado simples que representa o envio para um contato que não requer verificações adicionais.
    - **Estado `Enviando para não amigo`**: Estado que lida com o envio para jogadores que não estão na lista de amigos.
        - **Ação de Entrada (`entrada`)**: Ao entrar neste estado, a ação `verificarPermissao` é executada para validar se a mensagem pode ser enviada.
        - **Ação de Saída (`saida`)**: Ao sair deste estado, a ação `enviarMensagem` é efetivamente disparada.
- **Transição para Notificação**: Ambos os caminhos (`Enviando para amigo` e `Enviando para não amigo`) convergem e transitam para o estado `Notificar`.
- **Estado `Notificar`**: Representa a criação de uma notificação para o remetente e/ou destinatário.
- Após a notificação, o processo é concluído e o sistema atinge o estado final.

**Requisitos Relacionados:**
- **RF10:** Conversas entre jogadores.
- **RF12:** Notificações sobre mensagens, convites e novas sugestões.
