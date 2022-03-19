Comunicação entre sistemas.

    Existem 2 formatos de comunicação: sincrona e assincrona.
    A comunicação sincrona é aquela que a o client da requisição aguarda a reposta
    A comunição asincrona é aquela que o client da requisição não espera pela resposta.

    - Rest
        Rest = Representantion State Of Transfer
        - Simplicidade
        - Cacheável

        Nivel 2 de maturidade do rest = Usar os verbos HTTP e padrão nas URLS 
        Nivel 3 de maturidade do rest = Além do nível 2, o retorno da request volta "links" que o usuário pode executar como próximos passos. Exem:
        Get /clientes/1
        Retorno JSON {
            client: {
                id: 1,
                name: 'pedro'
            },
            links: {
                saldo: "/clients/1/balance",
                pedidos: "/clients/1/orders"
            }
        }

        Caracteristicas de uma boa API REST
            - Utiliza URIs únicas para serviços e itens 
            - Utiliza todos os verbos HTTP para realizar seus  recusos
            - Provê links relacionais com o recurso acessado


    - gRPC
        gRPC é um framework desenvolvido pela Google que possibilita a comunição entre sistemas. É extramente rápido, leve e independente de linguagem.

        Quando utilizar? 
            - Micro serviços
            - Mobile, browser, Back-end
            - geração de bibliotecas de forma automática
            - Streaming bidirecional utiizando HTTP/2

        Linguagens oficiais:
            - GO
            - Java
            - C
                C++
                Python
                Ruby
                PHP
                Nodejs
                Dart
                Kotlin

        Com gRPC é possível se conectar via streaming e stream bi direcional.

    - GraphQL
        GraphQL é uma linguagem de consulta para API's e um runtime para atender a essas consultas com seus dados existentes. GraphQL fornece uma descrição completa e compreensível dos ados em sua API, dá aos clientes o poder de pedir exatamente o que eles precisam e nada mais, torna mais fácil evoluir API's ao longo do tempo e permite poderosas ferramentas para desenvolvedor.

        Vantagens: Endpoint único, Request única, Server apresenta os recursos disponíveis, cleint solicita a informação desejada.
        
        Com essa incrivel tecnologia é possível que o front-end defina o que ele quer receber.