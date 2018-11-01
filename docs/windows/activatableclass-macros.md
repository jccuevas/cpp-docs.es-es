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
ms.openlocfilehash: 1b50d9ba59ef8aebe4eca388ee30449f4ddd53de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660673"
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

*nombre de clase*<br/>
Nombre de la clase para crear.

*Factory*<br/>
Generador que se va a crear una instancia de la clase especificada.

*Nombre de servidor*<br/>
Un nombre que especifica un subconjunto de fábricas del módulo.

## <a name="remarks"></a>Comentarios

No utilice estas macros con COM clásico a menos que use el `#undef` directiva para asegurarse de que el `__WRL_WINRT_STRICT__` se quita la definición de macro.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](../windows/module-class.md)