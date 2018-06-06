---
title: RoInitializeWrapper (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cac71857e6b472f11d1c9eaba48d181ea78fb456
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705597"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper (Clase)
Inicializa el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Comentarios  
 RoInitializeWrapper es la comodidad que inicializa el tiempo de ejecución de Windows y devuelve un HRESULT que indica si la operación se realizó correctamente. Dado que llama al destructor de clase `::Windows::Foundation::Uninitialize`, instancias de `RoInitializeWrapper` debe declararse en el ámbito global o de nivel superior.  
  
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