---
title: 'Eventtargetarray:: end (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::End
dev_langs:
- C++
helpviewer_keywords:
- End method
ms.assetid: 20c491b8-f355-4d8f-ad14-8f46121d9af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00827d42bb01263d6b4fd9b5aea3b0fc7f7c76e1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874270"
---
# <a name="eventtargetarrayend-method"></a>EventTargetArray::End (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ComPtr<IUnknown>* End();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 La dirección del último elemento de la matriz interna de controladores de eventos.  
  
## <a name="remarks"></a>Comentarios  
 Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [EventTargetArray (clase)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)