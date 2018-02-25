---
title: Clase is_nothrow_copy_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37964edce6b8b6370302a29c76e80386e54ab5a4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="isnothrowcopyassignable-class"></a>Clase is_nothrow_copy_assignable
Comprueba si el tipo tiene un operador de asignación de copia que el compilador sabe que no se inicia.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct is_nothrow_copy_assignable;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true para un tipo de referencia `T` si `is_nothrow_assignable<T&, const T&>` es true; en caso contrario, es false.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [Clase is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)   





