---
title: Clase is_standard_layout | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_standard_layout
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 39b7198e020a2c520fb054687a7dadfdd8172826
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="isstandardlayout-class"></a>is_standard_layout (Clase)
Comprueba si el tipo es un diseño estándar.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_standard_layout;
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Ty`|El tipo que se va a consultar.|  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `Ty` es una clase que tiene un diseño estándar de objetos miembro en memoria; en caso contrario, es false.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




