---
title: SimpleClassFactory (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleClassFactory class
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: debb78ba4be2731b8cffce1133518b0b4a04f63d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892766"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory (clase)
Proporciona un mecanismo fundamental para crear una clase base.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Base>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 Una clase base.  
  
## <a name="remarks"></a>Comentarios  
 La clase base debe proporcionar un constructor predeterminado.  
  
 En el ejemplo de código siguiente se muestra cómo utilizar SimpleClassFactory con el [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) macro.  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SimpleClassFactory::CreateInstance (método)](../windows/simpleclassfactory-createinstance-method.md)|Crea una instancia de la interfaz especificada.|  
  
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
  
 `ClassFactory`  
  
 `SimpleClassFactory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)