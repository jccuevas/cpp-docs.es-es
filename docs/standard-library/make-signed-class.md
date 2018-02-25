---
title: Clase make_signed | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::make_signed
dev_langs:
- C++
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34ed7804d00e6c36d3f71f6b1699e7f9f7654bb3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="makesigned-class"></a>make_signed (Clase)
Hace que el tipo o el tipo con signo más pequeño sea igual o superior en tamaño al tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del modificador de tipo contiene un tipo modificado que es `T` si `is_signed<T>` es true. En caso contrario, es el tipo sin signo menor `UT` para el que `sizeof (T) <= sizeof (UT)`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



