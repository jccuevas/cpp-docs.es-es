---
title: Clase is_error_code_enum | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::is_error_code_enum
- std.is_error_code_enum
- is_error_code_enum
- std::is_error_code_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 65c818260a4da28c3134e7fb9e124993b0200b74
ms.lasthandoff: 02/24/2017

---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum (Clase)
Representa un predicado de tipo que comprueba la enumeración [error_code](../standard-library/error-code-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <_Enum>
class is_error_code_enum;
```  
  
## <a name="remarks"></a>Comentarios  
 Una instancia de este [predicado de tipo](../standard-library/type-traits.md) es true si el tipo `_Enum` es un valor de enumeración adecuado para el almacenamiento en un objeto de tipo `error_code`.  
  
 Está permitido agregar especializaciones a este tipo para tipos definidos por el usuario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<system_error>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [<system_error>](../standard-library/system-error.md)




