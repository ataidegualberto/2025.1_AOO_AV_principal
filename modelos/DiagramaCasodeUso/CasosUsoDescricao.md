## 🔹 [DIAGRAMA DE CASOS DE USO](./DiagramaCasodeUso/Diagrama%20Caso%20de%20Uso.png)

> Descrição dos principais casos de uso do sistema, seus requisitos e regras de negócio.

<br>

## CSU01 – Buscar Jogadores

**Finalidade:**  
Listar jogadores com maior compatibilidade com base em horários, estilos de jogo e plataformas.

**Atores:**  
- Jogador

**Requisitos Funcionais:**  
- **RF01** – Aplicar filtros de busca (jogo, estilo, plataforma, região)  
- **RF02** – Listar jogadores compatíveis  
- **RF03** – Integrar dados de disponibilidade, estilo e plataforma no matchmaking

**Requisitos Não Funcionais:**  
- **RNF01** – Resposta da busca em até 3 segundos  
- **RNF02** – Interface amigável e responsiva

**Regras de Negócio:**  
- **RN02** – Jogadores mal avaliados aparecem com menor prioridade  
- **RN03** – Jogadores bloqueados não aparecem nos resultados

**Pré-condição:**  
- O jogador deve estar logado e com perfil preenchido (jogos, estilos e horários).

**Pós-condição:**  
- Exibição de uma lista de jogadores compatíveis, respeitando filtros e regras.

**Fluxo Principal:**
1. Jogador acessa a funcionalidade de busca.
2. Informa filtros desejados.
3. Sistema processa os critérios.
4. Regras de matchmaking são aplicadas.
5. Lista ordenada de jogadores é retornada.

**Fluxo Alternativo (FA01):**  
- Se nenhum jogador for compatível, exibe: _"Nenhum jogador encontrado com esses critérios."_

•Análise:
Ao analisar os artefatos, como o caso de uso CSU01, o diagrama de atividade DA03, o diagrama de estado DEM02 e as classes relacionadas, percebi alguns pontos que poderiam ser melhorados. Por exemplo, a pré-condição do caso de uso só fala que o jogador precisa estar logado e com o perfil preenchido, mas na prática o sistema depende de informações bem detalhadas, como estilos de jogo, horários e plataformas. Acho que isso poderia estar mais claro e o sistema deveria validar esses dados antes de permitir a busca.

Outro ponto é que o fluxo alternativo só cobre o caso de nenhum jogador compatível ser encontrado, mas não tem nada sobre o que acontece se der erro no sistema, ou se os filtros forem preenchidos de forma errada. 

•Sugestão: 
Deixar a pré-condição mais explícita e funcional.  Além disso, os diagramas poderiam contemplar melhor os diferentes caminhos que o usuário pode seguir, como cancelar, corrigir filtros ou lidar com erros.


<br>

## CSU02 – Enviar Convite

**Finalidade:**  
Permitir que um jogador convide outro para amizade e futuras partidas.

**Atores:**  
- Jogador

**Requisitos Funcionais:**  
- **RF04** – Enviar convite de amizade  
- **RF05** – Notificar jogador convidado

**Requisitos Não Funcionais:**  
- **RNF03** – Notificação em tempo real

**Pré-condição:**  
- Interação prévia via chat entre os jogadores.
  
\\ Não informa no DA04 nem o DEM03 tratam ou verificam essa pré-condição antes de liberar a ação “Enviar Convite”.
**Pós-condição:**  
- Convite enviado e notificação gerada para o destinatário.

**Fluxo Principal:**
1. Jogador acessa o perfil do outro jogador.
2. Verifica elegibilidade (chat prévio).
3. Clica em "Enviar Convite".
4. Sistema envia convite e notifica o outro jogador.

**Extensões:**  
- **CSU02.1** – Aceitar convite  
- **CSU02.2** – Notificações em tempo real


<br>

## CSU03 – Avaliar Jogador

**Finalidade:**  
Permitir avaliação mútua e estruturada dos jogadores após uma partida, garantindo que o sistema de reputação seja justo e impacte positivamente o matchmaking.

**Atores:**  
- Jogador

**Requisitos Funcionais:**  
- **RF06** – Apresentar opção de avaliação após a conclusão de uma partida  
- **RF07** – Validar a elegibilidade da avaliação (apenas entre participantes da mesma partida)  
- **RF08** – Registrar nota e comentário opcionais para a avaliação  
- **RF09** – Permitir a edição da avaliação dentro de um prazo determinado  

**Requisitos Não Funcionais:**  
- **RNF04** – Interface de avaliação clara, intuitiva e amigável  
- **RNF05** – Integridade dos dados de avaliação, garantindo o vínculo entre avaliador, avaliado e a partida correspondente  

**Regras de Negócio:**  
- **RN03** – Uma avaliação só pode ser submetida se existir um registro de partida concluída entre o avaliador e o avaliado  
- **RN04** – Um jogador só pode avaliar outro uma única vez por partida  
- **RN05** – A avaliação (nota e/ou comentário) impacta diretamente a pontuação de reputação do jogador, que é usada como critério no matchmaking (RN01)  
- **RN06** – Uma avaliação pode ser editada pelo autor em até 24 horas após ser submetida  

**Pré-condição:**  
- Uma partida entre os jogadores foi concluída e registrada no histórico do sistema.

**Pós-condição:**  
- Avaliação registrada e vinculada à partida específica  
- A pontuação de reputação do jogador avaliado é recalculada e atualizada  

**Fluxo Principal:**
1. Ao final de uma partida, o sistema notifica os jogadores sobre a disponibilidade da avaliação.
2. O jogador acessa a tela de avaliação a partir da notificação ou do histórico da partida.
3. O sistema valida a elegibilidade da avaliação, confirmando a participação de ambos na partida e a ausência de avaliação prévia.
4. O jogador seleciona uma nota (ex: 1 a 5) e, opcionalmente, escreve um comentário.
5. O jogador confirma o envio.
6. O sistema valida os dados (nota dentro do intervalo válido).
7. O sistema registra a avaliação, associando-a ao ID do avaliador, do avaliado e da partida.
8. O sistema recalcula a pontuação de reputação do jogador avaliado e exibe uma mensagem de sucesso.

**Fluxos Alternativos e de Exceção:**
- **FA01 – Recusa de Avaliação:**  
  Se o jogador ignorar a notificação ou fechar a tela, nenhuma avaliação é registrada. A opção permanecerá disponível no histórico da partida.  

- **FE01 – Erro na Submissão:**  
  Se ocorrer uma falha de conexão ou erro no servidor, o sistema exibe:  
  *"Erro ao registrar sua avaliação. Por favor, tente novamente."*  
  e preserva os dados inseridos.  

- **FE02 – Tentativa de Avaliação Duplicada:**  
  Se o jogador tentar avaliar o mesmo jogador pela mesma partida novamente, o sistema informa:  
  *"Você já avaliou este jogador para esta partida."*  
  e oferece a opção de editar a avaliação existente (se dentro do prazo da **RN06**).  

- **FE03 – Edição de Avaliação:**  
  O jogador localiza a avaliação em seu histórico, seleciona "Editar", modifica a nota/comentário e salva.  
  O sistema atualiza o registro e recalcula a reputação do jogador avaliado.

<br>

## CSU04 – Bloquear Jogador

**Finalidade:**  
Evitar interações com jogadores indesejados.

**Atores:**  
- Jogador  
- Administrador (para bloqueios/desbloqueios sistêmicos)

**Requisitos Funcionais:**  
- **RF07** – Bloquear jogador

**Requisitos Não Funcionais:**  
- **RNF05** – Confirmação e possibilidade de reversão do bloqueio

**Regras de Negócio:**  
- **RN03** – Jogadores bloqueados não aparecem nas buscas

**Pós-condição:**  
- Jogador bloqueado não poderá mais ser encontrado ou interagir.

**Fluxo Principal:**
1. Jogador acessa perfil do outro jogador.
2. Seleciona a opção "Bloquear jogador".
3. Sistema solicita confirmação.
4. Jogador é bloqueado e removido das buscas e contatos.

**Fluxos Alternativos:**  
- **FE01 – Cancelar bloqueio:**  
  1. Após passo 3, Jogador A clica em “Cancelar”.  
  2. Sistema aborta sem criar registro e retorna ao perfil.  
- **FE02 – Erro ao registrar bloqueio:**  
  1. Se falha de rede ou servidor no passo 5, exibe “Não foi possível bloquear. Tente novamente.” mantendo o motivo preenchido.  
- **FE03 – Bloqueio administrativo:**  
  1. Administrador invoca `bloquearJogadorSistema(B, motivo)`.  
  2. Sistema cria `Relacionamento{Admin→B, tipo=bloqueio, motivo, dataInicio}`.  
  3. Notifica B sobre bloqueio sistêmico.  

**Extensões:**  
- **CSU04.1 – Desbloquear Jogador**  
  - Fluxo muito similar ao principal, mas atualiza `dataFim` e `ativo=false`.  
  - Inclui confirmação “Tem certeza que deseja desbloquear?”  

<br>

## CSU05 – Cadastro de Horários

**Finalidade:**  
Permitir que o jogador informe seus horários disponíveis para jogar.

**Atores:**  
- Jogador

**Requisitos Funcionais:**  
- **RF08** – Definir manualmente ou aceitar sugestão automática de horários

**Requisitos Não Funcionais:**  
- **RNF06** – Interface intuitiva para seleção de horários

**Regras de Negócio:**  
- **RN04** – Horários podem ser definidos manualmente ou com base nos horários de login

**Pós-condição:**  
- Horários ficam salvos e usados no processo de matchmaking.

**Fluxo Principal:**
1. Jogador acessa sua agenda de disponibilidade.
2. Escolhe entre definir manualmente ou aceitar sugestão automática.
3. Sistema salva os dados.
4. Informações são utilizadas na busca por compatibilidade.

<br>

> Documento elaborado para a disciplina de Análise Orientada a Objetos, 2025
