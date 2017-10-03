---
title: Clase is_move_constructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 12
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 9498029f431b287312583f78effc5197fc097fd6
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="ismoveconstructible-class"></a>Clase is_move_constructible
Comprueba si el tipo tiene un constructor de movimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
struct is_move_constructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 T  
 El tipo que se debe evaluar  
  
## <a name="remarks"></a>Comentarios  
 Predicado de tipo que da como resultado True si el tipo `T` se puede construir mediante una operación de movimiento. Este predicado es equivalente a `is_constructible<T, T&&>`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




