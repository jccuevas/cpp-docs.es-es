---
title: Clase make_unsigned | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- make_unsigned
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
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 1bdebf2a3d3f03defa041d049ac98287df7aad6c
ms.lasthandoff: 02/24/2017

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




