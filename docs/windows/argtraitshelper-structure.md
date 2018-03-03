---
title: ArgTraitsHelper (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31d9072ebf8c36453a74c75ff4a8997805d0973f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename TDelegateInterface  
>  
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
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)