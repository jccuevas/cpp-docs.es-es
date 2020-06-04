---
title: Funciones &lt;random&gt;
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425248"
---
# <a name="ltrandomgt-functions"></a>Funciones &lt;random&gt;

## <a name="generate_canonical"></a>generate_canonical

Especifica un valor de punto flotante de una secuencia aleatoria.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parámetros

\ *RealType*
Tipo integral de punto flotante. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

\ *bits*
Número de bits de aleatoriedad que se va a usar.

\ del *generador*
Una clase de generador de números aleatorios.

\ *gen* .
Referencia a una instancia de un generador de números aleatorios de tipo *generator*.

### <a name="remarks"></a>Observaciones

La función de plantilla llama a `operator()` de *gen* repetidamente y empaqueta los valores devueltos en un valor de punto flotante `x` de tipo *RealType* hasta que ha reunido el número especificado de bits de mantisa en `x`. El número especificado es el menor de *bits* (que debe ser distinto de cero) y el número completo de bits de mantisa en *RealType*. La primera llamada proporciona los bits de orden más bajo. La función devuelve `x`.
