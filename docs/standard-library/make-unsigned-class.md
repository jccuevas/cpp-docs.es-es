---
title: Clase make_unsigned | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: 18
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
ms.openlocfilehash: fdd04e8b2b235e9711036fbb66f9ac0ed8a99e75
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="makeunsigned-class"></a>make_unsigned (Clase)
Hace que el tipo o el tipo sin signo más pequeño sea igual o superior en tamaño al tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`T`|Tipo que se va a modificar.|  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del modificador de tipo contiene un tipo modificado que es `T` si `is_unsigned<T>` es true. En caso contrario, es el tipo con signo menor `ST` para el que `sizeof (T) <= sizeof (ST)`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




