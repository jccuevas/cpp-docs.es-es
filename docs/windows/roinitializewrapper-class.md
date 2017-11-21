---
title: RoInitializeWrapper (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs: C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b94db5e54089fa91c3b79c185df8b366de07c38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper (constructor)](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializa una nueva instancia de la clase RoInitializeWrapper.|  
|[RoInitializeWrapper::~RoInitializeWrapper (destructor)](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Destruye la instancia actual de la clase RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() (operador)](../windows/roinitializewrapper-hresult-parens-operator.md)|Recupera el valor HRESULT producido por el constructor RoInitializeWrapper.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)