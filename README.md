# Arvore-de-Decisao

Dando continuidade a ideia é utilizar técnicas para classificar cada vez melhor as posições da NBA, dessa vez vamos usar o modelo de árvores de decisão.

É válido deixar comentado, que geralmente modelos de árvores são utlizados com uma quantidade maior de dados, o que pode ocasionar em Overfitting.

Inicialmente, trato as amostras removendo os outliers através dos método IQR, após vou usar o Cross-validation para avaliar o modelo visto que temos uma quantidade de dados limitados. 

O objetivo do Cross-validation é garantir que o modelo generalize bem para dados não vistos, reduzindo o risco de overfitting.

Vemos que os scores do nosso modelo são aceitaveis:

![image](https://github.com/user-attachments/assets/11183510-d6c5-4875-8295-68d4574f0d9a)

Ainda, evitanto o overfitting e buscando uma boa generalização dos dados, usei o Cross-validation para fazer uma análise em relação ao parâmetro 'depth' da árvore. Esse parâmetro diz sobre a profundidade da árvore, e dentro da nossa situação
um 'depth' muito grande pode ocasior o overfitting.

Aqui um gráfico mostrando a relação precisão X depth:

![image](https://github.com/user-attachments/assets/529c85c4-0326-498b-9d60-b80d10c270e6)

Então escolhi depth = 10.

( *Um parenteses aqui:*

![image](https://github.com/user-attachments/assets/fef5b877-0dcd-486d-a4d5-6e9db017e891)

*O conjunto teste tem uma defasagem em alguns clusters, então usei o método SMOTE (Synthetic Minority Over-sampling Technique) é uma técnica usada para criar novos dados 'sintéticas' para equilibrar nossa amostra.*

*Fecha parenteses.* )



**Resultados finais:**

Utilizando as Variaveis reias ('AST',	'REB',	'TOV',	'STL',	'BLK',	'PF', 'Altura',	'Peso')

![image](https://github.com/user-attachments/assets/06ae257e-d7b4-4d6f-b09c-7ad2a5131be7)

Utilizando as Componentes principais (combinação linear das Variaveis reias)

![image](https://github.com/user-attachments/assets/8a6e82a9-0eb6-4fe7-8cea-fcdf14139402)


- A accuracy realmente já é maior do que anteriormente (47.52%)
- As posições PF e SG por serem bem parecidas respectivamente com as C e PG , o modelo está com dificuldade em identificar corretamente muitos dos casos positivos reais (recall baixo). É válido um estudo mais profundo do porquê, mas inicialmente 'vou culpar' o Threshold (valor de corte que uma instância será classificada em uma determinada classe ) e a nossa amostra. Obs: usando um modelo de XGBoost pode solucionar nosso problema.
- Utilizando as C.P houve uma melhora no problema do recall das posições PF e SG, e na accuracy em geral.
  

