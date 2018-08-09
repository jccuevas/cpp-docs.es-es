---
title: Miembro de datos Targets_ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targets_
dev_langs:
- C++
helpviewer_keywords:
- targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea08cdc8657100e1c1e0157a8a542a44ea34cd4d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642378"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ (Miembro de datos)
Una matriz de uno o varios controladores de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando el evento representado por el actual **EventSource** se produce el objeto, se llama a los controladores de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)