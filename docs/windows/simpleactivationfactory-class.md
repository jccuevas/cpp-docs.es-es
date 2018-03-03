---
title: SimpleActivationFactory (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 991d428e90654fd29cfbb9c5c7e110708a05de01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory (clase)
Proporciona un mecanismo fundamental para crear una clase base de Windows Runtime o COM clásico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename Base  
>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 Una clase base.  
  
## <a name="remarks"></a>Comentarios  
 La clase base debe proporcionar un constructor predeterminado.  
  
 En el ejemplo de código siguiente se muestra cómo utilizar SimpleActivationFactory con el [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) macro.  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance (método)](../windows/simpleactivationfactory-activateinstance-method.md)|Crea una instancia de la interfaz especificada.|  
|[SimpleActivationFactory::GetRuntimeClassName (método)](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Obtiene el nombre de clase en tiempo de ejecución de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.|  
|[SimpleActivationFactory::GetTrustLevel (método)](../windows/simpleactivationfactory-gettrustlevel-method.md)|Obtiene el nivel de confianza de una instancia de la clase especificada por el `Base` parámetro de plantilla de clase.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ActivationFactory`  
  
 `SimpleActivationFactory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)