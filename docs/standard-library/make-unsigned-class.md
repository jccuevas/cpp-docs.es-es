---
title: Clase make_unsigned | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3691e8840bf4d51f48359e7efbdd777bd18e01cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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



