---
title: Estructura identity | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: dd840dba1de5e389e2fa1d8585d677d3be255f8e
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="identity-structure"></a>identity (Estructura)
Estructura que proporciona una definición de tipo como parámetro de plantilla.  
  
## <a name="syntax"></a>Sintaxis  
```  
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };  
```  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Valor que se va a identificar.|  
  
## <a name="remarks"></a>Comentarios  
 La clase contiene la definición de tipo público `type`, que es igual que el tipo de parámetro de plantilla. Se usa junto con la función de plantilla [forward](../standard-library/utility-functions.md#forward) para asegurarse de que un parámetro de función tiene el tipo deseado.  
  
 Para garantizar la compatibilidad con código antiguo, la clase también define la función identity `operator()` que devuelve su argumento `left`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<utility>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<utility>](../standard-library/utility.md)




