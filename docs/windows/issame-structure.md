---
title: IsSame (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
dev_langs:
- C++
helpviewer_keywords:
- IsSame structure
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52dd1920ad32719e4fbff5a0138e737367d97ff4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877675"
---
# <a name="issame-structure"></a>IsSame (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename T1,  
   typename T2  
>  
struct IsSame;  
template <  
   typename T1  
>  
struct IsSame<T1, T1>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T1`  
 Un tipo.  
  
 `T2`  
 Otro tipo.  
  
## <a name="remarks"></a>Comentarios  
 Comprueba si un tipo especificado es igual que otro tipo especificado.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[IsSame::value (constante)](../windows/issame-value-constant.md)|Indica si un tipo es igual a otro.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IsSame`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)