---
title: "WeakReference:: Decrementstrongreference (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bda6de03ce17db7ebac751865686c3e74a26d0d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>Comentarios  
 Disminuye el seguro recuento de referencias del objeto WeakReference actual.  
  
 Cuando el recuento de referencia segura se convierte en cero, la referencia segura se establece en `nullptr`.  
  
## <a name="return-value"></a>Valor devuelto  
 El recuento de referencia segura disminuye.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
[WeakReference (clase)](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)