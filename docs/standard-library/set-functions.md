---
title: Funciones &lt;set&gt;
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: 3873a85218c738b3a9693926e064a10b82a553c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412623"
---
# <a name="ltsetgt-functions"></a>Funciones &lt;set&gt;

|||
|-|-|
|[swap (mapa)](#swap)|[swap (conjunto mútiple)](#swap_multiset)|

## <a name="swap"></a>  swap  (mapa)

Intercambia los elementos de dos conjuntos.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El conjunto que proporciona los elementos que se van a intercambiar o el conjunto cuyos elementos se van a intercambiar con los del conjunto *izquierdo*.

*left*<br/>
El conjunto cuyos elementos se van a intercambiar con los del conjunto *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en la clase contenedora establecida para ejecutar la función miembro `left.` [intercambio](../standard-library/set-class.md#swap)(`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

`template` \< **classT**> **void swap**( **T&**, **T&**)

en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la clase miembro [set::swap](../standard-library/set-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="swap_multiset"></a>  swap  (conjunto mútiple)

Intercambia los elementos de dos conjuntos mútiples.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El conjunto múltiple que proporciona los elementos deben intercambiar o el conjunto mútiple cuyos elementos se van a intercambiar con los de la clase multiset *izquierdo*.

*left*<br/>
El conjunto mútiple cuyos elementos se van a intercambiar con los de la clase multiset *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en el conjunto múltiple de clase de contenedor para ejecutar la función miembro `left.` [intercambio](../standard-library/multiset-class.md#swap)(`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

`template` \< **classT**> **void swap**( **T&**, **T&**)

en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la clase miembro [multiset::swap](../standard-library/multiset-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="see-also"></a>Vea también

[\<set>](../standard-library/set.md)<br/>
