---
title: "algorithm (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "<cliext/algorithm>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<algorithm> (encabezado) [STL/CLR]"
  - "<cliext/algorithm> (encabezado) [STL/CLR]"
  - "funciones de algoritmo [STL/CLR]"
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# algorithm (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las funciones de la plantilla de contenedor de STL\/CLR que realizan algoritmos.  
  
## Sintaxis  
  
```  
#include <cliext/algorithm>  
```  
  
## Funciones  
  
|Función|Descripción|  
|-------------|-----------------|  
|[adjacent\_find](../dotnet/adjacent-find-stl-clr.md)|Buscar dos elementos adyacentes que son iguales.|  
|[binary\_search](../dotnet/binary-search-stl-clr.md)|Comprueba si una secuencia ordenada contiene un valor especificado.|  
|[copy](../dotnet/copy-stl-clr.md)|Copia los valores de un intervalo de origen a un rango de destino, iterando hacia delante.|  
|[copy\_backward](../dotnet/copy-backward-stl-clr.md)|Copia los valores de un intervalo de origen a un rango de destino, iterando en la dirección inversa.|  
|[count](../dotnet/count-stl-clr.md)|Devuelve el número de elementos en un intervalo cuya coincidencia de los valores un valor especificado.|  
|[count\_if](../dotnet/count-if-stl-clr.md)|Devuelve el número de elementos en un intervalo cuya coincidencia de los valores una condición especificada.|  
|[equal](../dotnet/equal-stl-clr.md)|Compara dos intervalos, elemento por elemento.|  
|[equal\_range](../dotnet/equal-range-stl-clr.md)|Busca una secuencia ordenada de valores y devuelve dos posiciones que delimitan un subsequence de valores que son todas igual a un elemento determinado.|  
|[relleno](../dotnet/fill-stl-clr.md)|Asigna el mismo valor nuevo a cada elemento del intervalo especificado.|  
|[fill\_n](../dotnet/fill-n-stl-clr.md)|Asigna un nuevo valor a un número especificado de elementos en un intervalo que comienza por un elemento determinado.|  
|[buscar](../dotnet/find-stl-clr.md)|Devuelve la posición de la primera aparición de un valor especificado.|  
|[find\_end](../dotnet/find-end-stl-clr.md)|Devuelve el subsequence pasado de un intervalo que sea idéntico a una secuencia especificada.|  
|[find\_first\_of](../dotnet/find-first-of-stl-clr.md)|Busca un intervalo para la primera aparición de un intervalo determinado de elementos.|  
|[find\_if](../dotnet/find-if-stl-clr.md)|Devuelve la posición del primer elemento de una secuencia de valores donde el elemento cumple una condición especificada.|  
|[for\_each](../dotnet/for-each-stl-clr.md)|Se aplica un objeto especificado de la función a cada elemento de una secuencia de valores y devuelve el objeto function.|  
|[generar](../dotnet/generate-stl-clr.md)|Asigna los valores generados por un objeto de función a cada elemento de una secuencia de valores.|  
|[generate\_n](../dotnet/generate-n-stl-clr.md)|Asigna los valores generados por un objeto de función a un número especificado de elementos.|  
|[includes](../dotnet/includes-stl-clr.md)|Prueba si un intervalo ordenados contiene todos los elementos en un intervalo ordenados segundo.|  
|[inplace\_merge](../dotnet/inplace-merge-stl-clr.md)|Combina los elementos de dos intervalos ordenados consecutivos en un único intervalo ordenados.|  
|[iter\_swap](../dotnet/iter-swap-stl-clr.md)|Los intercambios dos valores se refirieron por un par de iteradores especificados.|  
|[lexicographical\_compare](../dotnet/lexicographical-compare-stl-clr.md)|Compara dos secuencias, elemento por elemento, identifica qué secuencia es menor de los dos.|  
|[lower\_bound](../dotnet/lower-bound-stl-clr.md)|Encuentra la posición del primer elemento de una secuencia ordenada de valores que tiene un valor mayor o igual que un valor especificado.|  
|[make\_heap](../dotnet/make-heap-stl-clr.md)|Convierte los elementos de un intervalo especificado en una pila donde el mayor el primer elemento de la pila.|  
|[max](../dotnet/max-stl-clr.md)|Compara dos objetos y devuelve el mayor de los dos.|  
|[max\_element](../dotnet/max-element-stl-clr.md)|Encuentra el elemento más grande de una secuencia especificada de valores.|  
|[combinación](../dotnet/merge-stl-clr.md)|Combina todos los elementos de dos intervalos de origen ordenados en un rango de destino único, ordenados.|  
|[min](../dotnet/min-stl-clr.md)|Compara dos objetos y devuelve el menor de los dos.|  
|[min\_element](../dotnet/min-element-stl-clr.md)|Encuentra el elemento más pequeño de una secuencia especificada de valores.|  
|[mismatch](../dotnet/mismatch-stl-clr.md)|Compara el elemento de dos intervalos para el elemento y devuelve la primera posición donde una diferencia aparece.|  
|[next\_permutation](../dotnet/next-permutation-stl-clr.md)|Reorganiza los elementos en un intervalo de modo que el orden original se reemplaza por la mayor permutación lexicográficamente siguiente si existe.|  
|[nth\_element](../dotnet/nth-element-stl-clr.md)|Las particiones una secuencia de elementos, correctamente situando el elemento th de `n`de la secuencia de modo que todos los elementos delante de ella menor o igual que él y todos los elementos que lo siguen son mayor o igual que.|  
|[partial\_sort](../dotnet/partial-sort-stl-clr.md)|Organiza un número especificado de elementos más pequeños de un intervalo en nondescending petición.|  
|[partial\_sort\_copy](../dotnet/partial-sort-copy-stl-clr.md)|Copia los elementos de un intervalo de origen en un rango de destino para que los elementos del intervalo de origen están ordenados.|  
|[partition](../dotnet/partition-stl-clr.md)|Organiza los elementos en un intervalo de forma que los elementos que satisfacen un predicado unario preceden a los que no puedan para satisfacerlo.|  
|[pop\_heap](../dotnet/pop-heap-stl-clr.md)|Mueve el elemento mayor de delante de una pila hasta el final y después forma una nueva pila de los elementos restantes.|  
|[prev\_permutation](../dotnet/prev-permutation-stl-clr.md)|Reordena una secuencia de elementos para que el orden original se reemplaza por la mayor permutación lexicográficamente anterior si existe.|  
|[push\_heap](../dotnet/push-heap-stl-clr.md)|Agrega un elemento que está al final de un intervalo una pila existente que se compone de los elementos anteriores en el intervalo.|  
|[random\_shuffle](../dotnet/random-shuffle-stl-clr.md)|¡Reorganiza una secuencia de elementos de `N` en un intervalo en uno de `N`\! organizaciones posibles seleccionadas al azar.|  
|[quitar](../dotnet/remove-stl-clr.md)|Elimina un valor especificado de un intervalo determinado sin perturbar el orden de los elementos restantes y devuelve el final de un nuevo intervalo libre value especificado.|  
|[remove\_copy](../dotnet/remove-copy-stl-clr.md)|Copia los elementos de un intervalo de origen a un rango de destino, excepto en que los elementos del valor especificado no se copian, sin perturbar el orden de los elementos restantes.|  
|[remove\_copy\_if](../dotnet/remove-copy-if-stl-clr.md)|Copia los elementos de un intervalo de origen a un rango de destino, excepto los que satisfacen un predicado, sin perturbar el orden de los elementos restantes.|  
|[remove\_if](../dotnet/remove-if-stl-clr.md)|Elimina los elementos que cumplen un predicado de un intervalo determinado sin perturbar el orden de los elementos restantes. .|  
|[reemplazar](../dotnet/replace-stl-clr.md)|Reemplaza los elementos de un intervalo que coinciden con un valor especificado con un nuevo valor.|  
|[replace\_copy](../dotnet/replace-copy-stl-clr.md)|Copia los elementos de un intervalo de origen a un rango de destino, reemplazando los elementos que coinciden con un valor especificado con un nuevo valor.|  
|[replace\_copy\_if](../dotnet/replace-copy-if-stl-clr.md)|Examina cada elemento en un intervalo de origen y reemplácela si satisface un predicado especificado al copiar el resultado en un nuevo intervalo de destino.|  
|[replace\_if](../dotnet/replace-if-stl-clr.md)|Examina cada elemento en un intervalo y reemplácela si satisface el predicado especificado.|  
|[reverse](../dotnet/reverse-stl-clr.md)|Invierte el orden de los elementos dentro de un intervalo.|  
|[reverse\_copy](../dotnet/reverse-copy-stl-clr.md)|Invierte el orden de los elementos dentro de un intervalo de origen mientras la copia en un intervalo de destino.|  
|[rotate](../dotnet/rotate-stl-clr.md)|Cambie los elementos en dos intervalos adyacentes.|  
|[rotate\_copy](../dotnet/rotate-copy-stl-clr.md)|Cambie los elementos en dos intervalos adyacentes dentro de un intervalo de origen y copia el resultado a un rango de destino.|  
|[search](../dotnet/search-stl-clr.md)|Buscar la primera aparición de una secuencia dentro de un intervalo de destino cuyos elementos son iguales a los de una secuencia determinada de elementos o cuyos elementos son equivalentes en cierto modo especificados por un predicado binario a los elementos de la secuencia especificada.|  
|[search\_n](../dotnet/search-n-stl-clr.md)|Buscar el primer subsequence de un intervalo que de un número especificado de elementos que tienen un valor determinado o una relación a ese valor según lo especificado por un predicado binario.|  
|[set\_difference](../dotnet/set-difference-stl-clr.md)|Une todos los elementos que pertenecen a un intervalo de origen ordenada, pero no a un segundo tamaño el intervalo de origen, en un rango de destino único, ordenados, donde el criterio de ordenación se puede especificar por un predicado binario.|  
|[set\_intersection](../dotnet/set-intersection-stl-clr.md)|Une todos los elementos que pertenecen a los dos intervalos de origen ordenados en un rango de destino único, ordenados, donde el criterio de ordenación se puede especificar por un predicado binario.|  
|[set\_symmetric\_difference](../dotnet/set-symmetric-difference-stl-clr.md)|Une todos los elementos que pertenecen a uno, pero no ambos, intervalos de origen ordenados en un único, ajusta el intervalo de destino, donde el criterio de ordenación se puede especificar por un predicado binario.|  
|[set\_union](../dotnet/set-union-stl-clr.md)|Une todos los elementos que pertenecen al menos uno de dos intervalos de origen ordenados en un rango de destino único, ordenados, donde el criterio de ordenación se puede especificar por un predicado binario.|  
|[ordenar](../dotnet/sort-stl-clr.md)|Organiza los elementos en un intervalo especificado en nondescending petición o según un criterio de ordenación especificado por un predicado binario.|  
|[sort\_heap](../dotnet/sort-heap-stl-clr.md)|Convierte un montón en un intervalo ordenados.|  
|[stable\_partition](../dotnet/stable-partition-stl-clr.md)|Ordena elementos en un intervalo en dos conjuntos disjuntos, con los elementos satisfaciendo un predicado unario que precede a los que no puedan para satisfacerlo, conservando el orden relativo de elementos equivalentes.|  
|[stable\_sort](../dotnet/stable-sort-stl-clr.md)|Organiza los elementos en un intervalo especificado en nondescending petición o según un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de elementos equivalentes.|  
|[swap](../dotnet/swap-stl-clr.md)|Cambie los valores de los elementos entre dos tipos de objetos, asignando el contenido del primer objeto el segundo objeto y el contenido de segundos al primer.|  
|[swap\_ranges](../dotnet/swap-ranges-stl-clr.md)|Cambie los elementos de un intervalo con elementos de otro, como \- intervalo ordenados.|  
|[transform](../dotnet/transform-stl-clr.md)|Se aplica un objeto especificado de la función a cada elemento de un intervalo de origen o un par de elementos de dos intervalos de origen y copia los valores devueltos del objeto function en un rango de destino.|  
|[Unique](../dotnet/unique-stl-clr.md)|Quita los elementos duplicados que se adyacente a uno para en un intervalo especificado.|  
|[unique\_copy](../dotnet/unique-copy-stl-clr.md)|Copia los elementos de un intervalo de origen en un rango de destino salvo los elementos duplicados que se adyacente a sí.|  
|[upper\_bound](../dotnet/upper-bound-stl-clr.md)|Encuentra la posición del primer elemento en un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)