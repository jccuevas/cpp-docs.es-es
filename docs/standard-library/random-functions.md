---
title: Funciones &lt;random&gt;
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 87b640d4f3aa3fbfa23ad5603d84102301e71ea4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240383"
---
# <a name="ltrandomgt-functions"></a>Funciones &lt;random&gt;

## <a name="generate_canonical"></a> generate_canonical

Especifica un valor de punto flotante de una secuencia aleatoria.

> [!NOTE]
> La norma ISO C++ indica que esta función debe devolver valores dentro del intervalo [ `0`, `1`). Visual Studio todavía no cumple plenamente esta limitación. Use [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md) como solución provisional para generar valores en este intervalo.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parámetros

*RealType*\
Tipo integral de punto flotante. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

*Bits*\
Generador de números aleatorios.

*Gen*\
Generador de números aleatorios.

### <a name="remarks"></a>Comentarios

Las llamadas de función de plantilla `operator()` de *Gen* varias veces y empaqueta los valores devueltos en un valor de punto flotante `x` typu *RealType* hasta reunir el número especificado bits de mantisa en `x`. El número especificado es menor de *Bits* (que debe ser distinto de cero) y el número total de bits de mantisa en *RealType*. La primera llamada proporciona los bits de orden más bajo. La función devuelve `x`.
