---
title: 'Interfacetraits:: Casttounknown (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c02a79a5b4d8674317c97624bf77cce9b653808
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
static __forceinline IUnknown* CastToUnknown(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de parámetro `ptr`.  
  
 `ptr`  
 Puntero al tipo `T`.  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero a la interfaz IUnknown desde el que `Base` se deriva.  
  
## <a name="remarks"></a>Comentarios  
 Convierte el puntero especificado a un puntero a IUnknown.  
  
 Para obtener más información acerca de `Base`, vea la sección de definiciones de tipo público en [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Vea también  
 [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)