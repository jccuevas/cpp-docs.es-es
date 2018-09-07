---
title: Funciones de &lt;hash_set&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 5c96ac897d870e1f8dc153847797379b6720dc7b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103251"
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

*right*<br/>
El objeto hash_set que proporciona los elementos deben intercambiar o el objeto hash_set cuyos elementos se van a intercambiar con los del objeto hash_set *izquierdo*.

*left*<br/>
El objeto hash_set cuyos elementos se van a intercambiar con los del objeto hash_set *derecho*.

### <a name="remarks"></a>Comentarios

El `swap` función de plantilla es un algoritmo especializado en la clase contenedora hash_set para ejecutar la función miembro `left.` [intercambio](../standard-library/hash-set-class.md#swap)(`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

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

*right*<br/>
El objeto hash_multiset que proporciona los elementos deben intercambiar o el objeto hash_multiset cuyos elementos se van a intercambiar con los del objeto hash_multiset *izquierdo*.

*left*<br/>
El objeto hash_multiset cuyos elementos se van a intercambiar con los del objeto hash_multiset *derecho*.

### <a name="remarks"></a>Comentarios

El `swap` función de plantilla es un algoritmo especializado en la clase contenedora hash_multiset para ejecutar la función miembro `left.` [intercambio](../standard-library/hash-multiset-class.md#swap)(`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

**template \<class T> void swap(T&, T&),**

de la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código de la clase miembro [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="see-also"></a>Vea también

[<hash_set>](../standard-library/hash-set.md)<br/>
