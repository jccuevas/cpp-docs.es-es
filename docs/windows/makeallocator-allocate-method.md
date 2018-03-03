---
title: "Makeallocator:: Allocate (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e93cd6b5b8b3489fc18e8b083c0fc59589ebd1d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__forceinline void* Allocate();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un puntero a la memoria asignada; en caso contrario, `nullptr`.  
  
## <a name="remarks"></a>Comentarios  
 Asigna memoria y lo asocia con el objeto de MakeAllocator actual.  
  
 El tamaño de la memoria asignada es el tamaño del tipo especificado por el parámetro de plantilla MakeAllocator actual.  
  
 Un desarrollador debe reemplazar solamente el método Allocate() para implementar un modelo de asignación de memoria diferente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [MakeAllocator (clase)](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)