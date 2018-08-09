---
title: EnableIf (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
dev_langs:
- C++
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 014099ce3e9152d2402263baaa6d6b30607756ed
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644978"
---
# <a name="enableif-structure"></a>EnableIf (estructura)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   bool b,  
   typename T = void  
>  
  
struct EnableIf;  
template <  
   typename T  
>  
struct EnableIf<true, T>;  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Un tipo.  
  
 *b*  
 Expresión booleana.  
  
## <a name="remarks"></a>Comentarios  
 Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si se evalúa como el primer parámetro de plantilla **true**.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Si el parámetro de plantilla *b* se evalúa como **true**, la especialización parcial define el miembro de datos `type` a ser de tipo `T`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `EnableIf`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)