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
> Análise:
A ausência do fluxo alternativo previsto no caso de uso compromete a completude do diagrama. As notificações de convite necessitam de detalhamento, especialmente quanto a bloqueios e validações. Além disso, o diagrama de estados poderia ser mais fluido, oferecendo mais opções de navegação e interação para o usuário.

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
Permitir avaliação mútua dos jogadores após uma partida.

**Atores:**  
- Jogador

**Requisitos Funcionais:**  
- **RF06** – Avaliar jogador após partida

**Requisitos Não Funcionais:**  
- **RNF04** – Interface de avaliação amigável

**Regras de Negócio:**  
- **RN02** – Avaliação afeta sugestões de matchmaking

**Pré-condição:**  
- Partida entre os dois jogadores deve ter sido concluída.

**Pós-condição:**  
- Avaliação registrada e considerada em sugestões futuras.

**Fluxo Principal:**
1. Sistema solicita avaliação após partida.
2. Jogador fornece nota e/ou comentário.
3. Sistema registra avaliação.
4. Ranking do jogador é ajustado.

<br>

## CSU04 – Bloquear Jogador

**Finalidade:**  
Evitar interações com jogadores indesejados.

**Atores:**  
- Jogador

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
> Análise:
O principal ponto é a falta de uma melhor representação dessa função em um diagrama. Embora haja uma menção no DA02 – Editar Perfil, seria mais adequado criar um diagrama separado que destaque claramente a função de cadastro de horários e a forma como ele funciona, reforçando sua relevância como caso de uso próprio.

<br>

> Documento elaborado para a disciplina de Análise Orientada a Objetos, 2025
