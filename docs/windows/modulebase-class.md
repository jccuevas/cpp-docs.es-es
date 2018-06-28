---
title: ModuleBase (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bfee0c0cd7ff7bd7f4525a291184f08f1e2898e5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878741"
---
# <a name="modulebase-class"></a>ModuleBase (Clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>Comentarios  
 Representa la clase base de la [módulo](../windows/module-class.md) clases.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ModuleBase::ModuleBase (constructor)](../windows/modulebase-modulebase-constructor.md)|Inicializa una instancia de la clase de módulo.|  
|[ModuleBase::~ModuleBase (destructor)](../windows/modulebase-tilde-modulebase-destructor.md)|Desinicializa la instancia actual de la clase de módulo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount (método)](../windows/modulebase-decrementobjectcount-method.md)|Cuando se implementa, disminuye el número de objetos de seguimiento por el módulo.|  
|[ModuleBase::IncrementObjectCount (método)](../windows/modulebase-incrementobjectcount-method.md)|Cuando se implementa, incrementa el número de objetos que se hace un seguimiento mediante el módulo.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ModuleBase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)