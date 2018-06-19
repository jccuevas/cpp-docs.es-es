---
title: Constructor Eventtargetarray | Documentos de Microsoft
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
ms.openlocfilehash: fbfd12ea513044f1062e60f5c73f5089683f043d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872720"
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