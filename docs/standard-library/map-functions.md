---
title: Funciones de &lt;map&gt;
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 6c3480e9ffbbab46a42ae790d8b70afbcd823457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517304"
---
# <a name="ltmapgt-functions"></a>Funciones de &lt;map&gt;

|||
|-|-|
|[swap (mapa)](#swap)|[swap (mapa múltiple)](#swap_multimap)|

## <a name="swap_multimap"></a>  swap  (mapa)

Intercambia los elementos de dos mapas.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El mapa que proporciona los elementos deben intercambiar o mapa cuyos elementos se van a intercambiar con los del mapa *izquierdo*.

*left*<br/>
Mapa cuyos elementos se van a intercambiar con los del mapa *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en la clase contenedora de mapa para ejecutar la función miembro `left`.[ intercambio](../standard-library/map-class.md#swap)( `right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template** \< **class T**> **void swap**( **T&**, **T&**), en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la función miembro [map::swap](../standard-library/map-class.md#swap) para obtener un ejemplo del uso de la versión de la plantilla de `swap`.

## <a name="swap"></a>  swap  (mapa múltiple)

Intercambia los elementos de dos mapas múltiples.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
La asignación múltiple que proporciona los elementos deben intercambiar o el mapa múltiple cuyos elementos se van a intercambiar con los del mapa múltiple *izquierdo*.

*left*<br/>
El mapa múltiple cuyos elementos se van a intercambiar con los del mapa múltiple *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en la clase contenedora de mapa para ejecutar en el mapa múltiple de clase de contenedor para ejecutar la función miembro `left`.[ intercambio](../standard-library/multimap-class.md#swap) (`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template** \< **class T**> **void swap**( **T&**, **T&**), en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la función miembro [multimap::swap](../standard-library/multimap-class.md#swap) para obtener un ejemplo del uso de la versión de la plantilla de `swap`.

## <a name="see-also"></a>Vea también

[\<map>](../standard-library/map.md)<br/>
