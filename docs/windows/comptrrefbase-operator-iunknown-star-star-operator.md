---
title: 'Comptrrefbase:: operator IUnknown ** (operador) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
dev_langs:
- C++
helpviewer_keywords:
- operator IUnknown** operator
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 816c71d2c14b373e63de2b2c8725eb87b40d91e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870320"
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown** (Operador)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
operator IUnknown**() const;  
```  
  
## <a name="remarks"></a>Comentarios  
 Convierte la actual [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos a un puntero a-a-puntero-a la interfaz IUnknown.  
  
 Se genera un error si el ComPtrRefBase actual no se deriva de IUnknown.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [ComPtrRefBase (clase)](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)