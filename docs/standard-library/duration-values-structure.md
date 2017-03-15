---
title: duration_values (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::duration_values
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8b0c02d4edc3a460f166cb65b312ef78337d403f
ms.lasthandoff: 02/24/2017

---
# <a name="durationvalues-structure"></a>duration_values (Estructura)
Proporciona valores concretos para el parámetro de plantilla [duration](../standard-library/duration-class.md) `Rep`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Rep>  
struct duration_values;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[duration_values::max](#duration_values__max_method)|Estático. Especifica el límite superior para un valor de tipo `Rep`.|  
|[duration_values::min](#duration_values__min_method)|Estático. Especifica el límite inferior para un valor de tipo `Rep`.|  
|[duration_values::zero](#duration_values__zero_method)|Estático. Devuelve `Rep(0)`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** chrono  
  
 **Espacio de nombres:** std::chrono  
  
##  <a name="a-namedurationvaluesmaxmethoda--durationvaluesmax"></a><a name="duration_values__max_method"></a>  duration_values::max  
 Método estático que devuelve el límite superior para los valores de tipo `Ref`.  
  
```  
static constexpr Rep max();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En efecto, devuelve `numeric_limits<Rep>::max()`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser mayor que [duration_values::zero](#duration_values__zero_method).  
  
##  <a name="a-namedurationvaluesminmethoda--durationvaluesmin"></a><a name="duration_values__min_method"></a>  duration_values::min  
 Método estático que devuelve el límite inferior para valores de tipo `Ref`.  
  
```  
static constexpr Rep min();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En efecto, devuelve `numeric_limits<Rep>::lowest()`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser menor o igual que [duration_values::zero](#duration_values__zero_method).  
  
##  <a name="a-namedurationvalueszeromethoda--durationvalueszero"></a><a name="duration_values__zero_method"></a>  duration_values::zero  
 Devuelve `Rep(0)`.  
  
```  
static constexpr Rep zero();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe representar el infinito aditivo.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)


