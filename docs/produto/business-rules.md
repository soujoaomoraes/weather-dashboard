# Regras de Negócio

Esta documentação detalha as regras de negócio que governam o funcionamento do Weather Dashboard.

## 1. Fontes de Dados e Priorização
- **Fonte Primária:** A API OpenWeatherMap será a fonte de dados principal para informações meteorológicas.
- **Fonte Secundária:** A WeatherAPI será utilizada como fallback caso a OpenWeatherMap esteja indisponível ou não retorne dados para uma localidade específica.
- **Consolidação de Dados:** Se ambas as fontes forem consultadas, os dados da OpenWeatherMap terão prioridade. Não haverá fusão de dados parciais de ambas as fontes para uma mesma requisição.

## 2. Atualização de Dados e Cache
- **Cache de API:** As respostas das APIs externas serão armazenadas em um cache (Redis) por **10 minutos** para cada localidade.
- **Latência:** Requisições para uma localidade já em cache devem responder em menos de 100ms. Requisições que necessitem de consulta externa devem responder em menos de 500ms.
- **Atualização em Tempo Real:** O dashboard no cliente não fará polling automático. O usuário precisará atualizar a página ou clicar em um botão "Atualizar" para obter os dados mais recentes, o que invalidará o cache para aquela localidade.

## 3. Geolocalização
- **Automática:** Ao acessar o webapp, o sistema solicitará permissão ao usuário para acessar sua geolocalização via navegador (HTML5 Geolocation API). Se concedida, exibirá o clima para a localização atual.
- **Manual:** O usuário pode pesquisar por qualquer cidade do mundo. A busca deve ser tolerante a erros de digitação e apresentar uma lista de resultados correspondentes.

## 4. Unidades de Medida
- **Padrão:** O sistema usará o sistema Métrico como padrão (Celsius, km/h).
- **Customização:** O usuário poderá alterar as unidades de medida para o sistema Imperial (Fahrenheit, mph) nas configurações. Essa preferência será salva localmente (localStorage) para usuários não autenticados e no banco de dados para usuários autenticados.

## 5. Autenticação e Dados do Usuário
- **Usuários Autenticados:** Usuários podem criar uma conta para salvar uma lista de cidades favoritas e manter suas preferências de unidade de medida sincronizadas entre dispositivos.
- **Dados Salvos:** O sistema armazenará o nome de usuário, e-mail (para login e recuperação de senha) e as configurações/cidades favoritas. A senha será armazenada de forma segura usando hashing (e.g., bcrypt).

## 6. Notificações (PWA)
- **Alertas Climáticos:** Notificações push serão enviadas apenas para usuários que optarem por recebê-las.
- **Gatilhos:** As notificações serão disparadas para alertas climáticos severos (tempestades, ventos fortes, etc.) para as cidades favoritas do usuário. A verificação de alertas será feita no backend a cada 1 hora.

## 7. Limites de Uso e API Keys
- **Gerenciamento de Chaves:** As chaves de API para os serviços externos (OpenWeatherMap, WeatherAPI) devem ser armazenadas de forma segura no backend (e.g., usando um secret manager) e nunca expostas no frontend.
- **Rate Limiting:** O backend implementará um rate limit de 60 requisições por minuto por endereço IP para proteger contra abuso.
