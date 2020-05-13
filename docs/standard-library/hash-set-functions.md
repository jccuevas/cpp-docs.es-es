---
title: Funciones de &lt;hash_set&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: d7df6b3c5dc0d0d493d17b3e9995bc4758ffd6d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370584"
---
# <a name="lthash_setgt-functions"></a>Funciones de &lt;hash_set&gt;

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a><a name="swap"></a>Intercambio

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Intercambia los elementos de dos objetos hash_set.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El hash_set que proporciona los elementos a intercambiar, o el hash_set cuyos elementos deben intercambiarse con los de la hash_set *izquierda.*

*Izquierda*\
La hash_set cuyos elementos deben intercambiarse con los del *derecho*hash_set .

### <a name="remarks"></a>Observaciones

La `swap` función de plantilla es un algoritmo especializado en `left.`la`right`clase contenedora hash_set para ejecutar el [intercambio](../standard-library/hash-set-class.md#swap)de función miembro ( ). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

**template \<class T> void swap(T&, T&),**

en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código de la clase miembro [hash_set::swap](../standard-library/hash-set-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a>intercambio (hash_multiset)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Intercambia los elementos de dos objetos hash_multiset.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El hash_multiset que proporciona los elementos a intercambiar, o el hash_multiset cuyos elementos se van a intercambiar con los de la hash_multiset *izquierda.*

*Izquierda*\
El hash_multiset cuyos elementos deben intercambiarse con los del *derecho*hash_multiset .

### <a name="remarks"></a>Observaciones

La `swap` función de plantilla es un algoritmo especializado en `left.`la`right`clase contenedora hash_multiset para ejecutar el [intercambio](../standard-library/hash-multiset-class.md#swap)de función miembro ( ). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

**template \<class T> void swap(T&, T&),**

en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código de la clase miembro [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="see-also"></a>Consulte también

[<hash_set>](../standard-library/hash-set.md)
