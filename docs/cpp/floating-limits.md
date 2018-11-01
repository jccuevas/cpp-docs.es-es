---
title: Límites flotantes
ms.date: 08/03/2018
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
ms.openlocfilehash: cead21c9a66dbc54b46b1c9f8083022a59e80295
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469988"
---
# <a name="floating-limits"></a>Límites flotantes

**Específicos de Microsoft**

En la tabla siguiente se hace una lista de los límites de los valores de las constantes de punto flotante. Estos límites también se definen en el archivo de encabezado estándar \<float.h >.

## <a name="limits-on-floating-point-constants"></a>Límites en constantes de punto flotante

|Constante|Significado|Valor|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|Número de dígitos, q, tal que un número de punto flotante con q dígitos decimales se puede redondear en una representación de punto flotante y se puede restablecer sin pérdida de precisión.|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|Número positivo menor x, tal que x + 1,0 no es igual a 1,0.|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|Número de dígitos en la base especificada por `FLT_RADIX` en el significado de punto flotante. La base es 2. por lo tanto, estos valores especifican los bits.|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|Máximo número de punto flotante que se puede representar.|3.402823466e+38F<br/>1.7976931348623158e+308<br/>1.7976931348623158e+308|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|Entero máximo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|Entero máximo tal que `FLT_RADIX` elevado a dicho número es un número de punto flotante que se puede representar.|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|Valor positivo mínimo.|1.175494351e-38F<br/>2.2250738585072014e-308<br/>2.2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|Entero negativo mínimo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|Entero negativo mínimo tal que `FLT_RADIX` elevado a dicho número es un número de punto flotante que se puede representar.|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|Base de representación de exponente.|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|Modo de redondeo para la adición de punto flotante.|1 (próximo)<br/>1 (próximo)<br/>1 (próximo)|

> [!NOTE]
>  La información de la tabla puede ser diferente en versiones futuras del producto.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Límites de enteros](../cpp/integer-limits.md)
