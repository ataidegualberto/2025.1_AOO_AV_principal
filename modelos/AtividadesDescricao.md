## 🔹 [Descrição dos Diagramas de Atividade](./DiagramaDeAtividade)


## DA01 – Acesso ao Sistema

Este diagrama detalha os processos de **autenticação** e **cadastro** de um novo jogador no sistema.

**Finalidade:**
Permitir que um usuário acesse sua conta ou crie um novo perfil de jogador.

**Fluxo Descrito:**
1.  O processo inicia e o usuário escolhe entre `Entrar` (Login) ou `Cadastrar` (Registrar).
2.  **Se `Entrar`:**
    - O usuário fornece o **Email** e a **Senha**.
    - O sistema realiza a **validação** das credenciais.
    - Se válidas (```sim```), o acesso é concedido e o fluxo termina.
    - Se inválidas (```não```), o sistema solicita a senha novamente.
3.  **Se `Cadastrar`:**
    - O usuário fornece um **Nick** (apelido), que é validado.
    - Em seguida, cadastra um **Email**, que passa por uma validação.
    - Por fim, o usuário cria uma **Senha**, que também é validada.
    - Se todas as etapas forem concluídas com sucesso (```sim```), o perfil é criado, o acesso é concedido e o fluxo termina.
    - Se qualquer etapa falhar (```não```), o sistema retorna ao passo com erro para correção.

**Requisitos Relacionados:**
- **RF01:** Cadastro de usuário.
- **RF06:** Login com autenticação segura.

---

## DA02 – Editar Perfil

Este diagrama representa as ações que um jogador pode realizar para customizar e atualizar as informações de seu perfil.

**Finalidade:**
Permitir que o jogador cadastre e modifique suas informações de jogos, plataformas, estilos de jogo e horários de disponibilidade.

**Fluxo Descrito:**
1.  O jogador inicia a edição do perfil.
2.  O sistema apresenta as opções que podem ser alteradas de forma concorrente: `Cadastrar Horários`, `Cadastrar Plataformas`, `Cadastrar Jogos` e `Cadastrar Estilos`.
3.  Para cada opção, o jogador insere a informação desejada e o sistema pergunta se deseja `Salvo?`.
4.  Se o jogador não salva (```não```), ele pode alterar a informação novamente.
5.  Uma vez que todas as informações desejadas são salvas (```sim```), as atividades são sincronizadas e o processo de edição é finalizado.

**Requisitos Relacionados:**
- **RF02:** Cadastro de plataformas.
- **RF03:** Cadastro de jogos.
- **RF04:** Cadastro de estilos.
- **RF05:** Cadastro de horários.
- **RF07:** Edição e visualização de perfil de jogador.

**Regras de Negócio Aplicadas:**
- **RN04:** Horário de disponibilidade definido manualmente ou automaticamente por login.
- **RN05:** Cada jogador pode selecionar seus estilos de jogos principais.

---

## DA03 – Buscar Jogadores

Este diagrama ilustra o processo de busca e sugestão de jogadores compatíveis.

**Finalidade:**
Encontrar outros jogadores com base em filtros específicos ou através de sugestões automáticas do sistema para facilitar a formação de equipes.

**Fluxo Descrito:**
1.  O jogador inicia a busca.
2.  Ele pode optar por aplicar **filtros** (```sim```) ou ir direto para as sugestões (```não```).
3.  **Se filtrar:** O jogador pode aplicar filtros de `Jogos`, `Região`, `Plataforma` e `Estilo` de forma sequencial.
4.  Após a aplicação dos filtros (ou se não aplicou nenhum), o sistema executa a ação `Sugerir Jogadores`, que processa os dados e exibe uma lista de perfis.
5.  Ao visualizar a lista, o jogador tem três opções:
    - **Enviar convite:** Dispara uma notificação para o outro jogador.
    - **Visualizar perfil:** Acessa a tela de perfil do jogador selecionado.
    - **Encerrar:** Finaliza o fluxo de busca.

**Requisitos Relacionados:**
- **RF08:** Sugestão automática de jogadores compatíveis (matchmaking).
- **RF09:** Busca com filtros (jogo, plataforma, região, estilo, etc.).
- **RF11:** Envio e recebimento de convites para jogos.

**Regras de Negócio Aplicadas:**
- **RN02:** Jogadores mal avaliados têm menor prioridade nas sugestões.
- **RN03:** Jogadores bloqueados não aparecem em buscas ou sugestões.

---

## DA04 – Visualizar Perfil

Este diagrama descreve as interações possíveis quando um jogador está visualizando o perfil de outro jogador.

**Finalidade:**
Oferecer ações contextuais como enviar convite, avaliar ou bloquear um jogador a partir da tela de seu perfil.

**Fluxo Descrito:**
1.  Ao visualizar o perfil de outro jogador, o usuário tem três ações principais disponíveis: `Enviar convite?`, `Avaliar jogadores` e `Bloquear jogador`.
2.  **Se `Enviar convite?`**: Uma **notificação** de amizade/jogo é enviada ao outro jogador.
3.  **Se `Avaliar jogadores`**:
    - O usuário é levado a `Selecionar quantidade de estrelas`.
    - O sistema pergunta se deseja `Salvar?`. Se sim, a avaliação é registrada. Se não, a avaliação é descartada.
4.  **Se `Bloquear jogador`**:
    - O usuário pode informar um **motivo**, escolhendo entre `Incompatibilidade`, `Abuso verbal` ou `Digite o motivo`.
    - O bloqueio é efetivado e o fluxo se encerra.
    - O diagrama também mostra a opção `Desbloquear jogador` para reverter a ação.

**Requisitos Relacionados:**
- **RF07:** Edição e visualização de perfil de jogador.
- **RF11:** Envio e recebimento de convites para jogos.
- **RF13:** Avaliação de jogadores após partidas.
- **RF14:** Bloqueio de jogadores indesejados.

**Regras de Negócio Aplicadas:**
- **RN02:** A avaliação registrada aqui afetará a prioridade do jogador nas sugestões.
- **RN03:** O bloqueio realizado aqui impedirá que o jogador apareça em futuras buscas.

---

## DA05 – Enviar Mensagem

Este diagrama detalha o funcionamento do sistema de chat.

**Finalidade:**
Permitir a comunicação textual entre jogadores, seja em um chat privado ou em um canal global.

**Fluxo Descrito:**
1.  O processo começa quando o jogador aciona a função de mensagem.
2.  Ele escolhe entre `Chat Pessoal` e `Chat Global`.
3.  Independentemente da escolha, ele entra na tela de `Conversa`.
4.  Na conversa, ele pode realizar as ações de `Enviar mensagem` e `Receber mensagem`.
5.  Dentro da conversa, o jogador tem a opção de `Visualizar perfil?` do seu interlocutor.
6.  Se optar por visualizar (```sim```), ele é direcionado para a atividade "Visualizar Perfil". Se não (```não```), o fluxo de mensagens é encerrado.

**Requisitos Relacionados:**
- **RF10:** Conversas entre jogadores.
- **RF07:** Edição e visualização de perfil de jogador (como uma ação secundária).

---

## DA06 – Gerenciar Notificação

Este diagrama mostra como um usuário interage com as notificações recebidas no sistema.

**Finalidade:**
Permitir que o jogador visualize e responda às notificações recebidas, como convites de amizade ou para partidas.

**Fluxo Descrito:**
1.  O fluxo é iniciado quando o sistema envia uma **notificação** ao jogador.
2.  O jogador acessa suas **notificações**.
3.  Para uma notificação específica, ele tem três opções de ação: `Aceitar`, `Rejeitar` ou `Excluir`.
4.  As ações `Aceitar` e `Rejeitar` disparam uma **notificação** de volta ao remetente, informando a decisão. A ação `Excluir` apenas remove a notificação.
5.  Após a ação ser executada, o fluxo é finalizado.

**Requisitos Relacionados:**
- **RF12:** Notificações sobre mensagens, convites e novas sugestões.
- **RF11:** Envio e recebimento de convites para jogos (representa o lado do receptor).
