---
title: algoritmo (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
dev_langs:
- C++
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 30e347905c6802e544cb9f81c045f9cc881f29fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
Define las funciones de plantilla de contenedor STL/CLR que realizan algoritmos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <cliext/algorithm>  
```  
  
## <a name="functions"></a>Funciones  
  
|Función|Descripción|  
|--------------|-----------------|  
|[adjacent_find (STL/CLR)](../dotnet/adjacent-find-stl-clr.md)|Busca dos elementos adyacentes que son iguales.|  
|[binary_search (STL/CLR)](../dotnet/binary-search-stl-clr.md)|Prueba si una secuencia ordenada contiene un valor determinado.|  
|[copy (STL/CLR)](../dotnet/copy-stl-clr.md)|Copia los valores de un intervalo de origen a un intervalo de destino, efectuar una iteración en la dirección hacia delante.|  
|[copy_backward (STL/CLR)](../dotnet/copy-backward-stl-clr.md)|Copia los valores de un intervalo de origen a un intervalo de destino, efectuar una iteración en la dirección hacia atrás.|  
|[count (STL/CLR)](../dotnet/count-stl-clr.md)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con un valor especificado.|  
|[count_if (STL/CLR)](../dotnet/count-if-stl-clr.md)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con una condición especificada.|  
|[equal (STL/CLR)](../dotnet/equal-stl-clr.md)|Compara dos intervalos, elemento por elemento.|  
|[equal_range (STL/CLR)](../dotnet/equal-range-stl-clr.md)|Busca una secuencia ordenada de valores y devuelve dos posiciones que delimitan una subsecuencia de valores que son iguales a un elemento determinado.|  
|[fill (STL/CLR)](../dotnet/fill-stl-clr.md)|Asigna el mismo valor nuevo a cada elemento de un intervalo especificado.|  
|[fill_n (STL/CLR)](../dotnet/fill-n-stl-clr.md)|Asigna un nuevo valor a un número especificado de elementos de un intervalo a partir de un elemento determinado.|  
|[find (STL/CLR)](../dotnet/find-stl-clr.md)|Devuelve la posición de la primera aparición de un valor especificado.|  
|[find_end (STL/CLR)](../dotnet/find-end-stl-clr.md)|Devuelve la última subsecuencia de un intervalo que es idéntico a una secuencia especificada.|  
|[find_first_of (STL/CLR)](../dotnet/find-first-of-stl-clr.md)|Busca un intervalo para la primera aparición de cualquiera de un intervalo determinado de elementos.|  
|[find_if (STL/CLR)](../dotnet/find-if-stl-clr.md)|Devuelve la posición del primer elemento de una secuencia de valores donde el elemento satisface una condición especificada.|  
|[for_each (STL/CLR)](../dotnet/for-each-stl-clr.md)|Aplica un objeto de función especificada a cada elemento de una secuencia de valores y devuelve el objeto de función.|  
|[generate (STL/CLR)](../dotnet/generate-stl-clr.md)|Asigna los valores generados por un objeto de función a cada elemento de una secuencia de valores.|  
|[generate_n (STL/CLR)](../dotnet/generate-n-stl-clr.md)|Asigna los valores generados por un objeto de función a un número especificado de elementos.|  
|[includes (STL/CLR)](../dotnet/includes-stl-clr.md)|Comprueba si un intervalo ordenado contiene todos los elementos de un segundo intervalo ordenado.|  
|[inplace_merge (STL/CLR)](../dotnet/inplace-merge-stl-clr.md)|Combina los elementos de dos intervalos ordenados consecutivos en un único intervalo ordenado.|  
|[iter_swap (STL/CLR)](../dotnet/iter-swap-stl-clr.md)|Intercambia dos valores a los que se hace referencia mediante un par de iteradores especificados.|  
|[lexicographical_compare (STL/CLR)](../dotnet/lexicographical-compare-stl-clr.md)|Compara dos secuencias, elemento por elemento, identificar qué secuencia es el menor de los dos.|  
|[lower_bound (STL/CLR)](../dotnet/lower-bound-stl-clr.md)|Busca la posición del primer elemento de una secuencia ordenada de valores que tiene un valor mayor o igual a un valor especificado.|  
|[make_heap (STL/CLR)](../dotnet/make-heap-stl-clr.md)|Convierte los elementos de un intervalo especificado en un montón donde el primer elemento en el montón es el más grande.|  
|[max (STL/CLR)](../dotnet/max-stl-clr.md)|Compara dos objetos y devuelve el mayor de los dos.|  
|[max_element (STL/CLR)](../dotnet/max-element-stl-clr.md)|Busca el elemento más grande de una secuencia de valores especificada.|  
|[merge (STL/CLR)](../dotnet/merge-stl-clr.md)|Combina todos los elementos de dos intervalos de origen ordenados en un intervalo de destino único, ordenado.|  
|[min (STL/CLR)](../dotnet/min-stl-clr.md)|Compara dos objetos y devuelve el menor de los dos.|  
|[min_element (STL/CLR)](../dotnet/min-element-stl-clr.md)|Busca el elemento más pequeño de una secuencia de valores especificada.|  
|[mismatch (STL/CLR)](../dotnet/mismatch-stl-clr.md)|Compara dos intervalos elemento a elemento y devuelve la primera posición donde se produce una diferencia.|  
|[next_permutation (STL/CLR)](../dotnet/next-permutation-stl-clr.md)|Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe.|  
|[nth_element (STL/CLR)](../dotnet/nth-element-stl-clr.md)|Particiones de una secuencia de elementos correctamente situando el `n`elemento de la secuencia para que todos los elementos frente a él se menor o igual a él y todos los elementos siguientes son mayores o iguales que él.|  
|[partial_sort (STL/CLR)](../dotnet/partial-sort-stl-clr.md)|Organiza un número especificado de los elementos menores de un intervalo en orden no descendente.|  
|[partial_sort_copy (STL/CLR)](../dotnet/partial-sort-copy-stl-clr.md)|Copia los elementos de un intervalo de origen a un intervalo de destino, que se ordenan los elementos desde el intervalo de origen.|  
|[partition (STL/CLR)](../dotnet/partition-stl-clr.md)|Organiza los elementos en un intervalo de modo que los elementos que cumplen un predicado unario preceden a los que no lo satisfacen.|  
|[pop_heap (STL/CLR)](../dotnet/pop-heap-stl-clr.md)|Mover el elemento más grande de la parte delantera de un montón al final y, a continuación, se forma un nuevo montón con los elementos restantes.|  
|[prev_permutation (STL/CLR)](../dotnet/prev-permutation-stl-clr.md)|Reorganiza una secuencia de elementos de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente anterior, si existe.|  
|[push_heap (STL/CLR)](../dotnet/push-heap-stl-clr.md)|Agrega un elemento que está al final de un intervalo a un montón existente que se compone de los elementos anteriores del intervalo.|  
|[random_shuffle (STL/CLR)](../dotnet/random-shuffle-stl-clr.md)|¡Reorganiza una secuencia de `N` elementos de un intervalo en una de `N`! organizaciones posibles seleccionadas aleatoriamente.|  
|[remove (STL/CLR)](../dotnet/remove-stl-clr.md)|Elimina un valor especificado de un intervalo determinado sin alterar el orden de los elementos restantes y devuelve el final de un nuevo intervalo libre del valor especificado.|  
|[remove_copy (STL/CLR)](../dotnet/remove-copy-stl-clr.md)|Copia elementos de un intervalo de origen en un intervalo de destino, excepto que no se copian los elementos de un valor especificado, sin alterar el orden de los elementos restantes.|  
|[remove_copy_if (STL/CLR)](../dotnet/remove-copy-if-stl-clr.md)|Copia los elementos de un intervalo de origen a un intervalo de destino, excepto aquellos que cumplen un predicado, sin alterar el orden de los elementos restantes.|  
|[remove_if (STL/CLR)](../dotnet/remove-if-stl-clr.md)|Elimina los elementos que cumplen un predicado de un intervalo determinado sin alterar el orden de los elementos restantes. .|  
|[replace (STL/CLR)](../dotnet/replace-stl-clr.md)|Reemplaza los elementos de un intervalo que coincide con un valor especificado con un nuevo valor.|  
|[replace_copy (STL/CLR)](../dotnet/replace-copy-stl-clr.md)|Copia los elementos de un intervalo de origen a un intervalo de destino, reemplazando los elementos que coinciden con un valor especificado con un nuevo valor.|  
|[replace_copy_if (STL/CLR)](../dotnet/replace-copy-if-stl-clr.md)|Examina cada elemento de un intervalo de origen y lo reemplaza si satisface un predicado especificado y copia el resultado a un nuevo intervalo de destino.|  
|[replace_if (STL/CLR)](../dotnet/replace-if-stl-clr.md)|Examina cada elemento de un intervalo y lo reemplaza si satisface un predicado especificado.|  
|[reverse (STL/CLR)](../dotnet/reverse-stl-clr.md)|Invierte el orden de los elementos dentro de un intervalo.|  
|[reverse_copy (STL/CLR)](../dotnet/reverse-copy-stl-clr.md)|Invierte el orden de los elementos dentro de un intervalo de origen mientras los copia a un intervalo de destino.|  
|[rotate (STL/CLR)](../dotnet/rotate-stl-clr.md)|Intercambia los elementos de dos intervalos adyacentes.|  
|[rotate_copy (STL/CLR)](../dotnet/rotate-copy-stl-clr.md)|Intercambia los elementos de dos intervalos adyacentes dentro de un intervalo de origen y copia el resultado a un intervalo de destino.|  
|[search (STL/CLR)](../dotnet/search-stl-clr.md)|Busca la primera aparición de una secuencia dentro de un intervalo de destino cuyos elementos son iguales que los de una secuencia determinada de elementos o cuyos elementos son equivalentes según lo especificado por un predicado binario a los elementos de la secuencia especificada.|  
|[search_n (STL/CLR)](../dotnet/search-n-stl-clr.md)|Busca la primera subsecuencia de un intervalo en la que un número especificado de elementos tienen un valor determinado o una relación con ese valor según lo especificado por un predicado binario.|  
|[set_difference (STL/CLR)](../dotnet/set-difference-stl-clr.md)|Agrupa todos los elementos que pertenecen a un intervalo de origen ordenado, pero no a un segundo intervalo de origen ordenado, en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[set_intersection (STL/CLR)](../dotnet/set-intersection-stl-clr.md)|Agrupa todos los elementos que pertenecen a ambos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[set_symmetric_difference (STL/CLR)](../dotnet/set-symmetric-difference-stl-clr.md)|Agrupa todos los elementos que pertenecen a uno, pero no a ambos, de los intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[set_union (STL/CLR)](../dotnet/set-union-stl-clr.md)|Agrupa todos los elementos que pertenecen al menos a uno de los dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
|[sort (STL/CLR)](../dotnet/sort-stl-clr.md)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario.|  
|[sort_heap (STL/CLR)](../dotnet/sort-heap-stl-clr.md)|Convierte un montón en un intervalo ordenado.|  
|[stable_partition (STL/CLR)](../dotnet/stable-partition-stl-clr.md)|Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen, conservando el orden relativo de los elementos equivalentes.|  
|[stable_sort (STL/CLR)](../dotnet/stable-sort-stl-clr.md)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de los elementos equivalentes.|  
|[swap (STL/CLR)](../dotnet/swap-stl-clr.md)|Intercambia los valores de los elementos entre dos tipos de objetos, asignando el contenido del primer objeto al segundo objeto y el contenido del segundo al primero.|  
|[swap_ranges (STL/CLR)](../dotnet/swap-ranges-stl-clr.md)|Intercambia los elementos de un intervalo con los elementos de otro intervalo del mismo tamaño.|  
|[transform (STL/CLR)](../dotnet/transform-stl-clr.md)|Aplica un objeto de función especificado a cada elemento de un intervalo de origen o a un par de elementos de dos intervalos de origen y copia los valores devueltos del objeto de función a un intervalo de destino.|  
|[unique (STL/CLR)](../dotnet/unique-stl-clr.md)|Quita los elementos duplicados adyacentes entre sí en un intervalo especificado.|  
|[unique_copy (STL/CLR)](../dotnet/unique-copy-stl-clr.md)|Copia los elementos de un intervalo de origen a un intervalo de destino salvo los elementos duplicados que son adyacentes entre sí.|  
|[upper_bound (STL/CLR)](../dotnet/upper-bound-stl-clr.md)|Busca la posición del primer elemento de un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/algoritmo >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)