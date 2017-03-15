---
title: Enumeraciones &lt;limits&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e0f4b6ca5d11207787f9ff4f27b21dbbc78080c0
ms.lasthandoff: 02/24/2017

---
# <a name="ltlimitsgt-enums"></a>Enumeraciones &lt;limits&gt;
|||  
|-|-|  
|[Enumeración float_denorm_style](#float_denorm_style_enumeration)|[Enumeración float_round_style](#float_round_style_enumeration)|  
  
##  <a name="a-namefloatdenormstyleenumerationa--floatdenormstyle-enumeration"></a><a name="float_denorm_style_enumeration"></a>  Enumeración float_denorm_style  
 La enumeración describe los diversos métodos que puede elegir una implementación para representar un valor de punto flotante no normalizado (un valor demasiado pequeño para representarlo como un valor normalizado):  
  
```
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```  
  
### <a name="return-value"></a>Valor devuelto  
 La enumeración devuelve:  
  
- **denorm_indeterminate** si no se puede determinar en tiempo de traducción la presencia o la ausencia de formularios no normalizados.  
  
- **denorm_absent** si no hay presentes formularios no normalizados.  
  
- **denorm_present** si hay presentes formularios no normalizados.  
  
### <a name="example"></a>Ejemplo  
  Vea [numeric_limits:: has_denorm](../standard-library/numeric-limits-class.md#numeric_limits__has_denorm) para obtener un ejemplo del acceso a los valores de esta enumeración.  
  
##  <a name="a-namefloatroundstyleenumerationa--floatroundstyle-enumeration"></a><a name="float_round_style_enumeration"></a>  Enumeración float_round_style  
 La enumeración describe los diversos métodos que puede elegir una implementación para redondear un valor de punto flotante a un valor entero.  
  
```
enum float_round_style {    
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```  
  
### <a name="return-value"></a>Valor devuelto  
 La enumeración devuelve:  
  
- **round_indeterminate** si no se puede determinar el método de redondeo.  
  
- **round_toward_zero** si se redondea hacia cero.  
  
- **round_to_nearest** si se redondea al entero más próximo.  
  
- **round_toward_infinity** si se redondea para evitar el cero.  
  
- **round_toward_neg_infinity** si se redondea al entero más negativo.  
  
### <a name="example"></a>Ejemplo  
  Vea [numeric_limits::round_style](../standard-library/numeric-limits-class.md#numeric_limits__round_style) para obtener un ejemplo del acceso a los valores de esta enumeración.  
  
## <a name="see-also"></a>Vea también  
 [\<limits>](../standard-library/limits.md)




