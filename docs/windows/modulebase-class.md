---
title: ModuleBase (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ModuleBase
dev_langs: C++
helpviewer_keywords: ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe24bd4995acb7a36f6aa50378a03b519c8d8e3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ModuleBase::ModuleBase (constructor)](../windows/modulebase-modulebase-constructor.md)|Inicializa una instancia de la clase de módulo.|  
|[ModuleBase::~ModuleBase (destructor)](../windows/modulebase-tilde-modulebase-destructor.md)|Desinicializa la instancia actual de la clase de módulo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
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