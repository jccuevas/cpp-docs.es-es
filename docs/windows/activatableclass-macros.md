---
title: ActivatableClass (Macros) | Microsoft Docs
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
ms.openlocfilehash: aa178126b3a749e3af67b9dae3711c0a5cf9f408
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645791"
---
# <a name="activatableclass-macros"></a>ActivatableClass (Macros)

Rellena una memoria caché interna que contiene una fábrica que puede crear una instancia de la clase especificada.

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

*Factory*  
Generador que se va a crear una instancia de la clase especificada.

*Nombre de servidor*  
Un nombre que especifica un subconjunto de fábricas del módulo.

## <a name="remarks"></a>Comentarios

No utilice estas macros con COM clásico a menos que use el `#undef` directiva para asegurarse de que el `__WRL_WINRT_STRICT__` se quita la definición de macro.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
[Module (clase)](../windows/module-class.md)