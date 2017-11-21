---
title: Clase is_destructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_destructible
dev_langs: C++
helpviewer_keywords: is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b673ae9c46479723684a22205853229f913573d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="isdestructible-class"></a>Clase is_destructible
Comprueba si el tipo se puede destruir.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
struct is_destructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` se puede destruir. En caso contrario, es false. Los tipos que se pueden destruir son tipos de referencia, tipos de objetos y tipos en los que para algún tipo `U` igual a `remove_all_extents_t<T>` el operando no evaluado `std::declval<U&>.~U()` tiene un formato correcto. Otros tipos, incluidos los tipos incompletos, `void` y los tipos de función, no se pueden destruir.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



