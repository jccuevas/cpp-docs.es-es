---
title: vector&lt;bool&gt;::reference (Clase)
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 7930c1cd93cd05a752d4997b9480c766ee26bd99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471505"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference (Clase)

La clase `vector<bool>::reference` es una clase de proxy proporcionada por [vector\<bool> (Clase)](../standard-library/vector-bool-class.md) para simular `bool&`.

## <a name="remarks"></a>Comentarios

Se requiere una referencia simulada porque C++ no permite de forma nativa referencias directas a bits. `vector<bool>` solo utiliza un bit por elemento, al que se puede hacer referencia mediante esta clase proxy. Sin embargo, la simulación de referencia no se completa porque algunas asignaciones no son válidas. Por ejemplo, porque la dirección de la `vector<bool>::reference` objeto no se pueden tomar, el siguiente código que intenta usar `vector<bool>::operator&` no es correcta:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|Invierte el valor booleano de un elemento vector.|
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|Proporciona una conversión implícita de `vector<bool>::reference` a **bool**.|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Asigna un valor booleano a un bit o asigna el valor contenido en un elemento al que se hace referencia a un bit.|

## <a name="requirements"></a>Requisitos

**Encabezado**: \<vector>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<vector>](../standard-library/vector.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
