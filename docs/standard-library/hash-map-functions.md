---
title: Funciones de &lt;hash_map&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 12ceb799ccf0944b8f0e8d48975da25c39f22505
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100955"
---
# <a name="lthashmapgt-functions"></a>Funciones de &lt;hash_map&gt;

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>  swap (hash_map)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).

Intercambia los elementos de dos objetos hash_map.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El objeto hash_map cuyos elementos son van a intercambiar con los del mapa *izquierdo*.

*left*<br/>
El objeto hash_map cuyos elementos son van a intercambiar con los del mapa *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en la clase contenedora hash_map para ejecutar la función miembro `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template \<class T> void swap(T&, T&)** del archivo de encabezado de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

## <a name="swap"></a>  swap

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multimap](../standard-library/unordered-multimap-class.md).

Intercambia los elementos de dos objetos hash_multimap.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El objeto hash_multimap cuyos elementos son van a intercambiar con los del mapa *izquierdo*.

*left*<br/>
El objeto hash_multimap cuyos elementos son van a intercambiar con los del mapa *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en la clase contenedora hash_multimap para ejecutar la función miembro `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`. Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template \<class T> void swap(T&, T&)** del archivo de encabezado de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

## <a name="see-also"></a>Vea también

[<hash_map>](../standard-library/hash-map.md)<br/>
