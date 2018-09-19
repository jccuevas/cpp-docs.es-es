---
title: Enumeraciones &lt;limits&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 5795d146714c6eb00902518347138a98574679a8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960653"
---
# <a name="ltlimitsgt-enums"></a>Enumeraciones &lt;limits&gt;

|||
|-|-|
|[float_denorm_style](#float_denorm_style)|[float_round_style](#float_round_style)|

## <a name="float_denorm_style"></a>  Enumeración float_denorm_style

La enumeración describe los diversos métodos que puede elegir una implementación para representar un valor de punto flotante no normalizado (un valor demasiado pequeño para representarlo como un valor normalizado):

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Valor devuelto

La enumeración devuelve:

- `denorm_indeterminate` Si no se puede determinar la presencia o ausencia de formularios no normalizados en tiempo de traducción.

- `denorm_absent` Si no están presentes formularios no normalizados.

- `denorm_present` Si están presentes formularios no normalizados.

### <a name="example"></a>Ejemplo

Vea [numeric_limits:: has_denorm](../standard-library/numeric-limits-class.md#has_denorm) para obtener un ejemplo del acceso a los valores de esta enumeración.

## <a name="float_round_style"></a>  Enumeración float_round_style

La enumeración describe los diversos métodos que puede elegir una implementación para redondear un valor de punto flotante a un valor entero.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Valor devuelto

La enumeración devuelve:

- `round_indeterminate` Si no se puede determinar el método de redondeo.

- `round_toward_zero` Si el redondeo hacia cero.

- `round_to_nearest` Si redondea al entero más cercano.

- `round_toward_infinity` Si el redondeo para evitar el cero.

- `round_toward_neg_infinity` Si redondea al entero más negativo.

### <a name="example"></a>Ejemplo

Vea [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) para obtener un ejemplo del acceso a los valores de esta enumeración.

## <a name="see-also"></a>Vea también

[\<limits>](../standard-library/limits.md)<br/>
