---
title: Funciones &lt;random&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 5b0cd634dad099669d803d4a2717fc9198151781
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954163"
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

*RealType* tipo integral de punto flotante. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

*Bits* el generador de números aleatorios.

*Gen* el generador de números aleatorios.

### <a name="remarks"></a>Comentarios

Las llamadas de función de plantilla `operator()` de *Gen* varias veces y empaqueta los valores devueltos en un valor de punto flotante `x` typu *RealType* hasta reunir el número especificado bits de mantisa en `x`. El número especificado es menor de *Bits* (que debe ser distinto de cero) y el número total de bits de mantisa en *RealType*. La primera llamada proporciona los bits de orden más bajo. La función devuelve `x`.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
