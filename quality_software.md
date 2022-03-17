Perspectivas para arquitetar software de qualidade

    - Performance
        É o desempenho que o software possui para executar algo.
        Para medir ou avaliar a performace de um software podemos usar as medidas:
            - Latência ou response time
            - Throughput (Quantidade de requisições que aguenta)
            
        Ter um sistema performatico não significa ser escalavel.
        
        - Como melhorar a performance?
            Diminuir a latência
            Aumentando o Throughput
        
        - Principais razões para a baixa performance
            Processamento ineficiente
            Recursos computacionais limitados
            Trabalhar de forma bloqueante
            Acesso serial a recursos 

        - Principais dicas para aumentar a eficiência
            Escala de capacidade computacional
            Melhorar a lógica do software (Algoritimos, queries, overhead)
            Concorrência e paralelismo
            Banco de dados 
            Caching

        - Escala vertical x escala horizontal
            Escala vertical = Aumentar a capacidade computacional da maquina
            Escala horizontal = Aumenta a capacidade de maquinas (docker, container, loadbalancer e outros....)

        - Caching
            Cache na borda (Quando o cache ocorre antes msm de bater no servidor. Ex: Cloudflare)
            Cache de dados estáticos
            Cache de páginas/dados (DB)
            Cache de objetos

        - Edge computing
            É um tipo de cloud que tem diversos datacenters espalhados pelo mundo, esses datacenters são responsáveis por repassar arquivos estaticos de maneira mais rápida. 
            Pois se um client da BR estiver tentando acessar um arquivo que está hospedado no Japão, se esse arquivo tiver cache com Edge computing, nós não iremos recuperar o arquivo do datacenter original(Japão), mas sim do datacenter mais próximo. Provavelmente um datacenter aqui no Brasil mesmo, tornando assim a latencia muito menor para a resposta do arquivo.
    


    - Escalabilidade
        "Escalabilidade é a pacidade de sistemas suportarem o aumento (ou a redução) dos workloads incrementando ou reduzindo o custo em igual ou menor proporção"

        Pontos para escalar uma aplicação
            - Disco Efêmero (o disco pode ser apagado que o sistema não perde nenhum arquivo msm que isso aconteça)
            - SErvidor de aplicação (disco efêmero) 
            - Servdidor de ASSETS para arquivos staticos (imagens, documentos, mp3...) = - Upload -> Servidor de Assets
            - Servidor de cache ceentralizado
            - Servidor de sessões centralizado
        
        Pontos para escalar o banco de dados
            - Aumentar recursos computacionais
            - Distribuir responsabilidade (escrita vs leitura)
            - Shards de forma horizontal
            - Serveless
            - Trabalhar com índices de forma consciente
            - APM (Application performance monitoring) nas queries
            - Explain nas queires
            - CQRS (Command Query Responsibility Segregation)

        Proxy Reverso
            Proxy reverso é um servidor que fica na frente dos servidores web e encaminha as requisições do client (ex: navegador) para um servidor web.
            
            Soluções de proxy populares
                - Nginx
                - HaProxy (HA = High Availability)
                - Traefik
            
    - Resiliência
        Resiliência é um conjunto de estratégias adotadas intencionalmente para a adaptação de um sistema quando uma falha ocorre.
        Ter uma estratégia de resiliência nos possibilita minimizar os riscos de perder dados e transações.

        - Health Check (Checagem de saúde)
            Para criar um health check é preciso perguntar ao sistema, algo trivial como uma listagem de vendas. Se o sistema responder, em um tempo habil, com os dados esperados na resposta.. Provavelmente esse sistema está com a saúde OK. Mas se por exemplo, o timepo de resposta for muito longo, já pode indicar um tempo de atenção.

        - Rate Limiting
            É NECESSÁRIO SABER QUANTAS REQUISIÇÕES O SEU SISTEMA AGUENTA. Você tem que saber quantas requisições o sistema aguenta. Para chegar a esse resultado é preciso realizar um teste de estress.
            Se o sistema aguentar 50 requisições por segundo, se você bloquear acima de 50 requisições, você garante que seu sistema vai entregar pelo menos 50 requisições com qualdiade.  No mesmo cenário sem rate limiting ao receber 60, ou 80, 200 requisições o sistema vai ficar lento, dependendo da quantidade de requisições pode até memso  travar. 
            Porém, ao implementar precisa pensar se os consumidores(clients) do seu sistema(servidor) podem ou não ficar sem resposta por algum período até o servidor se recuperar.
            É possível definir um rate limiting programado para cada client.

        - Circuit Breaker
            Protege o sistema fazendo com que nas requisições feitas para ele sejam negadas Ex: HTTP 500
            - Circuito fechado (HTTP200,201...)
            - Circuito aberto (HTTP 500)
            - Meio aberto - Verifica se o sistema consegue responder as requisições e fica abrindo e fechando o circuito.

        - API Gateway
            É aqui que podemos fazer praticamente tudo que está descrito acima.

        - Service mesh
            Controlar o trafego da rede
            Evita implementações de proteção pelo próprio sistema.
            mTLS

        - Comunicação assíncrona
            Evita perda de dados
            Message broker / sistema de stream

        - Garantias de entrega com Retry
            Exponential backoff - Jitter     

    Quando pensamos em resiliência devemos pensar: 
        - O que acontece se o sistema cair? 
        - Haverá perda de informações/requisições ? 
        - O sistema está fora do ar? 
        - Como reiniciar o sistema? 