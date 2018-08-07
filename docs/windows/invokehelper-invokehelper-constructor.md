---
title: Constructor Invokehelper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6618d5fc219e5f4e6533eb4d31cf7cd14fc4b1d5
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602554"
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper (Constructor)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
explicit InvokeHelper(  
   TCallback callback  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *devolución de llamada*  
 Un controlador de eventos.  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la **InvokeHelper** clase.  
  
 El `TCallback` parámetro de plantilla especifica el tipo del controlador de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [InvokeHelper (estructura)](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)