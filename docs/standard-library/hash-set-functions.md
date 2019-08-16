---
title: Funciones de &lt;hash_set&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 2fbc05c16ba6629397bbb07bab30cb9315a16e1f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448593"
---
# <a name="lthashsetgt-functions"></a>Funciones de &lt;hash_set&gt;

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  swap

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Intercambia los elementos de dos objetos hash_set.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*correcta*\
Hash_set que proporciona los elementos que se van a intercambiar o el hash_set cuyos elementos se van a intercambiar con los de la hash_set *izquierda*.

*salido*\
Hash_set cuyos elementos se van a intercambiar con los del *derecho*hash_set.

### <a name="remarks"></a>Comentarios

La `swap` función de plantilla es un algoritmo especializado en la clase contenedora hash_set para ejecutar la `left.`función miembro`right` [swap](../standard-library/hash-set-class.md#swap)(). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

**template \<class T> void swap(T&, T&),**

de la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código de la clase miembro [hash_set::swap](../standard-library/hash-set-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Intercambia los elementos de dos objetos hash_multiset.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*correcta*\
Hash_multiset que proporciona los elementos que se van a intercambiar o el hash_multiset cuyos elementos se van a intercambiar con los de la hash_multiset *izquierda*.

*salido*\
Hash_multiset cuyos elementos se van a intercambiar con los del *derecho*hash_multiset.

### <a name="remarks"></a>Comentarios

La `swap` función de plantilla es un algoritmo especializado en la clase contenedora hash_multiset para ejecutar la `left.`función miembro`right` [swap](../standard-library/hash-multiset-class.md#swap)(). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

**template \<class T> void swap(T&, T&),**

de la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código de la clase miembro [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="see-also"></a>Vea también

[<hash_set>](../standard-library/hash-set.md)
