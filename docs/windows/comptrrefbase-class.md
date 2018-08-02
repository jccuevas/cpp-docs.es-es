---
title: ComPtrRefBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0342500fc41c650967e17919ebdc9605d4261cb5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464248"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase (clase)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 Un [ComPtr\<T >](../windows/comptr-class.md) tipo o un tipo derivado de éste, no simplemente la interfaz representada por el **ComPtr**.  
  
## <a name="remarks"></a>Comentarios  
 Representa la clase base para el [ComPtrRef](../windows/comptrref-class.md) clase.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`InterfaceType`|Un sinónimo del tipo de parámetro de plantilla *T*.|  
  
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