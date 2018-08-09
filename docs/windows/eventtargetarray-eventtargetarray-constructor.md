---
title: Constructor Eventtargetarray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59753f592f099f80396f408fa531756ba91b308e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652544"
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray (Constructor)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *recursos humanos*  
 Después de las operaciones de este constructor, parámetro *hr* indica si la asignación de la matriz se realizó correctamente o no. La tabla siguiente enumeran los valores posibles para *hr*.  
  
 S_OK  
 La operación se realizó correctamente.  
  
 E_OUTOFMEMORY  
 No se pudo asignar memoria para la matriz.  
  
 S_FALSE  
 Parámetro *elementos* es menor o igual que cero.  
  
 *elementos*  
 El número de elementos de matriz que se va a asignar.  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la **EventTargetArray** clase.  
  
 **EventTargetArray** se usa para mantener una matriz de controladores de eventos en un `EventSource` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [EventTargetArray (clase)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)