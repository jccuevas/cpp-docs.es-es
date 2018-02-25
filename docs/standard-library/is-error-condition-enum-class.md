---
title: Clase is_error_condition_enum | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::is_error_condition_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4f92a07a904ae80fb56e2cf21114bb79506dfa11
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum (Clase)
Representa un predicado de tipo que comprueba la enumeración [error_condition](../standard-library/error-condition-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <_Enum>
class is_error_condition_enum;
```  
  
## <a name="remarks"></a>Comentarios  
 Una instancia de este [predicado de tipo](../standard-library/type-traits.md) es true si el tipo `_Enum` es un valor de enumeración adecuado para el almacenamiento en un objeto de tipo `error_condition`.  
  
 Está permitido agregar especializaciones a este tipo para tipos definidos por el usuario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<system_error>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [<system_error>](../standard-library/system-error.md)



