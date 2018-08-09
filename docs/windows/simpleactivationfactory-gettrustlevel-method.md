---
title: Método Simpleactivationfactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1234c667426937f5d40937c5f2bcc72949e827ae
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012399"
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel (Método)
Obtiene el nivel de confianza de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
### <a name="parameters"></a>Parámetros  
 *trustLvl*  
 Cuando se completa esta operación, el nivel de confianza del objeto de clase actual.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre S_OK.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)