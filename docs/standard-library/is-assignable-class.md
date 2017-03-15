---
title: Clase is_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_assignable
- std.is_assignable
- std::is_assignable
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 208853a8e173797a37da60a824d06341e279ea34
ms.lasthandoff: 02/24/2017

---
# <a name="isassignable-class"></a>Clase is_assignable
Comprueba si un valor de tipo `From` se puede asignar a un tipo `To`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class To, class From>  
struct is_assignable;
```  
  
#### <a name="parameters"></a>Parámetros  
 Para  
 El tipo del objeto que recibe la asignación.  
  
 De  
 El tipo del objeto que proporciona el valor.  
  
## <a name="remarks"></a>Comentarios  
 La expresión no evaluada `declval<To>() = declval<From>()` debe tener un formato correcto. Tanto `From` como `To` deben ser tipos completos, `void` o matrices de límite desconocido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




