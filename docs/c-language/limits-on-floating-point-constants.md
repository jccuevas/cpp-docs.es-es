---
title: "Límites en constantes de punto flotante | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 92d89d08fdcd786e665b3ad40e3317f3e24d7a75
ms.lasthandoff: 04/01/2017

---
# <a name="limits-on-floating-point-constants"></a>Límites en constantes de punto flotante
**Específicos de Microsoft**  
  
 Los límites de los valores de las constantes de punto flotante se proporcionan en la tabla siguiente. El archivo de encabezado FLOAT.H contiene esta información.  
  
### <a name="limits-on-floating-point-constants"></a>Límites en constantes de punto flotante  
  
|Constante|Significado|Valor|  
|--------------|-------------|-----------|  
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|Número de dígitos, *q*, tal que un número de punto flotante con *q* dígitos decimales se puede redondear en una representación de punto flotante y se puede restablecer sin pérdida de precisión.|6<br />15<br />15|  
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|Número positivo menor *x*, tal que *x* + 1,0 no es igual a 1,0.|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|  
|**FLT_GUARD**||0|  
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|Número de dígitos en la base especificada por **FLT_RADIX** en el significado de punto flotante. La base es 2; por consiguiente, estos valores especifican los bits.|24<br />53<br />53|  
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|Número de punto flotante máximo que se puede representar.|3.402823466e+38F<br />1.7976931348623158e+308<br />1.7976931348623158e+308|  
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|Entero máximo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|38<br />308<br />308|  
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|Entero máximo tal que **FLT_RADIX** elevado a dicho número es un número de punto flotante que se puede representar.|128<br />1024<br />1024|  
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|Valor positivo mínimo.|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|  
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|Entero negativo mínimo tal que 10 elevado a dicho número es un número de punto flotante que se puede representar.|-37<br />-307<br />-307|  
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|Entero negativo mínimo tal que **FLT_RADIX** elevado a dicho número es un número de punto flotante que se puede representar.|-125<br />-1021<br />-1021|  
|**FLT_NORMALIZE**||0|  
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|Base de representación de exponente.|2<br />2<br />2|  
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|Modo de redondeo para la adición de punto flotante.|1 (próximo)<br />1 (próximo)<br />1 (próximo)|  
  
 Observe que la información de la tabla anterior puede diferir en futuras implementaciones.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Constantes de punto flotante de C](../c-language/c-floating-point-constants.md)
