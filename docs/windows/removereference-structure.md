---
title: RemoveReference (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
dev_langs:
- C++
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 126394e3a63016eccf1f5451d032753bb8f81da8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="removereference-structure"></a>RemoveReference (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class T>  
struct RemoveReference;  
template<class T>  
struct RemoveReference<T&>;  
template<class T>  
struct RemoveReference<T&&>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase.  
  
## <a name="remarks"></a>Comentarios  
 Elimina el rasgo de referencia o referencia rvalue del parámetro de plantilla de clase especificada.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Type`|Sinónimo para el parámetro de plantilla de clase.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `RemoveReference`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)