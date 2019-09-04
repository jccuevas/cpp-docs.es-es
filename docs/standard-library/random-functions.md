---
title: Funciones &lt;random&gt;
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273836"
---
# <a name="ltrandomgt-functions"></a>Funciones &lt;random&gt;

## <a name="generate_canonical"></a>generate_canonical

Especifica un valor de punto flotante de una secuencia aleatoria.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parámetros

*RealType*\
Tipo integral de punto flotante. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

*Parada*\
Número de bits de aleatoriedad que se va a usar.

*Generadores*\
Una clase de generador de números aleatorios.

*Group*\
Referencia a una instancia de un generador de números aleatorios de tipo *generator*.

### <a name="remarks"></a>Comentarios

La función de plantilla `operator()` llama *a de forma repetida* y empaqueta los valores devueltos en `x` un valor de punto flotante de tipo *RealType* hasta que ha reunido el `x`número especificado de bits de mantisa en. El número especificado es el menor de *bits* (que debe ser distinto de cero) y el número completo de bits de mantisa en *RealType*. La primera llamada proporciona los bits de orden más bajo. La función devuelve `x`.
