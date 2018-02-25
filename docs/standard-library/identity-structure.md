---
title: Estructura identity | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2411601a0294b5244049d2ead1b67c500908a33
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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



