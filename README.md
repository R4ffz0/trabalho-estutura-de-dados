Implementação do TimSort em Python + Testes de Desempenho

O TimSort é um algoritmo de ordenação híbrido, criado por Tim Peters em 2002, e utilizado oficialmente como o sort padrão do Python (list.sort() e sorted()).

Ele combina:
Insertion Sort → eficiente para pequenas sequências já ordenadas
Merge Sort → estável, eficiente e com pior caso O(n log n)

A grande sacada do TimSort é que ele detecta automaticamente runs, que são partes já ordenadas do array, e aproveita isso para acelerar muito a ordenação.

O algoritmo ocorre basicamente em duas etapas:

Detectar e ordenar pequenos blocos (RUNS)
O array é dividido em blocos de tamanho fixo (no Python, geralmente 32).

Cada bloco é ordenado com Insertion Sort, que é extremamente rápido para listas pequenas.

Fazer merges sucessivos
Depois, os blocos já ordenados são combinados usando Merge Sort, dobrando o tamanho dos blocos a cada passo:

32 → 64 → 128 → 256 → ...
Esse processo continua até a lista inteira estar ordenada.

Complexidade do TimSort:
No melhor caso [O(n)] se da quando a lista já está ordenada ou quase ordenada e o TimSort detecta isso automaticamente.
No caso médio [O(n log n)] é o comportamento normal, alternando merges e análises das runs.
No pior caso [O(n log n)] tem os dados totalmente bagunçados mesmo assim ele mantém boa performance.

Experimentos Realizados
Foram feitos testes de desempenho com listas aleatórias de tamanhos:

Entrada 100: 0.126 ms
Entrada 1000: 1.871 ms
Entrada 10000: 26.019 ms
Entrada 100000: 386.501 ms

Para cada tamanho, o tempo de execução foi medido com time.perf_counter().

Gráficos Obtidos
O gráfico mostra a relação:

Tamanho da lista (n) × Tempo de execução (ms)

A curva cresce aproximadamente como n log n, o esperado para TimSort.

Funcionalidades do Programa
Opção de ordenação crescente ou decrescente
Entrada de números digitados pelo usuário
Ordenação com implementação manual do TimSort
Benchmark automático para diferentes tamanhos
Geração de gráfico usando Matplotlib

Como conclusão o TimSort se destaca porque é muito rápido em dados parcialmente ordenados, é estavel e isso mantém a ordem dos elementos iguais, tem uma implementação inteligente o que reduz o trabalho necessário e por fim apresenta ótimos resultados na prática, por isso é adotado no Python
