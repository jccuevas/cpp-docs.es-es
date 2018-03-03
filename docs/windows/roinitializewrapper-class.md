---
title: RoInitializeWrapper (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f6330c78a6bbac5f14e94c253f05515e3d29575
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper (Clase)
Inicializa el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Comentarios  
 RoInitializeWrapper es la comodidad que inicializa el tiempo de ejecución de Windows y devuelve un HRESULT que indica si la operación se realizó correctamente.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper (constructor)](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializa una nueva instancia de la clase RoInitializeWrapper.|  
|[RoInitializeWrapper::~RoInitializeWrapper (destructor)](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Destruye la instancia actual de la clase RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() (operador)](../windows/roinitializewrapper-hresult-parens-operator.md)|Recupera el valor HRESULT producido por el constructor RoInitializeWrapper.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)