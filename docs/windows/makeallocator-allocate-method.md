---
title: 'Makeallocator:: Allocate (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0e8d387dea7687ad61d85f975d58aa47489266d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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