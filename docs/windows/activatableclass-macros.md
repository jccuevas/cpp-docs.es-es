---
title: ActivatableClass (Macros) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs:
- C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aeb68deddd1cdfa9e1e869a08bfb0a1f3bb8d6ca
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857469"
---
# <a name="activatableclass-macros"></a>ActivatableClass (Macros)

Rellena una caché interna que contiene una fábrica que puede crear una instancia de la clase especificada.

## <a name="syntax"></a>Sintaxis

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>Parámetros

*nombre de clase*  
Nombre de la clase para crear.  

*Generador*  
Generador que va a crear una instancia de la clase especificada.

*ServerName*  
Nombre que especifica un subconjunto de los generadores de en el módulo.

## <a name="remarks"></a>Comentarios

No utilice estas macros con COM clásico a menos que utilice el `#undef` directiva para asegurarse de que el **&#95; &#95;WRL_WINRT_STRICT&#95; &#95;** se quita la definición de macro.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](../windows/module-class.md)