---
title: InterfaceList (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52acf2f0b9936903b4359e21e23ae50c95d2f31a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="interfacelist-structure"></a>InterfaceList (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename T,  
   typename U  
>  
struct InterfaceList;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un nombre de la interfaz; la primera interfaz en la lista recursiva.  
  
 `U`  
 Un nombre de la interfaz; las interfaces restantes en la lista recursiva.  
  
## <a name="remarks"></a>Comentarios  
 Se utiliza para crear una lista recursiva de interfaces.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`FirstT`|Sinónimo de parámetro de plantilla `T`.|  
|`RestT`|Sinónimo de parámetro de plantilla `U`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `InterfaceList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)