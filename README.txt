 Análisis de agrupamiento mediante el algoritmo SOM tras eliminar outliers aplicando la distancia de Mahalanobis. Se incluye conexión a la base de datos desde Python para mediante una consulta obtener los datos.
 
 Algoritmo SOM:
 
El algoritmo SOM (Self-Organizing Maps) es un algoritmo basado en una red neuronal artificial que
permite establecer una correspondencia entre los datos de entrada y un espacio bidimensional, creando
mapas topológicos, de manera que datos similares entre si activen neuronas en zonas próximas. Este
algoritmo puede ser utilizado para el clustering estableciendo cada casilla del espacio bidimensionales
como una categoría o clúster.

El funcionamiento del algoritmo se basa en un conjunto inicial de entrenamiento que permita ajustar los
pesos de las neuronas. Estos pesos comienzan o bien con valores aleatorios o bien con valores iniciales
muestreados uniformemente de un subespacio generado por los dos mayores vectores propios. Los
pesos se ajustarán de forma que los nodos de la red neuronal con pesos similares a un vector de entrada
permitirán ajustar los demás nodos de su entorno cercano (vecindario) aproximándolos a su peso. De
esta forma los pesos de las neuronas irán ajustándose y el tamaño del vecindario reduciéndose hasta

 Conjunto de datos 1:
 
En este caso, y dado que el número de nodos de la red se espera que sea relativamente bajo, se tomará
el mismo número de clusters que en kmeans. Esto de sebe a que para cantidades bajas de nodos el
resultado resulta muy similar.
En el primer apartado, se realizan los imports necesarios y se instancia la clase SOM, indicando un tamaño
del espacio bidimensional de 2x2, es decir, 4 categorías que, tal y como se vio en kmeans con el método
del codo, era una cantidad óptima. A continuación, se invoca el método fit_predict previamente
presentado y se almacenan los resultados (etiquetas de cluster) como una nueva columna del dataframe.
Por último, se imprimen los resultados mediante un pairplot que permita comparar cada par de variables.

En la anterior gráfica se pueden observar los diferentes clústers. Se puede apreciar como existen pares
de variables para los que no existe una distribución clara de los grupos, hallándose sus puntos
entremezclados, mientras que para otras si que se puede observar ciertas fronteras entre grupos. Estas
últimas constituyen una fuente de información útil para caracterizar cada grupo. Un ejemplo sería el caso
del par de variables SS y ST. En su gráfica se puede observar cómo los datos pertenecientes al clúster 1
se caracterizan por valores bajos de ST, independientemente del valor de SS. Los del clúster 2 ocurre lo
mismo, solo que para valores altos de ST. Mientras que entre los datos del cluster 0 y el 3 (que tienen
valores similares de ST), el factor diferenciador aparenta ser el valor de SS. Se puede observar un
comportamiento similar en el caso del par fc y ST. En este caso la diferencia sería que el factor
diferenciador entre el cluster 0 y el 3 es que al primero le corresponderían valores bajos de fc y al segundo
valores altos (teniendo ambos valores de ST similares). En definitiva, parece que la variable ST es
determinante para discernir si un dato pertenece al cluster 1, al cluster 2 o al grupo de clusters constituido
por el cluster 0 y el 3. En este último caso parece que tanto la variable SS como fc constituyen un factor
diferenciador suficiente para dictaminar si pertenecerán al 0 o al 3.

 Conjunto de datos 2 (World Databank)
 
Para el segundo aparatado se seguirá el mismo proceso que en el anterior. Se instancia la clase, en este
caso con un tamaño de espacio bidimensional de 3x1 que permita obtener tres clusters. Se toma de
nuevo el número de clusters de la prueba del codo realizada para kmeans. Por último se invoca el método
fit_predict y se imprimen los resultados en un pairplot.

En la anterior gráfica se puede observar la representación por pares de variables de los datos junto al
color que los clasifica en uno de los tres clústers. Los resultados son altamente similares a los obtenidos
utilizando kmeans. En general se puede distinguir un cluster, el 0, compuesto por datos de países con
niveles de PIB altos y grandes inversiones en el sector de la sanidad, así como mayores niveles de
consumo eléctrico propios de un estilo de vida más primer mundista. Esto deriva en una mayor
expectativa de vida, menor mortalidad en neonatales y un menor número de natalidad en adolescentes.
Por otra parte, sobresale otro clúster, el 2, compuesto por países con menos recursos económicos,
inversión en salud y consumo eléctrico que parece derivar en menores expectativas de vida, así como un
mayor número de nacimientos entre padres adolescentes.
Por último, se puede observar el clúster 1. Este está constituido por datos de países con valores
intermedios que parecen ser estados con cierto grado de desarrollo pero que no alcanzan los niveles de
PIB, inversión o consumo eléctrico de los países del clúster 0. Estos países resultan de especial interés ya
que constituyen la transición entre el grupo más privilegiado y el peor parado. Se observa como en ciertos
casos como la esperanza de vida o la mortalidad neonatal los países de este clúster obtienen valores muy
cercanos a los del clúster de los países más desarrollados a pesar de tener menor PIB y menor inversión
en sanidad. Un ejemplo de esto es la gráfica de esperanza de vida frente a la inversión en sanidad.

El hecho anterior puede resultar importante para los países del clúster 2 (menos desarrollados) ya que
podrían observar los modelos de estos países tratando de idear estrategias de gobierno o gestión que
permitan mejorar la calidad de vida del país con unos recursos limitados.
