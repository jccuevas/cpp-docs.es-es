---
title: ArgTraitsHelper (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4df7e9fe3823e3dbb84b09863e6de5178ab44d18
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename TDelegateInterface>  
struct ArgTraitsHelper;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TDelegateInterface`  
 Una interfaz de delegado.  
  
## <a name="remarks"></a>Comentarios  
 Ayuda a define las características comunes de los argumentos de delegado.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`methodType`|Sinónimo de `decltype(&TDelegateInterface::Invoke)`.|  
|`Traits`|Sinónimo de `ArgTraits<methodType>`.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[ArgTraitsHelper::args (constante)](../windows/argtraitshelper-args-constant.md)|Ayuda a [Argtraits](../windows/argtraits-args-constant.md) mantener recuento del número de parámetros en el método de invocación de una interfaz de delegado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)