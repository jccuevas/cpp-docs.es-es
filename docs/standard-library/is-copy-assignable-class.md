---
title: Clase is_copy_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb6dfc91d47a0b6afb5f0918d036d1b07a5e693f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="iscopyassignable-class"></a>Clase is_copy_assignable
Comprueba si el tipo se puede copiar en la asignación.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_copy_assignable;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un operador de asignación de copia; en caso contrario, contiene false. Equivalente a is_assignable\<Ty&, const Ty&>.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



