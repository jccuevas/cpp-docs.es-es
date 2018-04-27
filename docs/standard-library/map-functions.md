---
title: Funciones de &lt;map&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
caps.latest.revision: 6
manager: ghogen
ms.openlocfilehash: 6a83feab5c477f222dc192c1c916e5cbb93e637d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

`right` La asignación que proporciona los elementos deben intercambiar o la asignación cuyos elementos se van a intercambiar con los del mapa `left`.

`left` La asignación cuyos elementos se van a intercambiar con los del mapa `right`.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en el mapa de la clase de contenedor para ejecutar la función miembro `left`.[ intercambio](../standard-library/map-class.md#swap)( `right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template** \< **class T**> **void swap**( **T&**, **T&**), en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

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

`right` La asignación múltiple proporciona los elementos deben intercambiar o la asignación múltiple cuyos elementos se van a intercambiar con los de la asignación múltiple `left`.

`left` La asignación múltiple cuyos elementos se van a intercambiar con los de la asignación múltiple `right`.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en el mapa de la clase de contenedor para ejecutar en la asignación múltiple de clase de contenedor para ejecutar la función miembro `left`.[ intercambio](../standard-library/multimap-class.md#swap) ( `right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template** \< **class T**> **void swap**( **T&**, **T&**), en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la función miembro [multimap::swap](../standard-library/multimap-class.md#swap) para obtener un ejemplo del uso de la versión de la plantilla de `swap`.

## <a name="see-also"></a>Vea también

[\<map>](../standard-library/map.md)<br/>
