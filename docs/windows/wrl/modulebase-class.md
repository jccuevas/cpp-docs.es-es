---
title: ModuleBase (Clase)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 254796c03d25a77da22c48881c086a41ffbfeb82
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337495"
---
# <a name="modulebase-class"></a>ModuleBase (Clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Comentarios

Representa la clase base de la [módulo](module-class.md) clases.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                         | Descripción
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase::ModuleBase](#modulebase)        | Inicializa una instancia de la clase `Module`.
[ModuleBase::~ModuleBase](#tilde-modulebase) | Desinicializa la instancia actual de la `Module` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                      | Descripción
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase::DecrementObjectCount](#decrementobjectcount) | Cuando se implementa, disminuye el número de objetos que sigue el módulo.
[ModuleBase::IncrementObjectCount](#incrementobjectcount) | Cuando se implementa, incrementa el número de objetos que se hace un seguimiento mediante el módulo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ModuleBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="tilde-modulebase"></a>ModuleBase::~ModuleBase

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Comentarios

Desinicializa la instancia actual de la `ModuleBase` clase.

## <a name="decrementobjectcount"></a>ModuleBase::DecrementObjectCount

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de decremento.

### <a name="remarks"></a>Comentarios

Cuando se implementa, disminuye el número de objetos que sigue el módulo.

## <a name="incrementobjectcount"></a>ModuleBase::IncrementObjectCount

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de incremento.

### <a name="remarks"></a>Comentarios

Cuando se implementa, incrementa el número de objetos que se hace un seguimiento mediante el módulo.

## <a name="modulebase"></a>ModuleBase::ModuleBase

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Comentarios

Inicializa una instancia de la clase `Module`.
