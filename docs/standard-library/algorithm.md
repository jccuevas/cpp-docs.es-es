---
title: "&lt;algorithm&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<algorithm>"
  - "std::<algorithm>"
  - "algorithm/std::<algorithm>"
  - "std.<algorithm>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<algorithm> (encabezado)"
  - "algorithm (encabezado) [C++]"
  - "Biblioteca estándar de C++, algoritmos"
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
caps.latest.revision: 23
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;algorithm&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las funciones de plantilla contenedor de la Biblioteca de plantillas estándar \(STL\) que realizan algoritmos.  
  
## Sintaxis  
  
```  
(see relevant links below for specific algorithm syntax)  
```  
  
## Comentarios  
 Los algoritmos de STL son genéricos porque pueden funcionar en diversas estructuras de datos.  Las estructuras de datos en las que se pueden usar incluyen no solo de las clases contenedoras de STL como `vector` y `list`, sino también estructuras de datos y matrices de elementos definidas por el programa que cumplen los requisitos de un algoritmo determinado.  Para lograr este nivel de generalidad, los algoritmos de STL acceden a los elementos de un contenedor y los recorren indirectamente mediante iteradores.  
  
 Los algoritmos de STL procesan los intervalos de iteradores que se suelen especificar por sus posiciones inicial o final.  Los intervalos a los que se hace referencia deben ser válidos en el sentido de que todos los punteros de los intervalos se deben poder desreferenciar y, dentro de las secuencias de cada intervalo, se debe poder llegar a la última posición desde la primera mediante incrementos.  
  
 Los algoritmos de STL extienden las acciones que admiten las operaciones y las funciones miembro de cada contenedor de STL y permiten trabajar, por ejemplo, con diferentes tipos de objetos contenedor al mismo tiempo.  Se usan dos sufijos para transmitir información sobre el propósito de los algoritmos.  
  
-   El sufijo `_if` indica que el algoritmo se usa con objetos de función que operan sobre los valores de los elementos, en lugar de usarse con los valores de los propios elementos.  El algoritmo `find_if` busca los elementos cuyos valores satisfacen el criterio especificado por un objeto de función y el algoritmo `find` busca un valor determinado.  
  
-   El sufijo \_copy indica que el algoritmo no solo manipula los valores de los elementos, sino que también copia los valores modificados a un intervalo de destino.  El algoritmo `reverse` invierte el orden de los elementos dentro de un intervalo y el algoritmo `reverse_copy` también copia el resultado a un intervalo de destino.  
  
 Los algoritmos de STL se suelen clasificar en grupos que indican de alguna manera su propósito o sus requisitos.  Entre ellos se incluyen algoritmos de modificación que cambian el valor de los elementos, a diferencia de los algoritmos que no son de modificación, que no lo hacen.  Los algoritmos de mutación cambian el orden de los elementos, pero no los valores de sus elementos.  Los algoritmos de eliminación pueden eliminar elementos de un intervalo o de una copia de un intervalo.  Los algoritmos de ordenación reordenan los elementos de un intervalo de varias maneras y los algoritmos de intervalo ordenado solo actúan sobre los algoritmos cuyos elementos se han ordenado de una manera determinada.  
  
 Los algoritmos numéricos de STL que se proporcionan para el procesamiento numérico tienen su propio archivo de encabezado [\<numeric\>](../standard-library/numeric.md), y los objetos de función y los adaptadores se definen en el encabezado [\<functional\>](../standard-library/functional.md). Los objetos de función que devuelven valores booleanos se conocen como predicados.  El predicado binario predeterminado es el `operator<` de comparación.  En general, los elementos que se van a ordenar deben ser menores que otros comparables para que, dados dos elementos cualesquiera, se pueda determinar que son equivalentes \(en el sentido de que ninguno es menor que el otro\) o que uno es menor que el otro.  Esto produce una ordenación entre los elementos no equivalentes.  
  
### Funciones  
  
|||  
|-|-|  
|[adjacent\_find](../Topic/adjacent_find.md)|Busca dos elementos adyacentes que son iguales o cumplen una condición especificada.|  
|[all\_of](../Topic/all_of.md)|Devuelve `true` cuando una condición está presente en todos los elementos del intervalo especificado.|  
|[any\_of](../Topic/any_of.md)|Devuelve `true` cuando una condición está presente al menos una vez en el intervalo especificado de elementos.|  
|[binary\_search](../Topic/binary_search.md)|Comprueba si hay un elemento en un intervalo ordenado que sea igual a un valor especificado o equivalente a este del modo especificado por un predicado binario.|  
|[copy](../Topic/copy.md)|Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia delante.|  
|[copy\_backward](../Topic/copy_backward.md)|Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia atrás.|  
|[copy\_if](../Topic/copy_if.md)|Copia todos los elementos de un intervalo especificado que comprueban `true` para una condición especificada|  
|[copy\_n](../Topic/copy_n.md)|Copia un número especificado de elementos.|  
|[count](../Topic/count.md)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con un valor especificado.|  
|[count\_if](../Topic/count_if.md)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con una condición especificada.|  
|[equal](../Topic/equal.md)|Compara dos intervalos elemento a elemento para ver si son iguales o equivalentes según lo especificado por un predicado binario.|  
|[equal\_range](../Topic/equal_range.md)|Busca un par de posiciones en un intervalo ordenado; la primera es menor o equivalente a la posición de un elemento especificado y la segunda es mayor que la posición del elemento, donde el sentido de equivalencia o de ordenación empleado para establecer las posiciones en la secuencia se puede especificar con un predicado binario.|  
|[fill](../Topic/fill.md)|Asigna el mismo valor nuevo a cada elemento de un intervalo especificado.|  
|[fill\_n](../Topic/fill_n.md)|Asigna un nuevo valor a un número especificado de elementos en un intervalo que comienza con un elemento determinado.|  
|[find](../Topic/find%20\(STL\).md)|Busca la posición de la primera aparición de un elemento en un intervalo que tiene un valor especificado.|  
|[find\_end](../Topic/find_end.md)|Busca en un intervalo la última subsecuencia que es idéntica a una secuencia especificada o que es equivalente según lo especificado por un predicado binario.|  
|[find\_first\_of](../Topic/find_first_of.md)|Busca la primera aparición de cualquiera de varios valores dentro de un intervalo de destino o la primera aparición de cualquiera de varios elementos que son equivalentes según lo especificado por un predicado binario en un conjunto especificado de los elementos.|  
|[find\_if](../Topic/find_if.md)|Busca la posición de la primera aparición de un elemento en un intervalo que cumple una condición especificada.|  
|[find\_if\_not](../Topic/find_if_not.md)|Devuelve el primer elemento del intervalo indicado que no satisface una condición.|  
|[for\_each](../Topic/for_each.md)|Aplica un objeto de función especificado a cada elemento en un orden hacia delante dentro de un intervalo y devuelve el objeto de función.|  
|[generate](../Topic/generate.md)|Asigna los valores generados por un objeto de función a cada elemento de un intervalo.|  
|[generate\_n](../Topic/generate_n.md)|Asigna los valores generados por un objeto de función a un número especificado de elemento de un intervalo y vuelve a la posición situada una más allá del último valor asignado.|  
|[includes](../Topic/includes.md)|Prueba si un intervalo ordenado contiene todos los elementos incluidos en un segundo intervalo ordenado, donde el criterio de ordenación o equivalencia entre los elementos se pueden especificar mediante un predicado binario.|  
|[inplace\_merge](../Topic/inplace_merge.md)|Combina los elementos de dos intervalos ordenados consecutivos en un único intervalo ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[is\_heap](../Topic/is_heap.md)|Devuelve `true` si los elementos del intervalo especificado forman un montón.|  
|[is\_heap\_until](../Topic/is_heap_until.md)|Devuelve `true` si el intervalo especificado forma un montón hasta el último elemento.|  
|[is\_partitioned](../Topic/is_partitioned.md)|Devuelve `true` si todos los elementos del intervalo especificado que prueban si una condición es `true` aparecen antes que cualquier elemento que prueba si es `false`.|  
|[is\_permutation](../Topic/is_permutation.md)|Determina si los elementos de un intervalo determinado forman una permutación válida.|  
|[is\_sorted](../Topic/is_sorted.md)|Devuelve `true` si los elementos del intervalo especificado están ordenados.|  
|[is\_sorted\_until](../Topic/is_sorted_until.md)|Devuelve `true` si los elementos del intervalo especificado están ordenados.|  
|[iter\_swap](../Topic/iter_swap.md)|Intercambia dos valores a los que se hace referencia mediante un par de iteradores especificados.|  
|[lexicographical\_compare](../Topic/lexicographical_compare.md)|Compara dos secuencias elemento a elemento para determinar cuál es menor de los dos.|  
|[lower\_bound](../Topic/lower_bound.md)|Busca la posición del primer elemento en un intervalo ordenado que tiene un valor mayor o equivalente a un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[make\_heap](../Topic/make_heap.md)|Convierte elementos de un intervalo especificado en un montón en el que el primer elemento es el mayor y para el que se puede especificar un criterio de ordenación con un predicado binario.|  
|[max](../Topic/max.md)|Compara dos objetos y devuelve el mayor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[max\_element](../Topic/max_element.md)|Busca la primera aparición del elemento mayor en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[merge](../Topic/merge.md)|Combina todos los elementos de dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[min](../Topic/min.md)|Compara dos objetos y devuelve el menor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[min\_element](../Topic/min_element.md)|Busca la primera aparición del menor elemento en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[minmax](../Topic/minmax.md)|Compara dos parámetros de entrada y los devuelve como un par, en orden de menor a mayor.|  
|[minmax\_element](../Topic/minmax_element.md)|Realiza el trabajo efectuado por [min\_element](../Topic/min_element.md) y [max\_element](../Topic/max_element.md) en una llamada.|  
|[mismatch](../Topic/mismatch.md)|Compara dos intervalos elemento a elemento para ver si son iguales o equivalentes según lo especificado por un predicado binario y busca la primera posición donde se produce una diferencia.|  
|[mover](../Topic/%3Calg%3E%20move.md)|Mueve los elementos asociados a un intervalo especificado.|  
|[move\_backward](../Topic/move_backward.md)|Mover los elementos de un iterador a otro.  El movimiento comienza con el último elemento de un intervalo especificado y termina con el primer elemento de ese intervalo.|  
|[next\_permutation](../Topic/next_permutation.md)|Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe, donde el sentido de siguiente se puede especificar con un predicado binario.|  
|[none\_of](../Topic/none_of.md)|Devuelve `true` cuando una condición nunca está presente entre los elementos del intervalo especificado.|  
|[nth\_element](../Topic/nth_element.md)|Divide un intervalo de elementos correctamente situando el *enésimo* elemento de la secuencia en el intervalo de modo que todos los elementos que hay delante sean menores o iguales que él y todos los elementos que lo siguen en la secuencia sean mayores o iguales que él.|  
|[partial\_sort](../Topic/partial_sort.md)|Organiza un número especificado de los elementos menores de un intervalo en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario.|  
|[partial\_sort\_copy](../Topic/partial_sort_copy.md)|Copia los elementos de un intervalo de origen a un intervalo de destino donde los elementos de origen están ordenados por menor que u otro predicado binario especificado.|  
|[partition](../Topic/partition.md)|Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen.|  
|[partition\_copy](../Topic/partition_copy.md)|Copia a un destino los elementos para los que una condición es `true` y a otro destino diferente los elementos para los que la condición es `false`.  Los elementos deben proceder de un intervalo especificado.|  
|[partition\_point](../Topic/partition_point.md)|Devuelve el primer elemento del intervalo especificado que no satisface la condición.  Los elementos se ordenan de forma que aquellos que satisfacen la condición están antes que los que no lo hacen.|  
|[pop\_heap](../Topic/pop_heap.md)|Quita el elemento mayor del principio de un montón hasta la penúltima posición del intervalo y después forma un nuevo montón con los elementos restantes.|  
|[prev\_permutation](../Topic/prev_permutation.md)|Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe, donde el sentido de siguiente se puede especificar con un predicado binario.|  
|[push\_heap](../Topic/push_heap.md)|Agrega un elemento que está al final de un intervalo a un montón existente que se compone de los elementos anteriores del intervalo.|  
|[random\_shuffle](../Topic/random_shuffle.md)|Reorganiza una secuencia de *N* elementos de un rango en una de *N*\!  organizaciones posibles seleccionadas aleatoriamente.|  
|[remove](../Topic/remove.md)|Elimina un valor especificado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.|  
|[remove\_copy](../Topic/remove_copy.md)|Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos de un valor especificado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.|  
|[remove\_copy\_if](../Topic/remove_copy_if.md)|Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos que satisfacen un predicado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.|  
|[remove\_if](../Topic/remove_if.md)|Elimina los elementos que cumplen un predicado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.|  
|[replace](../Topic/replace.md)|Examina cada elemento de un intervalo y lo reemplaza si coincide con un valor especificado.|  
|[replace\_copy](../Topic/replace_copy.md)|Examina cada elemento de un intervalo de origen y lo reemplaza si coincide con un valor especificado y copia el resultado a un nuevo intervalo de destino.|  
|[replace\_copy\_if](../Topic/replace_copy_if.md)|Examina cada elemento de un intervalo de origen y lo reemplaza si satisface un predicado especificado y copia el resultado a un nuevo intervalo de destino.|  
|[replace\_if](../Topic/replace_if.md)|Examina cada elemento de un intervalo y lo reemplaza si satisface un predicado especificado.|  
|[reverse](../Topic/reverse.md)|Invierte el orden de los elementos dentro de un intervalo.|  
|[reverse\_copy](../Topic/reverse_copy.md)|Invierte el orden de los elementos dentro de un intervalo de origen mientras los copia a un intervalo de destino|  
|[rotate](../Topic/rotate.md)|Intercambia los elementos de dos intervalos adyacentes.|  
|[rotate\_copy](../Topic/rotate_copy.md)|Intercambia los elementos de dos intervalos adyacentes dentro de un intervalo de origen y copia el resultado a un intervalo de destino.|  
|[search](../Topic/search.md)|Busca la primera aparición de una secuencia dentro de un intervalo de destino cuyos elementos son iguales que los de una secuencia determinada de elementos o cuyos elementos son equivalentes según lo especificado por un predicado binario a los elementos de la secuencia especificada.|  
|[search\_n](../Topic/search_n.md)|Busca la primera subsecuencia de un intervalo en la que un número especificado de elementos tienen un valor determinado o una relación con ese valor según lo especificado por un predicado binario.|  
|[set\_difference](../Topic/set_difference.md)|Agrupa todos los elementos que pertenecen a un intervalo de origen ordenado, pero no a un segundo intervalo de origen ordenado, en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[set\_intersection](../Topic/set_intersection.md)|Agrupa todos los elementos que pertenecen a ambos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[set\_symmetric\_difference](../Topic/set_symmetric_difference.md)|Agrupa todos los elementos que pertenecen a uno, pero no a ambos, de los intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[set\_union](../Topic/set_union.md)|Agrupa todos los elementos que pertenecen al menos a uno de los dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[sort](../Topic/sort.md)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario.|  
|[shuffle](../Topic/std::shuffle.md)|Ordena aleatoriamente \(reordena\) elementos de un rango determinado usando un generador de números aleatorios.|  
|[sort\_heap](../Topic/sort_heap.md)|Convierte un montón en un intervalo ordenado.|  
|[stable\_partition](../Topic/stable_partition.md)|Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen, conservando el orden relativo de los elementos equivalentes.|  
|[stable\_sort](../Topic/stable_sort.md)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de los elementos equivalentes.|  
|[swap](../Topic/swap.md)|Intercambia los valores de los elementos entre dos tipos de objetos, asignando el contenido del primer objeto al segundo objeto y el contenido del segundo al primero.|  
|[swap\_ranges](../Topic/swap_ranges.md)|Intercambia los elementos de un intervalo con los elementos de otro intervalo del mismo tamaño.|  
|[transform](../Topic/transform.md)|Aplica un objeto de función especificado a cada elemento de un intervalo de origen o a un par de elementos de dos intervalos de origen y copia los valores devueltos del objeto de función a un intervalo de destino.|  
|[unique](../Topic/unique%20\(%3Calgorithm%3E\).md)|Quita los elementos duplicados adyacentes entre sí en un intervalo especificado.|  
|[unique\_copy](../Topic/unique_copy.md)|Copia los elementos de un intervalo de origen a un intervalo de destino salvo los elementos duplicados que son adyacentes entre sí.|  
|[upper\_bound](../Topic/upper_bound.md)|Busca la posición del primer elemento de un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)