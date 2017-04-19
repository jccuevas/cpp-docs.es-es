---
title: Clase is_nothrow_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- is_nothrow_assignable
- type_traits/std::is_nothrow_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: 13
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 8f7cfa4eafda6061e503b5b8495d64c29a19eda8
ms.lasthandoff: 02/24/2017

---
# <a name="isnothrowassignable-class"></a>Clase is_nothrow_assignable
Prueba si un valor de tipo `From` se puede asignar al tipo `To` y se sabe que la asignación no se inicia.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class To, class From>  
struct is_nothrow_assignable;
```  
  
#### <a name="parameters"></a>Parámetros  
 Para  
 El tipo del objeto que recibe la asignación.  
  
 De  
 El tipo del objeto que proporciona el valor.  
  
## <a name="remarks"></a>Comentarios  
 La expresión `declval<To>() = declval<From>()` debe tener el formato correcto y el compilador debe saber que no se inicia. Tanto `From` como `To` deben ser tipos completos, `void` o matrices de límite desconocido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




