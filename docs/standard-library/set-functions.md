---
title: Funciones &lt;set&gt;
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425170"
---
# <a name="ltsetgt-functions"></a>Funciones &lt;set&gt;

## <a name="swap"></a>intercambiar (asignar)

Intercambia los elementos de dos conjuntos.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Conjunto que proporciona los elementos que se van a intercambiar o el conjunto cuyos elementos se van a intercambiar con los del conjunto *izquierdo*.

\ *izquierda*
Conjunto cuyos elementos se van a intercambiar con los del conjunto *derecho*.

### <a name="remarks"></a>Observaciones

La función de plantilla es un algoritmo especializado en la clase de contenedor establecida para ejecutar la función miembro `left.`[swap](../standard-library/set-class.md#swap)(`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

`template` \< **classt**> **void swap**( **t &** , **t &** )

de la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la clase miembro [set::swap](../standard-library/set-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="swap_multiset"></a>swap (MultiSet)

Intercambia los elementos de dos conjuntos mútiples.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Conjunto múltiple que proporciona los elementos que se van a intercambiar o el conjunto múltiple cuyos elementos se van a intercambiar con los del conjunto múltiple *izquierdo*.

\ *izquierda*
Conjunto múltiple cuyos elementos se van a intercambiar con los del *derecho*de conjunto múltiple.

### <a name="remarks"></a>Observaciones

La función de plantilla es un algoritmo especializado en la clase contenedor MultiSet para ejecutar la función miembro `left.`[swap](../standard-library/multiset-class.md#swap)(`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

`template` \< **classt**> **void swap**( **t &** , **t &** )

de la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la clase miembro [multiset::swap](../standard-library/multiset-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.
