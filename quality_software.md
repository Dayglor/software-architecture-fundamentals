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
    - Resiliência