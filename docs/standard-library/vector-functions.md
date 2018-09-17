---
title: Funciones de &lt;vector&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: 71594b225c950714d8b9aba169e68804033c93a2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700757"
---
# <a name="ltvectorgt-functions"></a>Funciones de &lt;vector&gt;


## <a name="swap"></a>  swap

Intercambia los elementos de dos vectores.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El vector que proporciona los elementos que se van a intercambiar o el vector cuyos elementos se van a intercambiar con los del vector *izquierdo*.

*left*<br/>
El vector cuyos elementos se van a intercambiar con los del vector *derecho*.

### <a name="remarks"></a>Comentarios

La función de plantilla es un algoritmo especializado en el vector de clase de contenedor para ejecutar la función miembro `left`. [Vector:: swap](../standard-library/vector-class.md) *(derecho*). Se trata de instancias de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla **template** \< **class T**> **void swap**( **T&**, **T&**), en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

### <a name="example"></a>Ejemplo

Vea el ejemplo de código para la función miembro [vector::swap](../standard-library/vector-class.md) para obtener un ejemplo que usa la versión de la plantilla de `swap`.

## <a name="see-also"></a>Vea también

[\<vector>](../standard-library/vector.md)<br/>
