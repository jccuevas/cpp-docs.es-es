---
title: "Límites flotantes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 449356b7bce3f17862919e90d7fc7e72b2d57df6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="floating-limits"></a>Límites flotantes
**Específicos de Microsoft**  
  
 En la tabla siguiente se hace una lista de los límites de los valores de las constantes de punto flotante. Estos límites también se definen en el archivo de encabezado estándar FLOAT.H.  
  
### <a name="limits-on-floating-point-constants"></a>Límites en constantes de punto flotante  
  
|Constante|Significado|Valor|  
|--------------|-------------|-----------|  
|FLT_DIG DBL_DIG LDBL_DIG|Número de dígitos, q, tal que un número de punto flotante con q dígitos decimales se puede redondear en una representación de punto flotante y se puede restablecer sin pérdida de precisión.|6 15 15|  
|FLT_EPSILON DBL_EPSILON LDBL_EPSILON|Número positivo menor x, tal que x + 1,0 no es igual a 1,0.|1, 192092896e-07F 2, 2204460492503131e-016 2, 2204460492503131e-016|  
|FLT_GUARD||0|  
|FLT_MANT_DIG DBL_MANT_DIG LDBL_MANT_DIG|Número de dígitos en la base especificada por FLT_RADIX en el significado de punto flotante. La base es 2; por lo tanto, estos valores especifican los bits.|24 53 53|  
|FLT_MAX DBL_MAX LDBL_MAX|Máximo número de punto flotante puede representar.|3,402823466e+38F 1,7976931348623158e+308 1,7976931348623158e+308|  
|FLT_MAX_10_EXP DBL_MAX_10_EXP LDBL_MAX_10_EXP|Entero máximo tal que 10 elevado a dicho número es un número de punto flotante puede representar.|38 308 308|  
|FLT_MAX_EXP DBL_MAX_EXP LDBL_MAX_EXP|Entero máximo tal que FLT_RADIX elevado a dicho número es un número de punto flotante que se puede representar.|128 1024 1024|  
|FLT_MIN DBL_MIN LDBL_MIN|Valor positivo mínimo.|1, 175494351e-38F 2, 2250738585072014E-308 2, 2250738585072014E-308|  
|FLT_MIN_10_EXP DBL_MIN_10_EXP LDBL_MIN_10_EXP|Entero negativo mínimo tal que 10 elevado a dicho número es un número de punto flotante puede representar.|-37<br /><br /> -307<br /><br /> -307|  
|FLT_MIN_EXP DBL_MIN_EXP LDBL_MIN_EXP|Entero negativo mínimo tal que FLT_RADIX elevado a dicho número es un número de punto flotante que se puede representar.|-125<br /><br /> -1021<br /><br /> -1021|  
|FLT_NORMALIZE||0|  
|FLT_RADIX _DBL_RADIX _LDBL_RADIX|Base de representación de exponente.|2 2 2|  
|FLT_ROUNDS _DBL_ROUNDS _LDBL_ROUNDS|Modo de redondeo para la adición de punto flotante.|1 (próximo) 1 (próximo) 1 (próximo)|  
  
> [!NOTE]
>  La información de la tabla puede ser diferente en versiones futuras del producto.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Límites de enteros](../cpp/integer-limits.md)