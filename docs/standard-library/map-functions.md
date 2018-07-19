---
title: Funciones de &lt;map&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 3c6cb7d0308e4bafc531fe0baf0c5d666228c3ec
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966373"
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

*derecha* el mapa que proporciona los elementos deben intercambiar o mapa cuyos elementos se van a intercambiar con los del mapa *izquierdo*.

*izquierdo* mapa cuyos elementos se van a intercambiar con los del mapa *derecho*.

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

*derecha* la asignación múltiple que proporciona los elementos deben intercambiar o el mapa múltiple cuyos elementos se van a intercambiar con los del mapa múltiple *izquierdo*.

*izquierdo* el mapa múltiple cuyos elementos se van a intercambiar con los del mapa múltiple *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en la clase contenedora de mapa para ejecutar en el mapa múltiple de clase de contenedor para ejecutar la función miembro `left`.[ intercambio](../standard-library/multimap-class.md#swap) (`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template** \< **class T**> **void swap**( **T&**, **T&**), en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la función miembro [multimap::swap](../standard-library/multimap-class.md#swap) para obtener un ejemplo del uso de la versión de la plantilla de `swap`.

## <a name="see-also"></a>Vea también

[\<map>](../standard-library/map.md)<br/>
