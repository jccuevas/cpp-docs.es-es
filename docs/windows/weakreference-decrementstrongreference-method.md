---
title: 'WeakReference:: Decrementstrongreference (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d5605670e05f91f9f1293c8bff0f4d74e458d25
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890341"
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