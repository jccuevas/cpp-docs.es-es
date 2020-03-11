---
title: Funciones de &lt;map&gt;
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883970"
---
# <a name="ltmapgt-functions"></a>Funciones de &lt;map&gt;

## <a name="swap_multimap"></a>intercambiar (asignar)

Intercambia los elementos de dos mapas.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Mapa que proporciona los elementos que se van a intercambiar o la asignación cuyos elementos se van a intercambiar con los del mapa *izquierdo*.

\ *izquierda*
Asignación cuyos elementos se van a intercambiar con los del *derecho*de asignación.

### <a name="remarks"></a>Observaciones

La función de plantilla es un algoritmo especializado en la asignación de clase de contenedor para ejecutar la función miembro `left`. [swap](../standard-library/map-class.md#swap)(`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla, la **plantilla** \< **clase t**> **void swap**( **t &** , **t &** ) en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la función miembro [map::swap](../standard-library/map-class.md#swap) para obtener un ejemplo del uso de la versión de la plantilla de `swap`.

## <a name="swap"></a>swap (Multimap)

Intercambia los elementos de dos mapas múltiples.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Multimap que proporciona los elementos que se van a intercambiar o el Multimap cuyos elementos se van a intercambiar con los de la Multimap *izquierda*.

\ *izquierda*
Multimap cuyos elementos se van a intercambiar con los del *derecho*Multimap.

### <a name="remarks"></a>Observaciones

La función de plantilla es un algoritmo especializado en el mapa de la clase de contenedor que se va a ejecutar en la clase contenedora Multimap para ejecutar la función miembro `left`. [swap](../standard-library/multimap-class.md#swap) (`right`). Se trata de una instancia de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla, la **plantilla** \< **clase t**> **void swap**( **t &** , **t &** ) en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la función miembro [multimap::swap](../standard-library/multimap-class.md#swap) para obtener un ejemplo del uso de la versión de la plantilla de `swap`.
