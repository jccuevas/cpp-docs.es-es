---
title: Constructor Eventtargetarray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6dbe316310e04172c659460c08137edd2a401df6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray (Constructor)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hr`  
 Después de las operaciones de este constructor, parámetro `hr` indica si la asignación de la matriz se realizó correctamente o no. En la tabla siguiente se enumera los posibles valores para `hr`.  
  
 S_OK  
 La operación se realizó correctamente.  
  
 E_OUTOFMEMORY  
 No se pudo asignar memoria para la matriz.  
  
 S_FALSE  
 Parámetro `items` es menor o igual que cero.  
  
 `items`  
 El número de elementos de matriz que se va a asignar.  
  
## <a name="remarks"></a>Comentarios  
 Inicializa una nueva instancia de la clase EventTargetArray.  
  
 EventTargetArray se usa para mantener una matriz de controladores de eventos en un objeto de origen de eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [EventTargetArray (clase)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)