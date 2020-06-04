---
title: Funciones de &lt;hash_map&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 7cb2e46f19bd30e3eb313cde867c6a055cb8bca5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370611"
---
# <a name="lthash_mapgt-functions"></a>Funciones de &lt;hash_map&gt;

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a>intercambio (hash_map)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).

Intercambia los elementos de dos objetos hash_map.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El hash_map cuyos elementos se van a intercambiar con los del mapa *dejado*.

*Izquierda*\
El hash_map cuyos elementos deben intercambiarse con los del mapa *a la derecha.*

### <a name="remarks"></a>Observaciones

La función de plantilla es un algoritmo especializado en la clase contenedora hash_map para ejecutar la función miembro `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template \<class T> void swap(T&, T&)** del archivo de encabezado de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

## <a name="swap"></a><a name="swap"></a>Intercambio

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Intercambia los elementos de dos objetos hash_multimap.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El hash_multimap cuyos elementos se van a intercambiar con los del mapa a la *izquierda.*

*Izquierda*\
El hash_multimap cuyos elementos deben intercambiarse con los del mapa *a la derecha.*

### <a name="remarks"></a>Observaciones

La función de plantilla es un algoritmo especializado en la clase contenedora hash_multimap para ejecutar la función miembro `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`. Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template \<class T> void swap(T&, T&)** del archivo de encabezado de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada en cada contenedor es mucho más rápida dado que puede funcionar con la representación interna de la clase contenedora.

## <a name="see-also"></a>Consulte también

[<hash_map>](../standard-library/hash-map.md)
