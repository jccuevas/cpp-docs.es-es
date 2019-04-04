---
title: ActivatableClass (Macros)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: eee8267e2e76eead267eb2486836dbcc38a90231
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785967"
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

*className*<br/>
Nombre de la clase para crear.

*factory*<br/>
Generador que se va a crear una instancia de la clase especificada.

*serverName*<br/>
Un nombre que especifica un subconjunto de fábricas del módulo.

## <a name="remarks"></a>Comentarios

No utilice estas macros con COM clásico a menos que use el `#undef` directiva para asegurarse de que el `__WRL_WINRT_STRICT__` se quita la definición de macro.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](module-class.md)