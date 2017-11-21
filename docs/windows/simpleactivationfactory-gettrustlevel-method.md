---
title: "Simpleactivationfactory:: Gettrustlevel (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs: C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb709d0f79a1fd57dfe84567b0bc7f8d1d15c3d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel (Método)
Obtiene el nivel de confianza de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `trustLvl`  
 Cuando se completa esta operación, el nivel de confianza del objeto de clase actual.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre S_OK.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)