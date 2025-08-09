<design_research>
O objetivo é criar um dashboard meteorológico que seja ao mesmo tempo funcional e esteticamente agradável. A interface deve ser intuitiva, permitindo que os usuários acessem rapidamente as informações meteorológicas mais importantes. A experiência do usuário será focada na clareza e na simplicidade, com uma hierarquia visual bem definida que destaca os dados essenciais.

**Benchmarking:**
- **AccuWeather:** Forte em detalhes e previsões de longo prazo, mas a interface pode ser poluída.
- **The Weather Channel:** Ótimos mapas interativos, mas a experiência do usuário é interrompida por muitos anúncios.
- **Carrot Weather:** Conhecido por sua personalidade e humor, o que pode ser um diferencial.
- **Google Weather:** Interface limpa e minimalista, focada em informações rápidas.

**Jornada do Usuário:**
1.  **Persona 1: O Planejador Diário (Ana, 32 anos)**
    *   **Caso de Uso:** Ana verifica o tempo todas as manhãs para decidir o que vestir e se precisa levar um guarda-chuva. Ela quer uma visão geral rápida da previsão do dia e da semana.
2.  **Persona 2: O Viajante (Carlos, 45 anos)**
    *   **Caso de Uso:** Carlos viaja com frequência a trabalho. Ele precisa verificar o tempo em diferentes cidades para planejar suas viagens e fazer as malas adequadamente.
3.  **Persona 3: O Entusiasta do Tempo (Bruno, 25 anos)**
    *   **Caso de Uso:** Bruno é fascinado por meteorologia. Ele gosta de explorar dados detalhados, como velocidade do vento, pressão atmosférica e umidade. Ele aprecia gráficos interativos e dados em tempo real.

</design_research>
<wireframes>
**Tela Principal (Dashboard)**

*   **Header:**
    *   Logo do aplicativo à esquerda.
    *   Campo de busca de cidade no centro.
    *   Ícone de geolocalização à direita do campo de busca.
    *   Toggle de Dark/Light Mode e um ícone de menu (hambúrguer) à direita.
*   **Widget Principal:**
    *   Nome da cidade e país.
    *   Data e hora atual.
    *   Temperatura atual em destaque, com um ícone grande representando a condição climática (sol, nuvens, chuva, etc.).
    *   Descrição da condição climática (ex: "Parcialmente Nublado").
    *   Temperaturas máxima e mínima do dia.
*   **Previsão por Hora (Próximas 24 horas):**
    *   Carrossel horizontal com a previsão para as próximas horas.
    *   Cada item do carrossel mostra:
        *   Hora.
        *   Ícone da condição climática.
        *   Temperatura.
*   **Previsão da Semana (Próximos 7 dias):**
    *   Lista vertical com a previsão para os próximos 7 dias.
    *   Cada item da lista mostra:
        *   Dia da semana.
        *   Ícone da condição climática.
        *   Temperaturas máxima e mínima.
*   **Widgets de Detalhes:**
    *   Grid com cartões para informações adicionais:
        *   **Vento:** Velocidade e direção (com um ícone de bússola animado).
        *   **Umidade:** Porcentagem com uma barra de progresso.
        *   **Pressão Atmosférica:** Valor e tendência (subindo ou descendo).
        *   **Visibilidade:** Distância.
        *   **Índice UV:** Nível e recomendação.
        *   **Nascer e Pôr do Sol:** Horários com uma visualização gráfica do arco solar.

**Tela de Busca**

*   Aparece como um overlay ou uma nova página quando o usuário clica no campo de busca.
*   Lista de cidades recentes pesquisadas.
*   Resultados da busca em tempo real à medida que o usuário digita.
*   Feedback visual para estados de loading e erro.

**Menu Lateral (Aberto pelo ícone de hambúrguer)**

*   Links para:
    *   Dashboard (tela principal).
    *   Configurações (unidades de medida, notificações).
    *   Sobre o aplicativo.
    *   Feedback.

</wireframes>
<design_system>
**Tokens de Design**

*   **Cores (Paleta Dinâmica):**
    *   **Light Mode:**
        *   Fundo: `#F8F9FA` (Branco suave)
        *   Superfície: `#FFFFFF` (Branco puro para cartões)
        *   Texto Principal: `#212529` (Preto suave)
        *   Texto Secundário: `#6C757D` (Cinza)
        *   Acento (cores variam com o clima):
            *   Sol: `#FFC107` (Amarelo)
            *   Chuva: `#0D6EFD` (Azul)
            *   Nuvens: `#6C757D` (Cinza)
    *   **Dark Mode:**
        *   Fundo: `#121212` (Preto)
        *   Superfície: `#1E1E1E` (Cinza escuro para cartões)
        *   Texto Principal: `#E8EAED` (Branco suave)
        *   Texto Secundário: `#9AA0A6` (Cinza claro)
        *   Acento (mesmas cores do Light Mode, mas com mais saturação).
*   **Tipografia:**
    *   **Fonte Principal:** Inter (sans-serif) - moderna, legível e com boa variedade de pesos.
    *   **Títulos (h1, h2, h3):** Peso "Bold" (700).
    *   **Corpo de Texto:** Peso "Regular" (400).
    *   **Labels e Legendas:** Peso "Medium" (500).
*   **Espaçamentos (Base 8px):**
    *   `xs: 4px`
    *   `sm: 8px`
    *   `md: 16px`
    *   `lg: 24px`
    *   `xl: 32px`
    *   `xxl: 48px`
*   **Border Radius:**
    *   Pequeno: `4px`
    *   Médio: `8px`
    *   Grande: `16px`

**Componentes**

*   **Botões:** Estilos primário, secundário e terciário, com estados `hover`, `focus` e `disabled`.
*   **Cartões (Cards):** Componente base para todos os widgets, com sombra sutil e `border-radius` médio.
*   **Ícones:** Biblioteca de ícones consistentes (ex: Material Icons ou Feather Icons).
*   **Gráficos:** Gráficos de linha para tendências de temperatura e gráficos de barra para precipitação, usando `recharts` ou `Chart.js`.

</design_system>
<interactions>
*   **Loading State:**
    *   Esqueletos de UI (shimmer effect) para os widgets enquanto os dados da API são carregados.
*   **Transições de Tela:** Animações suaves de fade-in/fade-out.
*   **Hover em Gráficos:** Tooltips com informações detalhadas aparecem ao passar o mouse sobre os pontos de dados.
*   **Toggle de Modo:** Transição suave de cores entre os modos Dark e Light.
*   **Ícone de Vento:** A agulha da bússola gira para indicar a direção do vento.
*   **Scroll Suave:** Efeito de parallax sutil nos elementos do background ao rolar a página.

</interactions>
<accessibility>
*   **Contraste de Cores:** Garantir que todas as combinações de texto e fundo atendam aos critérios AA da WCAG 2.1.
*   **Labels para Controles:** Todos os botões, ícones e campos de formulário terão `aria-labels` descritivos.
*   **Navegação por Teclado:** O aplicativo será totalmente navegável usando a tecla Tab. Foco visível e lógico.
*   **Texto Alternativo:** Ícones e imagens terão `alt text` ou `aria-label` apropriado.
*   **Fontes Escaláveis:** Usar unidades relativas (rem) para a tipografia, permitindo que os usuários ajustem o tamanho do texto nas configurações do navegador.

</accessibility>