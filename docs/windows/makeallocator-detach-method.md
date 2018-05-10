---
title: 'Makeallocator:: Detach (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50afca04492c29aa526f7a004c6e0f725022e9ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__forceinline void Detach();  
```  
  
## <a name="remarks"></a>Comentarios  
 Desasocia la memoria asignada por el [Allocate](../windows/makeallocator-allocate-method.md) método MakeAllocator del objeto actual.  
  
 Si se llama a Detach(), es responsabilidad suya eliminar la memoria proporcionada por el método de asignación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [MakeAllocator (clase)](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)