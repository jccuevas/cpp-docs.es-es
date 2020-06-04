---
title: Enumeraciones &lt;limits&gt;
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425614"
---
# <a name="ltlimitsgt-enums"></a>Enumeraciones &lt;limits&gt;

## <a name="float_denorm_style"></a>float_denorm_style

La enumeración describe los diversos métodos que puede elegir una implementación para representar un valor de punto flotante no normalizado (un valor demasiado pequeño para representarlo como un valor normalizado):

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Valor devuelto

La enumeración devuelve:

- `denorm_indeterminate` si la presencia o ausencia de formularios no normalizados no se puede determinar en el momento de la conversión.

- `denorm_absent` si faltan formularios no normalizados.

- `denorm_present` si están presentes formularios no normalizados.

### <a name="example"></a>Ejemplo

Vea [numeric_limits:: has_denorm](../standard-library/numeric-limits-class.md#has_denorm) para obtener un ejemplo del acceso a los valores de esta enumeración.

## <a name="float_round_style"></a>float_round_style

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

- `round_indeterminate` si no se puede determinar el método de redondeo.

- `round_toward_zero` si el redondeo se redondea hacia cero.

- `round_to_nearest` si se redondea al entero más próximo.

- `round_toward_infinity` si el redondeo es distinto de cero.

- `round_toward_neg_infinity` si se redondea a un entero más negativo.

### <a name="example"></a>Ejemplo

Vea [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) para obtener un ejemplo del acceso a los valores de esta enumeración.
