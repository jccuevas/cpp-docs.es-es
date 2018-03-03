---
title: ComPtrRefBase (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 071598c83086afe12e1d19ef541dbfb3d0dbc55a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase (clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md) tipo o un tipo derivado de él, no solo la interfaz representada por la clase ComPtr.  
  
## <a name="remarks"></a>Comentarios  
 Representa la clase base para la [ComPtrRef](../windows/comptrref-class.md) clase.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`InterfaceType`|Un sinónimo para el tipo de parámetro de plantilla `T`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable** (operador)](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Convierte la actual [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos a un puntero a-a-puntero-a la interfaz IInspectable.|  
|[ComPtrRefBase::operator IUnknown** (operador)](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Convierte la actual [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos a un puntero a-a-puntero-a la interfaz IUnknown.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_ (miembro de datos)](../windows/comptrrefbase-ptr-data-member.md)|Puntero al tipo especificado por el parámetro de plantilla actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)