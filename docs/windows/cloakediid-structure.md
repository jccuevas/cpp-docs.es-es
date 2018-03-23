---
title: CloakedIid (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
dev_langs:
- C++
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 075694e83f4c0e2004ccc9a86b03a0f7b7ea7f78
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="cloakediid-structure"></a>CloakedIid (estructura)
Indica a las plantillas RuntimeClass, Implements y ChainInterfaces que la interfaz especificada no es accesible en la lista IID.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
struct CloakedIid : T;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La interfaz que está oculto (escondida).  
  
## <a name="remarks"></a>Comentarios  
 El siguiente es un ejemplo de cómo se usa CloakedIid: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `T`  
  
 `CloakedIid`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)