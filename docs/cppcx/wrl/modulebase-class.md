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
ms.openlocfilehash: 13a8ceef3133e9946524e1fcd02e96535eccd7fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371269"
---
# <a name="modulebase-class"></a>ModuleBase (Clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Observaciones

Representa la clase base de las clases [Module.](module-class.md)

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                         | Descripción
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase::ModuleBase](#modulebase)        | Inicializa una instancia de la clase `Module`.
[ModuleBase::-ModuleBase](#tilde-modulebase) | Desinicializa la instancia `Module` actual de la clase.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                      | Descripción
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase::DecrementObjectCount](#decrementobjectcount) | Cuando se implementa, disminuye el número de objetos seguidos por el módulo.
[ModuleBase::IncrementObjectCount](#incrementobjectcount) | Cuando se implementa, incrementa el número de objetos a los que realiza el seguimiento el módulo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ModuleBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a>ModuleBase::-ModuleBase

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Observaciones

Desinicializa la instancia `ModuleBase` actual de la clase.

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a>ModuleBase::DecrementObjectCount

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Valor devuelto

El conteo antes de la operación de decremento.

### <a name="remarks"></a>Observaciones

Cuando se implementa, disminuye el número de objetos seguidos por el módulo.

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a>ModuleBase::IncrementObjectCount

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de incremento.

### <a name="remarks"></a>Observaciones

Cuando se implementa, incrementa el número de objetos a los que realiza el seguimiento el módulo.

## <a name="modulebasemodulebase"></a><a name="modulebase"></a>ModuleBase::ModuleBase

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Observaciones

Inicializa una instancia de la clase `Module`.
