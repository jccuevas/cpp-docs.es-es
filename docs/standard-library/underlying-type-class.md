---
title: underlying_type (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- underlying_type
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: 13
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 95012fdeb3ac78d5e1cc76e03ed851a0b9701f5e
ms.lasthandoff: 02/24/2017

---
# <a name="underlyingtype-class"></a>underlying_type (Clase)
Genera el tipo entero subyacente para un tipo de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
struct underlying_type;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## <a name="remarks"></a>Comentarios  
 La definición de tipo miembro `type` de la clase de plantilla nombra el tipo entero subyacente de `T`, cuando `T` es un tipo de enumeración, de lo contrario, no hay ninguna definición de tipo miembro `type`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




