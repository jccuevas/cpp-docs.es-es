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
ms.openlocfilehash: 7bc3d789d6c0d304aa170d59dff23a97a67061d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214291"
---
# <a name="activatableclass-macros"></a>ActivatableClass (Macros)

Rellena una memoria caché interna que contiene un generador que puede crear una instancia de la clase especificada.

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
Nombre de la clase que se va a crear.

*Factory*<br/>
Generador que creará una instancia de la clase especificada.

*serverName*<br/>
Nombre que especifica un subconjunto de generadores del módulo.

## <a name="remarks"></a>Observaciones

No use estas macros con COM clásico a menos que utilice la Directiva `#undef` para asegurarse de que se quita la definición de macro `__WRL_WINRT_STRICT__`.

## <a name="requirements"></a>Requisitos

**Encabezado:** Module. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Module (clase)](module-class.md)
