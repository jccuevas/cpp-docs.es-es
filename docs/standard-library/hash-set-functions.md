---
title: Funciones de &lt;hash_set&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 083d928198d8d83d8a56d8a74a6204e94c86aa67
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846290"
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

`right` El hash_set proporciona los elementos deben intercambiar o hash_set cuyos elementos se van a intercambiar con los del hash_set `left`.

`left` El hash_set cuyos elementos se van a intercambiar con los del hash_set `right`.

### <a name="remarks"></a>Comentarios

La función de plantilla `swap` es un algoritmo especializado en la clase contenedora hash_set para ejecutar la función miembro `left.`[swap](../standard-library/hash-set-class.md#swap)( `right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

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

`right` El hash_multiset proporciona los elementos deben intercambiar o hash_multiset cuyos elementos se van a intercambiar con los del hash_multiset `left`.

`left` El hash_multiset cuyos elementos se van a intercambiar con los del hash_multiset `right`.

### <a name="remarks"></a>Comentarios

La función de plantilla `swap` es un algoritmo especializado en el objeto hash_multiset de la clase contenedora para ejecutar la función miembro `left.`[swap](../standard-library/hash-multiset-class.md#swap)( `right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla

**template \<class T> void swap(T&, T&),**

de la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código de la clase miembro [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) para obtener un ejemplo del uso de la versión de plantilla de `swap`.

## <a name="see-also"></a>Vea también

[<hash_set>](../standard-library/hash-set.md)<br/>
