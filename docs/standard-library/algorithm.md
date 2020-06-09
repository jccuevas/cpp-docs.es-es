---
title: '&lt;algorithm&gt;'
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: d36ee5ea0d38455b52cb988dc30b13d47be16e53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623849"
---
# <a name="ltalgorithmgt"></a>&lt;algorithm&gt;

Define las funciones de plantilla contenedor de la biblioteca estándar de C++ que realizan algoritmos.

## <a name="syntax"></a>Sintaxis

```cpp
(see relevant links below for specific algorithm syntax)
```

> [!NOTE]
> La \<algorithm> biblioteca también utiliza la `#include <initializer_list>` instrucción.

## <a name="remarks"></a>Observaciones

Los algoritmos de la biblioteca estándar de C++ son genéricos porque se pueden usar en diversas estructuras de datos. Las estructuras de datos en las que se pueden usar incluyen no solo las clases contenedoras de la biblioteca estándar de C++, como `vector` y `list`, sino también estructuras de datos y matrices de elementos definidas por el programa que cumplen los requisitos de un algoritmo determinado. Los algoritmos de la biblioteca estándar de C++ logran este nivel de generalidad al acceder a los elementos de un contenedor indirectamente mediante iteradores y al recorrerlos.

Los algoritmos de la biblioteca estándar de C++ procesan los intervalos de iteradores que se suelen especificar por sus posiciones inicial o final. Los intervalos a los que se hace referencia deben ser válidos en el sentido de que todos los punteros de los intervalos se deben poder desreferenciar y, dentro de las secuencias de cada intervalo, se debe poder llegar a la última posición desde la primera mediante incrementos.

Los algoritmos de la biblioteca estándar de C++ extienden las acciones que admiten las operaciones y las funciones miembro de cada contenedor de la biblioteca estándar de C++ y permiten trabajar, por ejemplo, con diferentes tipos de objetos contenedor al mismo tiempo. Se usan dos sufijos para transmitir información sobre el propósito de los algoritmos.

- El `_if` sufijo indica que el algoritmo se usa con objetos de función que operan sobre los valores de los elementos en lugar de en los propios elementos. El algoritmo `find_if` busca los elementos cuyos valores satisfacen el criterio especificado por un objeto de función y el algoritmo `find` busca un valor determinado.

- El sufijo _copy indica que el algoritmo no solo manipula los valores de los elementos, sino que también copia los valores modificados a un intervalo de destino. El algoritmo `reverse` invierte el orden de los elementos dentro de un intervalo y el algoritmo `reverse_copy` también copia el resultado a un intervalo de destino.

Los algoritmos de la biblioteca estándar de C++ se suelen clasificar en grupos que indican de alguna manera su propósito o sus requisitos. Entre ellos se incluyen algoritmos de modificación que cambian el valor de los elementos, a diferencia de los algoritmos que no son de modificación, que no lo hacen. Los algoritmos de mutación cambian el orden de los elementos, pero no los valores de sus elementos. Los algoritmos de eliminación pueden eliminar elementos de un intervalo o de una copia de un intervalo. Los algoritmos de ordenación reordenan los elementos de un intervalo de varias maneras y los algoritmos de intervalo ordenado solo actúan sobre los intervalos cuyos elementos se han ordenado de una manera determinada.

Los algoritmos numéricos de la biblioteca estándar de C++ que se proporcionan para el procesamiento numérico tienen su propio archivo [\<numeric>](numeric.md) de encabezado, y los objetos de función y los adaptadores se definen en la función de encabezado los [\<functional>](functional.md) objetos que devuelven valores booleanos se conocen como predicados. El predicado binario predeterminado es el `operator<` de comparación. En general, los elementos que se van a ordenar deben ser menores que otros comparables para que, dados dos elementos cualesquiera, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes.

### <a name="function-templates"></a>Plantillas de función

|||
|-|-|
|[adjacent_find](algorithm-functions.md#adjacent_find)|Busca dos elementos adyacentes que son iguales o cumplen una condición especificada.|
|[all_of](algorithm-functions.md#all_of)|Devuelve **verdadero** cuando una condición está presente en cada elemento del intervalo especificado.|
|[any_of](algorithm-functions.md#any_of)|Devuelve **verdadero** cuando una condición está presente al menos una vez en el intervalo de elementos especificado.|
|[binary_search](algorithm-functions.md#binary_search)|Comprueba si hay un elemento en un intervalo ordenado que sea igual a un valor especificado o equivalente a este del modo especificado por un predicado binario.|
|[Sujet](algorithm-functions.md#clamp)||
|[copy](algorithm-functions.md#copy)|Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia delante.|
|[copy_backward](algorithm-functions.md#copy_backward)|Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia atrás.|
|[copy_if](algorithm-functions.md#copy_if)|Copiar todos los elementos de un intervalo determinado que prueban **true** para una condición especificada|
|[copy_n](algorithm-functions.md#copy_n)|Copia un número especificado de elementos.|
|[count](algorithm-functions.md#count)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con un valor especificado.|
|[count_if](algorithm-functions.md#count_if)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con una condición especificada.|
|[sea](algorithm-functions.md#equal)|Compara dos intervalos elemento a elemento para ver si son iguales o equivalentes según lo especificado por un predicado binario.|
|[equal_range](algorithm-functions.md#equal_range)|Busca un par de posiciones en un intervalo ordenado; la primera es menor o equivalente a la posición de un elemento especificado y la segunda es mayor que la posición del elemento, donde el sentido de equivalencia o de ordenación empleado para establecer las posiciones en la secuencia se puede especificar con un predicado binario.|
|[relleno](algorithm-functions.md#fill)|Asigna el mismo valor nuevo a cada elemento de un intervalo especificado.|
|[fill_n](algorithm-functions.md#fill_n)|Asigna un nuevo valor a un número especificado de elementos en un intervalo que comienza con un elemento determinado.|
|[find](algorithm-functions.md#find)|Busca la posición de la primera aparición de un elemento en un intervalo que tiene un valor especificado.|
|[find_end](algorithm-functions.md#find_end)|Busca en un intervalo la última subsecuencia que es idéntica a una secuencia especificada o que es equivalente según lo especificado por un predicado binario.|
|[find_first_of](algorithm-functions.md#find_first_of)|Busca la primera aparición de cualquiera de varios valores dentro de un intervalo de destino o la primera aparición de cualquiera de varios elementos que son equivalentes según lo especificado por un predicado binario en un conjunto especificado de los elementos.|
|[find_if](algorithm-functions.md#find_if)|Busca la posición de la primera aparición de un elemento en un intervalo que cumple una condición especificada.|
|[find_if_not](algorithm-functions.md#find_if_not)|Devuelve el primer elemento del intervalo indicado que no satisface una condición.|
|[for_each](algorithm-functions.md#for_each)|Aplica un objeto de función especificado a cada elemento en un orden hacia delante dentro de un intervalo y devuelve el objeto de función.|
|[for_each_n](algorithm-functions.md#for_each_n)||
|[generate](algorithm-functions.md#generate)|Asigna los valores generados por un objeto de función a cada elemento de un intervalo.|
|[generate_n](algorithm-functions.md#generate_n)|Asigna los valores generados por un objeto de función a un número especificado de elemento de un intervalo y vuelve a la posición situada una más allá del último valor asignado.|
|[presenta](algorithm-functions.md#includes)|Prueba si un intervalo ordenado contiene todos los elementos incluidos en un segundo intervalo ordenado, donde el criterio de ordenación o equivalencia entre los elementos se pueden especificar mediante un predicado binario.|
|[inplace_merge](algorithm-functions.md#inplace_merge)|Combina los elementos de dos intervalos ordenados consecutivos en un único intervalo ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[is_heap](algorithm-functions.md#is_heap)|Devuelve **true** si los elementos del intervalo especificado forman un montón.|
|[is_heap_until](algorithm-functions.md#is_heap_until)|Devuelve **true** si el intervalo especificado forma un montón hasta el último elemento.|
|[is_partitioned](algorithm-functions.md#is_partitioned)|Devuelve **true** si todos los elementos del intervalo especificado que prueban **true** para una condición van antes que los elementos que prueban **false**.|
|[is_permutation](algorithm-functions.md#is_permutation)|Determina si los elementos de un intervalo determinado forman una permutación válida.|
|[is_sorted](algorithm-functions.md#is_sorted)|Devuelve **true** si los elementos del intervalo especificado están ordenados.|
|[is_sorted_until](algorithm-functions.md#is_sorted_until)|Devuelve **true** si los elementos del intervalo especificado están ordenados.|
|[iter_swap](algorithm-functions.md#iter_swap)|Intercambia dos valores a los que se hace referencia mediante un par de iteradores especificados.|
|[lexicographical_compare](algorithm-functions.md#lexicographical_compare)|Compara dos secuencias elemento a elemento para determinar cuál es menor de los dos.|
|[lower_bound](algorithm-functions.md#lower_bound)|Busca la posición del primer elemento en un intervalo ordenado que tiene un valor mayor o equivalente a un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[make_heap](algorithm-functions.md#make_heap)|Convierte elementos de un intervalo especificado en un montón en el que el primer elemento es el mayor y para el que se puede especificar un criterio de ordenación con un predicado binario.|
|[max](algorithm-functions.md#max)|Compara dos objetos y devuelve el mayor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[max_element](algorithm-functions.md#max_element)|Busca la primera aparición del elemento mayor en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[sin](algorithm-functions.md#merge)|Combina todos los elementos de dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[min](algorithm-functions.md#min)|Compara dos objetos y devuelve el menor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[min_element](algorithm-functions.md#min_element)|Busca la primera aparición del menor elemento en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[MinMax](algorithm-functions.md#minmax)|Compara dos parámetros de entrada y los devuelve como un par, en orden de menor a mayor.|
|[minmax_element](algorithm-functions.md#minmax_element)|Realiza el trabajo efectuado por [min_element](algorithm-functions.md#min_element) y [max_element](algorithm-functions.md#max_element) en una llamada.|
|[versiones](algorithm-functions.md#mismatch)|Compara dos intervalos elemento a elemento para ver si son iguales o equivalentes según lo especificado por un predicado binario y busca la primera posición donde se produce una diferencia.|
|[&lt;movimiento de alg &gt;](algorithm-functions.md#alg_move)|Mueve los elementos asociados a un intervalo especificado.|
|[move_backward](algorithm-functions.md#move_backward)|Mover los elementos de un iterador a otro. El movimiento comienza con el último elemento de un intervalo especificado y termina con el primer elemento de ese intervalo.|
|[next_permutation](algorithm-functions.md#next_permutation)|Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe, donde el sentido de siguiente se puede especificar con un predicado binario.|
|[none_of](algorithm-functions.md#none_of)|Devuelve **verdadero** cuando una condición nunca está presente entre los elementos del intervalo especificado.|
|[nth_element](algorithm-functions.md#nth_element)|Divide un intervalo de elementos, localizando correctamente el elemento *n*de la secuencia en el intervalo de modo que todos los elementos de delante sean menores o iguales que él y todos los elementos que lo siguen en la secuencia sean mayores o iguales que él.|
|[partial_sort](algorithm-functions.md#partial_sort)|Organiza un número especificado de los elementos menores de un intervalo en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario.|
|[partial_sort_copy](algorithm-functions.md#partial_sort_copy)|Copia los elementos de un intervalo de origen a un intervalo de destino donde los elementos de origen están ordenados por menor que u otro predicado binario especificado.|
|[partition](algorithm-functions.md#partition)|Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen.|
|[partition_copy](algorithm-functions.md#partition_copy)|Copia los elementos para los que una condición es **verdadera** para un destino y cuya condición es **falsa** en otro. Los elementos deben proceder de un intervalo especificado.|
|[partition_point](algorithm-functions.md#partition_point)|Devuelve el primer elemento del intervalo especificado que no satisface la condición. Los elementos se ordenan de forma que aquellos que satisfacen la condición están antes que los que no lo hacen.|
|[pop_heap](algorithm-functions.md#pop_heap)|Quita el elemento mayor del principio de un montón hasta la penúltima posición del intervalo y después forma un nuevo montón con los elementos restantes.|
|[prev_permutation](algorithm-functions.md#prev_permutation)|Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe, donde el sentido de siguiente se puede especificar con un predicado binario.|
|[push_heap](algorithm-functions.md#push_heap)|Agrega un elemento que está al final de un intervalo a un montón existente que se compone de los elementos anteriores del intervalo.|
|[random_shuffle](algorithm-functions.md#random_shuffle)|Reorganiza una secuencia de *N* elementos de un intervalo en una de *N*! organizaciones posibles seleccionadas aleatoriamente.|
|[remove](algorithm-functions.md#remove)|Elimina un valor especificado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.|
|[remove_copy](algorithm-functions.md#remove_copy)|Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos de un valor especificado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.|
|[remove_copy_if](algorithm-functions.md#remove_copy_if)|Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos que satisfacen un predicado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.|
|[remove_if](algorithm-functions.md#remove_if)|Elimina los elementos que cumplen un predicado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.|
|[replace](algorithm-functions.md#replace)|Examina cada elemento de un intervalo y lo reemplaza si coincide con un valor especificado.|
|[replace_copy](algorithm-functions.md#replace_copy)|Examina cada elemento de un intervalo de origen y lo reemplaza si coincide con un valor especificado y copia el resultado a un nuevo intervalo de destino.|
|[replace_copy_if](algorithm-functions.md#replace_copy_if)|Examina cada elemento de un intervalo de origen y lo reemplaza si satisface un predicado especificado y copia el resultado a un nuevo intervalo de destino.|
|[replace_if](algorithm-functions.md#replace_if)|Examina cada elemento de un intervalo y lo reemplaza si satisface un predicado especificado.|
|[viceversa](algorithm-functions.md#reverse)|Invierte el orden de los elementos dentro de un intervalo.|
|[reverse_copy](algorithm-functions.md#reverse_copy)|Invierte el orden de los elementos dentro de un intervalo de origen mientras los copia a un intervalo de destino|
|[rota](algorithm-functions.md#rotate)|Intercambia los elementos de dos intervalos adyacentes.|
|[rotate_copy](algorithm-functions.md#rotate_copy)|Intercambia los elementos de dos intervalos adyacentes dentro de un intervalo de origen y copia el resultado a un intervalo de destino.|
|[AdventureWorks](algorithm-functions.md#sample)||
|[search](algorithm-functions.md#search)|Busca la primera aparición de una secuencia dentro de un intervalo de destino cuyos elementos son iguales que los de una secuencia determinada de elementos o cuyos elementos son equivalentes según lo especificado por un predicado binario a los elementos de la secuencia especificada.|
|[search_n](algorithm-functions.md#search_n)|Busca la primera subsecuencia de un intervalo en la que un número especificado de elementos tienen un valor determinado o una relación con ese valor según lo especificado por un predicado binario.|
|[set_difference](algorithm-functions.md#set_difference)|Agrupa todos los elementos que pertenecen a un intervalo de origen ordenado, pero no a un segundo intervalo de origen ordenado, en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[set_intersection](algorithm-functions.md#set_intersection)|Agrupa todos los elementos que pertenecen a ambos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[set_symmetric_difference](algorithm-functions.md#set_symmetric_difference)|Agrupa todos los elementos que pertenecen a uno, pero no a ambos, de los intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[set_union](algorithm-functions.md#set_union)|Agrupa todos los elementos que pertenecen al menos a uno de los dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[sort](algorithm-functions.md#sort)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario.|
|[shuffle](algorithm-functions.md#shuffle)|Ordena aleatoriamente (reordena) elementos de un rango determinado usando un generador de números aleatorios.|
|[sort_heap](algorithm-functions.md#sort_heap)|Convierte un montón en un intervalo ordenado.|
|[stable_partition](algorithm-functions.md#stable_partition)|Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen, conservando el orden relativo de los elementos equivalentes.|
|[stable_sort](algorithm-functions.md#stable_sort)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de los elementos equivalentes.|
|[swap](algorithm-functions.md#swap)|Intercambia los valores de los elementos entre dos tipos de objetos, asignando el contenido del primer objeto al segundo objeto y el contenido del segundo al primero.|
|[swap_ranges](algorithm-functions.md#swap_ranges)|Intercambia los elementos de un intervalo con los elementos de otro intervalo del mismo tamaño.|
|[transformación](algorithm-functions.md#transform)|Aplica un objeto de función especificado a cada elemento de un intervalo de origen o a un par de elementos de dos intervalos de origen y copia los valores devueltos del objeto de función a un intervalo de destino.|
|[unique](algorithm-functions.md#unique)|Quita los elementos duplicados adyacentes entre sí en un intervalo especificado.|
|[unique_copy](algorithm-functions.md#unique_copy)|Copia los elementos de un intervalo de origen a un intervalo de destino salvo los elementos duplicados que son adyacentes entre sí.|
|[upper_bound](algorithm-functions.md#upper_bound)|Busca la posición del primer elemento de un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar de C++](cpp-standard-library-reference.md)
